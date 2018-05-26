# Docker CppUTest

A Docker image with CppUTest, gcc, and CMake installed.

## Background

Images can be built from tags in the CppUTest repo (for example, v3.8)
or from a specific git commit to incorporate bugfixes (e.g. v3.8-bugfix).
CppUTest is installed to `/usr/local`.

## Build

```
$ docker build -t cpputest-v3.8 v3.8
```

## Run

### Build in Container

Mount the source code directory to the container. This ensures that the container
has access to the source code but that build results persist on the host.
The container is run as the current user. This prevents `root` from owning build results.

```
$ docker run \
    --rm --name cpputest-v3.8 \
    -it \
    --user $(id --user):$(id --group) \
    --mount type=bind,src=/path/to/host/source,dst=/path/to/container/source \
    -w /path/to/container/source \
    cpputest-v3.8 \
    bash
```

### Shell Into Container

To explore the contents of a container, run
```
$ docker run --rm --name cpputest-v3.8 -it cpputest-v3.8 bash
```
