# Day 5 – Docker Volumes & Persistent Storage

## Why We Need Volumes

- Containers are **ephemeral**:
  - If you delete a container, its internal filesystem changes are lost.
  - Updating images or redeploying may recreate containers from scratch.
- Many applications (databases, stateful services) need **persistent data** that survives container deletion.

**Solution**: Docker **volumes** and **bind mounts** provide persistent storage outside the container’s writable layer.

---

## Types of Storage in Docker

1. **Container’s writable layer**
   - Temporary; deleted with the container.

2. **Volumes (named volumes)**
   - Managed by Docker (`docker volume` commands).
   - Stored in Docker’s storage area.
   - Best for production use.

3. **Bind mounts**
   - Host directory or file mounted into container.
   - Path comes from host filesystem (e.g., `/data/app` or `$(pwd)/data`).
   - Useful for development, sharing source code, or mounting config files.

This day focuses on Docker **volumes** and using `-v` with `docker run`.

---

## Docker Volume Commands

### List Volumes

```bash
docker volume ls
```

- Shows all volumes managed by Docker.

### Create a Volume

```bash
docker volume create mydata
```

- Creates a named volume `mydata`.

### Inspect a Volume

```bash
docker volume inspect mydata
```

- Shows mountpoint on host and containers using it.

### Remove a Volume

```bash
docker volume rm mydata
```

- Volume must not be in use by any container.

### Remove Unused Volumes

```bash
docker volume prune
```

- Deletes all volumes not used by at least one container.
- Use carefully; confirm the prompt.

---

## Using Volumes with `docker run -v`

### Named Volumes

Syntax: `-v volume_name:container_path`

Example – MySQL with named volume:

```bash
docker volume create mysqldata

docker run -d --name db \
  -e MYSQL_ROOT_PASSWORD=root \
  -v mysqldata:/var/lib/mysql \
  mysql:8
```

- MySQL data is stored in volume `mysqldata`.
- You can remove/recreate the `db` container without losing database data.

### Bind Mounts

Syntax: `-v host_path:container_path`

Example – mount current directory into Nginx web root:

```bash
docker run -d --name web \
  -p 8080:80 \
  -v $(pwd)/html:/usr/share/nginx/html \
  nginx
```

- Files in `./html` on the host are served by Nginx.
- Changing files on host updates content in the container immediately.

> Use absolute paths or `$(pwd)` (Linux/macOS) for predictable behavior.

---

## Best Practices

- Use **named volumes** for application data that must persist across container recreations.
- Use **bind mounts** for:
  - Local development (mounting source code).
  - Sharing configuration and log directories.

Examples:

- App logs:

```bash
docker run -d --name app \
  -v app-logs:/var/log/myapp \
  myusername/myapp:1.0
```

- Developer source code mount:

```bash
docker run -it --name app-dev \
  -p 3000:3000 \
  -v $(pwd):/app \
  -w /app \
  node:18-alpine \
  npm start
```

---

## Summary of Key Commands (Day 5)

- Volume management:
  - `docker volume ls`
  - `docker volume create <name>`
  - `docker volume inspect <name>`
  - `docker volume rm <name>`
  - `docker volume prune`

- Use with containers:
  - Named volume: `docker run -v mydata:/container/path ...`
  - Bind mount: `docker run -v /host/path:/container/path ...`

Practice:
- Create a named volume.
- Run a database container using that volume.
- Stop/remove the container and verify data persists.
- Try a bind mount to serve static HTML content via Nginx.






```
1  docker create volume my-vol
    2  docker --help \
    3  docker --help
    4  docker create volume my-vol
    5  docker volume create my-vol 
    6  docker volume ls 
    7  docker inspect volume 
    8  docker inspect volume my-vol
    9  docker pull nginx 
   10  vim index.html 
   11  docker run -d -P --name cont1 -v my-vol c881927
   12  docker ps 
   13  docker inspect df3b6677ffea 
   14  ls
   15  df -h
   16  docker ps 
   17  docker run -d -P -v my-vol:/usr/share/nginx/html nginx
   18  docker ps 
   19  ls
   20  docker cp index.html c963681dfc7c:/usr/share/nginx/html
   21  docker ps 
   22  curl ifconfig.me
   23  docker run -d -P --name test -v my-vol:/usr/share/nginx/html nginx 
   24  docker ps
   25  curl ifconfig.me
   26  docker inspect volume my-vol
   27  cd /var/lib/docker/volumes/my-vol/_data
   28  ls
   29  cd
   30  ls
   31  mkdir -p /mnt/test
   32  ls /mnt/test/
   33  docker run -d -P --name voltest -v /mnt/test:/usr/share/nginx/html nginx 
   34  docker ps 
   35  curl ifconfig.me
   36  cd /mnt/test/
   37  ls
   38  cat > index.html 
   39  ls
   40  cd
   41  docker volume create my-test
   42  docker volume list 
   43  df -h 
   44  docker volume ls
   45  docker volume inspect my-vol
   46  docker volume rm my-vol
   47  docker volume rm my-test
   48  docker volume prune
   49  df -h 
   50  docker network create --driver bridge --subnet 172.168.0.0/16 custom-network 
   51  docker network ls 
   52  docker image ls
   53  docker volume ls 
   54  docker ps 
   55  docker network ls 
   56  docker run -d -P --network custom-network -v my-vol:/usr/share/nginx/html nginx:latest
   57  docker ps 
   58  docker inspect e5880575d411
   59  docker ps 
   60  docker network create --driver bridge --subnet 192.16.0.0/16 test-network 
   61  docker run -d -P --network test-network -v my-vol:/usr/share/nginx/html nginx:latest
   62  docker ps 
   63  docker inspect ed883e12e7ef
   64  docker network create --driver bridge --subnet 192.16.0.0/24 test1-network 
   65  docker network create --driver bridge --subnet 10.0.0.0/24 test1-network 
   66  docker run -d -P --network test1-network -v my-vol:/usr/share/nginx/html nginx:latest
   67  docker ps 
   68  docker inspect 38e7496efcb7
   69  ls
   70  history 
   ```
