## Docker commands 

```
docker --version                  ## docker version 
docker pull <image>
docker run <image_ID>             ## run intractivly
docker run -d <image_ID>          ## run detached
docker run -d -P <image_ID>       ## give random port
docker run -d -p 80:80 <image_ID> ## on assing port container run 
docker ps                         ## list all runnning conatainer 
docker ps -a                      ## list all state container
docker ps -aq                     ## list all container only container ID 
docker stop <cont_ID>             ## stop container
docker stop $(docker ps)
docker start $(docker ps -aq
docker rm <cont_ID>               ## remove container 
docker rmi <Image_ID>             ## to remove image
docker exec -it <cont_ID> bash    ## to enter into docker container
docker log 
```
--- 
# Day 2 – Docker Container Commands & Lifecycle

## Essential Concepts

- **Image**: blueprint/template.
- **Container**: running (or stopped) instance of an image.
- Lifecycle operations: create, start, stop, restart, remove.

---

## Core Container Lifecycle Commands

### Create a Container (but do not start)

```bash
docker create --name mycontainer ubuntu:latest
```

- Creates container metadata from the image.
- Container appears in `docker ps -a`, but is in **created** state.

### Run (Create + Start) a Container

```bash
docker run ubuntu:latest
```

- Equivalent to `docker create` + `docker start`.
- If no command is specified, Docker uses the image’s default command (`CMD` / `ENTRYPOINT`).

With a name:

```bash
docker run --name myubuntu ubuntu:latest
```

---

## Starting, Stopping, and Removing Containers

### Start a Stopped Container

```bash
docker start mycontainer
```

### Stop a Running Container

```bash
docker stop mycontainer
```

- Sends a graceful `SIGTERM`, then `SIGKILL` if it doesn’t exit in time.

### Remove a Container

```bash
docker rm mycontainer
```

- Container must be stopped before removal (or use `-f` to force).

Remove multiple containers at once:

```bash
docker rm $(docker ps -aq)
```

> `docker ps -aq` returns all container IDs (quiet mode), which are then passed to `docker rm`.

---

## Listing and Inspecting Containers

### List Running Containers

```bash
docker ps
```

### List All Containers (including stopped)

```bash
docker ps -a
```

### List Only Container IDs

```bash
docker ps -aq
```

### Inspect a Container

```bash
docker inspect mycontainer
```

- Shows detailed JSON: configuration, networking, mounts, environment, etc.
- Very useful for troubleshooting.

---

## `docker run` – Important Options

### Detached Mode (`-d`)

```bash
docker run -d --name web nginx
```

- Runs container in the background.
- You get the container ID back, and the container continues running.

### Port Mapping (`-p` and `-P`)

- `-p hostPort:containerPort` – map a host port to container port.

```bash
docker run -d --name web -p 8080:80 nginx
```

- Access using `http://localhost:8080`.

- `-P` – publish all **EXPOSE**d ports to random host ports.

```bash
docker run -d -P nginx
```

### Environment Variables (`-e`)

```bash
docker run -d -e APP_ENV=prod -e DEBUG=false myimage
```

- Passes `APP_ENV` and `DEBUG` as environment variables into the container.

### Naming a Container (`--name`)

```bash
docker run -d --name mynginx -p 8080:80 nginx
```

- Custom name makes it easier to reference the container instead of using IDs.

---

## Exposing Applications to the World

To make a containerized app accessible from the host or outside:

1. The app listens on a specific port inside the container (e.g., `80`).
2. You publish that port using `-p`.

Example:

```bash
docker run -d --name myweb -p 8080:80 nginx
```

- Container’s port `80` → host’s port `8080`.
- Access from host: `http://localhost:8080`.

---

## Interacting with Containers Using `exec`

`docker exec` runs commands **inside a running container**.

### Start a Shell Inside a Running Container

```bash
docker exec -it myweb bash
```

- `-i`: interactive.
- `-t`: allocate a pseudo-TTY.
- You are now inside the container’s filesystem and process namespace.

If image doesn’t have `bash`, use `sh`:

```bash
docker exec -it myweb sh
```

### Run a One-Time Command

```bash
docker exec myweb ls /usr/share/nginx/html
```

- Executes `ls` inside the container, prints result to host terminal.

---

## Logs and Troubleshooting

### View Container Logs

```bash
docker logs myweb
```

- Shows STDOUT/STDERR of the container’s main process.

Follow logs in real-time:

```bash
docker logs -f myweb
```

### Inspect Container Details

```bash
docker inspect myweb
```

- Look for:
  - `Config.Cmd`, `Config.Env`.
  - `NetworkSettings.Ports`.
  - `Mounts` for volumes.

### Copy Files To/From Containers (`docker cp`)

```bash
# From container to host
docker cp myweb:/usr/share/nginx/html/index.html ./index.html

# From host to container
docker cp ./new-index.html myweb:/usr/share/nginx/html/index.html
```

---

## Monitoring Containers – `docker stats`

```bash
docker stats
```

- Real-time view of:
  - CPU usage
  - Memory usage
  - Network I/O
  - Block I/O

Useful to identify containers using too many resources.

---

## Summary of Key Commands (Day 2)

- **Lifecycle**: `run`, `create`, `start`, `stop`, `rm`, `ps`, `ps -aq`.
- **Interaction**: `exec -it`, `logs`, `cp`, `inspect`, `stats`.
- **Networking basics** via `docker run`: `-d`, `-p`, `-P`, `-e`, `--name`.

Practice:
- Run Nginx on port 8080.
- Enter container, list web root files.
- Check logs and stats.
- Stop and remove containers with `docker ps -aq` and `docker rm`.
