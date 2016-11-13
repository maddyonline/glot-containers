fluent-containers -- a fork of glot-containers
===============
## Fork of https://github.com/prasmussen/glot-containers

Build binary for linux
```sh
docker run --rm -it -v $PWD/files:/go/bin/linux_386 -e GOPATH=/go -w /go/src/app -e GOOS=linux -e GOARCH=386 golang go get -v github.com/maddyonline/fluent
mv files/fluent files/runner
```

Build docker image(s)
```sh
docker build -t phluent/clang:latest -f clang/latest/Dockerfile .
docker build -t phluent/python:latest -f python/latest/Dockerfile .
```

Run docker container(s)
```sh
cat clang/latest/tests/cpp_hello_world/payload.json | docker run --rm -i phluent/clang
cat clang/latest/tests/cpp_hello_world/payload.json | docker run --rm -i phluent/clang -stream


cat python/latest/tests/hello_world/payload.json | docker run --rm -i phluent/python
cat python/latest/tests/hello_world/payload.json | docker run --rm -i phluent/python -stream
```

Push docker container(s)
```sh
docker push phluent/clang
docker push phluent/python
```

## Original README

## Overview
glot-containers are a collection of docker images that are used
by [glot.io](https://glot.io) to run code. The built images can be
found on [docker hub](https://hub.docker.com/r/glot/).
