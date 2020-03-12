# Docker Tools

A collection of scripts for maintaining Docker from the in- and outside.

## Host Scripts

The scripts provided inside the `scripts` directory are intended to be used on the host system of the Docker daemon.
These simplify several maintenance tasks or shorten common operations against the daemon.

### `docker-backup-volume`

Backup a volume by it's name.

### `docker-backup-container-volumes`

Backup all volumes used by a specific container.

### `docker-remove-dangling`

Cleanup dangling data from Docker. (images, volumes, networks)

## Container Scripts

The scripts provided inside the `container` directory are intended to be used inside a Docker container.
These simplify several informational tasks and provide useful helpers for common operations.
It is recommended to provision required scripts to the `/usr/bin` directory during the build process of your image.

### `hostip`

This script is a shortcut to retrieving the host IP address from inside the container.
It may be useful if you need to whitelist your host in some dynamic network configuration.

```bash
$ hostip
172.21.0.1
```

### `containerip`

This script is a shortcut to retrieving the current container IP addres from inside the container.
As the IP is not known during build-time this little helper can come in handy if your application depends on that information.

```bash
$ containerip
172.21.0.2
```
