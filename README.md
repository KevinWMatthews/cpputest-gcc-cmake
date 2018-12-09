# CppUTest

A Docker image with CppUTest, gcc8, and CMake installed.


## Tags and `Dockerfile` Links

Images are tagged with the CppUTest version first and, if a bleeding edge build,
the exact SHA. For example, `CppUTest v3.8` is tagged with `v3.8` while a build
with bugfixes after v3.8 could be `v3.8-2b45d38`. 

  * [cpputest-gcc8-cmake3.13.1:v3.8]()
  * [cpputest-gcc8-cmake3.13.1:v3.8-2b45d38]()

These images are updated as changes are make to the Dockerfiles.

Additionally, images are tagged with a date stamp `YYYMMDD:

  * cpputest-gcc8-cmake3.13.1:v3.8-2b45d38-2018120


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
