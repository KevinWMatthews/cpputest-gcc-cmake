# CppUTest

A Docker image with CppUTest, gcc8, and CMake 3.13.1 installed.


## Tags and `Dockerfile` Links

Images are tagged with the CppUTest version first and, if a bleeding edge build,
the exact SHA. For example, `CppUTest v3.8` is tagged with `v3.8` while a build
with bugfixes after v3.8 could be `v3.8-2b45d38`. 

  * [cpputest-gcc-cmake:v3.8]()
  * [cpputest-gcc-cmake:v3.8-2b45d38]()

These images are updated as changes are make to the Dockerfiles.

Additionally, images are tagged with a date stamp `YYYMMDD:

  * cpputest-gcc-cmake:v3.8-2b45d38-2018120


## Build In Container

CppUTest is installed to the system in `/usr/local` so you can compile and link
against the system.

For rapid development, bind mount your source and build directories to the
container:

```bash
$ docker run \
    --rm -it \
    --user $(id --user):$(id --group) \
    --mount type=bind,src=/path/to/source/dir,dst=/usr/src/<source_dir> \
    --mount type=bind,src=/path/to/build/dir,dst=/usr/src/<build_dir> \
    --workdir /usr/src/<build_dir> \
    <image> \
    <command>
```

This will run the container, execute `<command>`, and exit the container.

Leave `<command>` blank to shell into the container.


### Permissions

When mounting code to the container, it is advisable to run the container
with current system user ID. If the container is run as root, all files
that the container touches in the source and build directories will be owned by root.

This can be prevented with `docker run`'s `--user` option. On Ubuntu Linux, use:

```bash
--user $(id --user):$(id --group)
```
or something similar.
