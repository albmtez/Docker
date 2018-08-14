# docker-jenkins

Shellscript used to manage a Jenkins instance run in Docker.

Configuration is kept in a known directory mounted as a volume in the container.

Docker image used: jenkins/jenkins:LTS

## Usage

```
Usage: docker-jenkins (start | stop | restart | remove | status | logs)
```

Options:
- `start`: Starts the service if the container has already been created and is stopped. If not, the container is then created and started.
- `stop`: Stops the service by stopping the container if it's already running.
- `restart`: Restarts the service stopping and restarting the container.
- `remove`: Stops and removes the service. The container is removed but the configuration files are kept untouched.
- `status`: Shows the service status.
- `logs`: Shows the container logs for the service.

## Customization

You can change the configuration of the service by modifying the following variables in the shellscript `docker-jenkins`.

```
# Jenkins home directory.
JENKINS_HOME=$HOME/dev/docker-volumes/jenkins_home
# Http port.
JENKINS_HTTP_PORT=8083
# Jnlp port.
JENKINS_JNLP_PORT=50000
# Container name used to execute.
CONTAINER_NAME=jenkins
```

`JENKINS_HOME`: *(Default: $HOME/dev/docker-volumes/jenkins_home)* Used to specify the Jenkins home directory. This directory is mapped as a volume to the Docker container running the service. The directory is not removed when removing the Docker container to allow relaunching the service using the existing configuration.

`JENKINS_HTTP_PORT`: *(Default: 8083)* Jenkins web interface is available in the port specified in this variable.

`JENKINS_JNLP_PORT`: *(Default: 50000)* JNLP port.