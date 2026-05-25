# Jenkins Essentials 🚀

## 🌟 Introduction to CI Process

### What is Continuous Integration (CI)?
Continuous Integration is a software development practice where developers frequently integrate their code into a shared repository. Each integration is automatically verified by:

- **Automated Build Processes** 📦
- **Automated Testing** ✅

This ensures the early detection of integration issues and maintains a high-quality codebase.

### Benefits of CI
- 🕒 **Faster Feedback Loop**: Detect issues early.
- 🔒 **Improved Code Quality**: Continuous testing and validation.
- 🤝 **Collaboration**: Teams work cohesively.
- 📈 **Efficiency**: Streamlined development workflow.

---

## 🌐 Difference Between Continuous Delivery and Continuous Deployment

| Aspect                        | Continuous Delivery 🚚                             | Continuous Deployment 🚀                              |
|-------------------------------|--------------------------------------------------|--------------------------------------------------|
| **Definition**                | Ensures code is always in a deployable state.    | Automatically deploys every change to production.|
| **Deployment Trigger**        | Manual approval for production release.          | Fully automated without manual intervention.     |
| **Use Case**                  | Suitable for environments requiring compliance.  | Ideal for rapid release environments.            |
| **Automation Level**          | High, except production deployment.              | Fully automated, end-to-end.                     |

---

## 🧰 Introduction to Jenkins

### What is Jenkins?
Jenkins is an open-source automation server widely used for:
- **Building** 🛠️
- **Testing** 🧪
- **Deploying** 🚀 applications in a CI/CD pipeline.

### Why Jenkins?
- 🌍 **Extensive Community Support**: A vast plugin ecosystem.
- 🖥️ **Cross-Platform**: Runs on various OS (Windows, Linux, macOS).
- 📈 **Scalable**: From small teams to large enterprises.
- 🔌 **Integration**: Easily integrates with version control systems and build tools.

### Core Features
- 🎛️ **Pipeline as Code**: Automate your workflows using Jenkinsfile.
- ⚙️ **Plugins**: Extend functionality with 1,500+ plugins.
- 📊 **Monitoring**: Track builds and test results in real-time.
- 🛡️ **Security**: Role-based access control and integration with SSO.

---

# Jenkins Essentials: Freestyle Job and Git Plugin

### 🚀 **Create Your First Freestyle Job**
A **Freestyle Job** in Jenkins is a basic project that allows you to configure and automate simple tasks, such as building code or running scripts. Here's how to create your first freestyle job:

1. **Log in to Jenkins**
   - Open your Jenkins dashboard in your browser.
   - Use your admin credentials to log in.

2. **Create a New Job**
   - Click on `New Item` from the Jenkins dashboard.
   - Enter the **name** for your job (e.g., `MyFirstFreestyleJob`).
   - Select `Freestyle project` and click `OK`.

3. **Configure the Job**
   - **Description**: Add a meaningful description for your job.
   - **Source Code Management**: Select `None` for now.
   - **Build Triggers**: Choose the appropriate trigger, such as "Build periodically" or "Poll SCM" if applicable.
   - **Build Steps**: Add a build step like `Execute shell` and provide the command to execute.

4. **Save and Build**
   - Click `Save` to save the configuration.
   - Click `Build Now` to execute the job.

5. **View Build Results**
   - Check the console output by clicking on the build number in the Build History section.

---

### 🔧 **Install Git Plugin**
To pull source code from a Git repository, you need to install the Git plugin.

1. **Navigate to Plugin Manager**
   - Go to `Manage Jenkins` > `Manage Plugins`.

2. **Search for Git Plugin**
   - Under the `Available` tab, search for `Git Plugin`.
   - Select the plugin and click `Install without restart`.

3. **Verify Installation**
   - After installation, go to `Manage Jenkins` > `Installed Plugins` and ensure the `Git Plugin` is listed.

4. **Set Up Global Git Configuration** *(Optional)*
   - Go to `Manage Jenkins` > `Configure System`.
   - Under `Git`, add global configurations like `Name` and `Email` for Git commits.

---

### 🌟 **Create Freestyle Job to Pull Source Code**
Here are the steps to create a freestyle job that pulls source code from a Git repository:

1. **Create a New Freestyle Job**
   - From the Jenkins dashboard, click `New Item`.
   - Enter the job name (e.g., `PullSourceCodeJob`) and select `Freestyle project`. Click `OK`.

2. **Configure Source Code Management**
   - In the job configuration page, go to `Source Code Management`.
   - Select `Git`.
   - Enter the Git repository URL (e.g., `https://github.com/user/repo.git`).
   - Provide credentials if the repository is private.

3. **Build Steps**
   - Add a build step to verify the code, such as `Execute shell` with a command like:
     ```bash
     ls -l
     ```

4. **Save and Build**
   - Click `Save` to save the job configuration.
   - Trigger a build by clicking `Build Now`.

5. **Verify Build**
   - Check the console output to ensure the code is pulled successfully.

---

### 🤔 **Tips and Suggestions**
- Use the **Build Triggers** to automate jobs (e.g., poll the repository for changes).
- Test the repository URL in a local terminal before adding it to Jenkins.
- Use the Git plugin's advanced options to handle branches, tags, and shallow clones.

---
## 1. Install SSH Build Agent Plugin 🔌

The SSH Build Agent Plugin allows Jenkins to manage and connect with build agents using SSH.

### Steps to Install:
1. Navigate to **Manage Jenkins** > **Manage Plugins**.
2. Go to the **Available** tab.
3. Search for `SSH Build Agents`.
4. Select the plugin and click **Install without restart**.

---

## 2. Create and Attach SSH Agents to Master Jenkins 🤖

Build agents help distribute build loads across multiple machines.

### Steps to Configure SSH Build Agent:
1. **Add Node (Build Agent)**:
   - Go to **Manage Jenkins** > **Manage Nodes and Clouds**.
   - Click on **New Node**.
   - Provide a name for the node (e.g., `Build-Agent-1`) and select **Permanent Agent**.
   - Click **OK**.

2. **Configure Node**:
   - Enter the following details:
     - **Remote root directory**: `/home/jenkins` (or any desired directory).
     - **Labels**: Add labels to identify the node (e.g., `linux`, `build-agent`).
   - Under **Launch Method**, select **Launch agent via SSH**.
     - Enter the **host address**, **credentials**, and the **port** (default: 22).
     - Test the connection to ensure proper configuration.
   - Save the configuration.

3. **Verify Agent**:
   - Once the node is added, it will appear on the **Manage Nodes** page.
   - Check the status; it should be **online**.

### Benefits of SSH Agents:
- Centralized job execution.
- Improved build performance with distributed workloads.
- Scalability for larger projects.

---

## 3. Job Configuration 🛠️

Job configuration defines how Jenkins executes a task.

### Key Configuration Options:
1. **General**:
   - Add a description of the job.
   - Restrict where this project can be run by specifying agent labels (e.g., `linux`, `windows`).

2. **Source Code Management (SCM)**:
   - Integrate with Git, Subversion, or other SCM tools.
   - Provide the repository URL and credentials.

3. **Build Triggers**:
   - Poll SCM: Trigger builds based on repository changes.
   - Build Periodically: Schedule builds at specific times.

4. **Build Environment**:
   - Add environment variables.
   - Delete workspace before the build starts.

5. **Build Steps**:
   - Execute shell scripts, batch commands, or invoke build tools.

6. **Post-Build Actions**:
   - Archive artifacts, publish test reports, or send notifications.

---
