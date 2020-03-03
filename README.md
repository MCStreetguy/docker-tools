# Docker Tools

A collection of scripts for maintaining Docker from the in- and outside.

## Host Scripts

The scripts provided inside the `scripts` directory are intended to be used on the host system of the Docker daemon.
These simplify several maintenance tasks or shorten common operations against the daemon.

### `docker-backup-volume`

_WIP_

### `docker-remove-dangling`

_WIP_

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

### `randomport`

Generate a random port number. This may be useful for some dynamic network configuration or if your application needs to listen on ephermal ports.
Not provided any arguments, the script creates a private (/dynamic/ephermal) port number in the range of `49152-65535`.

```bash
$ randomport
60696
```

You may provide up to two additional arguments to change the port number range used.
The syntax is:

```bash
randomport [minimum_port=49152] [maximum_port=65535]
```

So for example:

```bash
$ randomport 1024
10838
$ randomport 1024 1500
1365
```

If you exceed the valid port range of `1-65535` or the minimum and maximum port numbers overlap, the script will print an error message and exit with code `1`.
