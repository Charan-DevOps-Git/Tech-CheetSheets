## Basic Concepts

- **Job/Project**: A task or a unit of work in Jenkins, like building or testing software.
- **Build**: The process of executing a Jenkins job.
- **Pipeline**: A suite of plugins which supports implementing and integrating continuous delivery pipelines into Jenkins.
- **Node/Slave**: A machine that is part of the Jenkins environment and is capable of executing pipelines or jobs.
- **Master**: The main Jenkins server that orchestrates the job runs on the nodes.
- **Workspace**: The directory on a node where Jenkins runs a job.

## Common Commands

### Jenkins Installation

#### On Ubuntu
```
wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt-get update
sudo apt-get install jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins
```

## Access Jenkins

- Open your browser and navigate to http://<your_server_ip>:8080.

## Unlock Jenkins

- Retrieve the initial admin password:
```
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
- Enter the password in the Jenkins setup wizard.

# Jenkins CLI

## Jenkins CLI Installation

- Download the jenkins-cli.jar file from http://<your_jenkins_url>/jnlpJars/jenkins-cli.jar.

## Running Jenkins CLI
```
java -jar jenkins-cli.jar -s http://<your_jenkins_url>/ <command>
# Example:
java -jar jenkins-cli.jar -s http://localhost:8080/ who-am-i
```

# Managing Jobs

## Create a New Job

1. Open Jenkins dashboard.
2. Click on New Item.
3. Enter an item name and select a job type.
4. Configure the job and save.

## List All Jobs
```
java -jar jenkins-cli.jar -s http://<your_jenkins_url>/ list-jobs
```

## Trigger a Job
```
java -jar jenkins-cli.jar -s http://<your_jenkins_url>/ build <job_name>
# Example:
java -jar jenkins-cli.jar -s http://localhost:8080/ build myjob
```

## Get Job Status
```
java -jar jenkins-cli.jar -s http://<your_jenkins_url>/ get-job <job_name>
# Example:
java -jar jenkins-cli.jar -s http://localhost:8080/ get-job myjob
```

## Delete a Job
```
java -jar jenkins-cli.jar -s http://<your_jenkins_url>/ delete-job <job_name>
# Example:
java -jar jenkins-cli.jar -s http://localhost:8080/ delete-job myjob
```

# Jenkins Pipelines

## Simple Pipeline Example
```
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }
}
```

# Create a Pipeline Job

1. Open Jenkins dashboard.
2. Click on New Item.
3. Enter an item name and select Pipeline.
4. In the pipeline section, enter your pipeline script.
5. Save the job.

# Jenkins Plugins

## List Installed Plugins
```
java -jar jenkins-cli.jar -s http://<your_jenkins_url>/ list-plugins
```

## Install a Plugin
```
java -jar jenkins-cli.jar -s http://<your_jenkins_url>/ install-plugin <plugin_name>
# Example:
java -jar jenkins-cli.jar -s http://localhost:8080/ install-plugin git
```

## Uninstall a Plugin
```
java -jar jenkins-cli.jar -s http://<your_jenkins_url>/ uninstall-plugin <plugin_name>
# Example:
java -jar jenkins-cli.jar -s http://localhost:8080/ uninstall-plugin git
```

# Managing Nodes

## List Nodes
```
java -jar jenkins-cli.jar -s http://<your_jenkins_url>/ list-nodes
```

## Add a New Node
```
java -jar jenkins-cli.jar -s http://<your_jenkins_url>/ create-node <node_name>
# Example:
java -jar jenkins-cli.jar -s http://localhost:8080/ create-node mynode
```

## Delete a Node
```
java -jar jenkins-cli.jar -s http://<your_jenkins_url>/ delete-node <node_name>
# Example:
java -jar jenkins-cli.jar -s http://localhost:8080/ delete-node mynode
```

# Security and Users

## Create a New User
1. Open Jenkins dashboard.
2. Click on Manage Jenkins -> Manage Users -> Create User.
3. Fill out the user details and save.

## Manage Roles and Permissions

- Install and configure the Role-based Authorization Strategy plugin to manage roles and permissions.

# Resources

[Jenkins Documentation](https://www.jenkins.io/doc/)

This cheat sheet provides a comprehensive overview of Jenkins, covering basic concepts, common commands, managing jobs, pipelines, plugins, nodes, and security.
