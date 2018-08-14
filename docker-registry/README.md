# docker-registry

Shellscripts allowing to start a local Docker Registry without authentication (`docker-registry`) and managing images pushed to it (`docker-registry-manage`).

## Managing the service

You can manage the service using the shellscript `docker-registry`.

The registry is started using a fixed directory for storage mounted as a volume in Docker container. This allows to easily backup the registry.

Docker image used: registry:2.

### Usage

```
Usage: $script_name (start | stop | restart | remove | status | logs)
```

- `start`: Starts the registry service, creating the Docker container if it does not exist.
- `stop`: Stops the registry service.
- `restart`: Restarts the registry service, stopping and restarting the container.
- `remove`: Stops and removes the service, removing the Docker container.
- `status`: Shows the service status.
- `logs`: Shows the Docker container logs.

### Customization

You can customize the service modifying the values of the following variables in the shellscript `docker-registry`:

```
# Registry home directory.
REGISTRY_HOME=$HOME/dev/docker-volumes/registry/
# Http port.
REGISTRY_HTTP_PORT=5000
# Container name used to execute.
CONTAINER_NAME=registry
```

- `REGISTRY_HOME`: Directory used to Registry's storage.
- `REGISTRY_HTTP_PORT`: HTTP port used to access the Registry.
- `CONTAINER_NAME`: Docker container name.

## Managing the images

In order to manage the images in the Registry you can use the shellscript `docker-registry-manage`. This script allows to list images and tags, or remove tags, in a Registry. Registry's RestAPI is used to launch the actions.

### Usage

```
Usage: $script_name (list_images <registry> | list_images_full <registry> | list_tags <registry> <image_name> | remove_tag <registry> <image_name>:<tag_name>)
```
- list_images <registry> - Lists all images in the registry.
- list_images_full <registry> - List all images in the registry including the list of all tags for each one.
- list_tags <registry> <image_name> - List all of the image's tags in a registry.
- remove_tag <registry> <image_name>:<tag_name> - Remove the <image_name>:<tag_name> from the registry, purging all files.