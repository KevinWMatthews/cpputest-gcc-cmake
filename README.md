# Docker CppUTest

A Docker image with CppUTest, gcc, and CMake installed.

## Background

Images can be built from tags in the CppUTest repo (for example, v3.8)
or from a specific git commit to incorporate bugfixes (e.g. v3.8-bugfix).

## Build

```
$ docker build -t cpputest-v3.8 v3.8
```

## Run

To launch a shell into the container.

```
$ docker run --rm --name cpputest-v3.8 cpputest-v3.8 bash
```
