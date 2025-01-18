[![JetBrains incubator project](https://jb.gg/badges/incubator-plastic.svg)](https://confluence.jetbrains.com/display/ALL/JetBrains+on+GitHub)


# About
Reference Dockerfile to get started with Docker or Remote toolchain in CLion.
Read more in CLion [Blog](https://blog.jetbrains.com/clion/2020/01/using-docker-with-clion/#major-updates)

## How to build and run
1. docker stop clion_remote_env && docker rm clion_remote_env
2. docker build --platform linux/amd64  -t clion/remote-cpp-env:0.5 -f Dockerfile.remote-cpp-env .
3. docker run --platform linux/amd64 -d --cap-add sys_ptrace -p127.0.0.1:2222:22 --name clion_remote_env clion/remote-cpp-env:0.5
4. ssh -p 2222 user@localhost
5. cd /workspace  && bazelisk build //...
6. alias docker-login-remote-cpp-env="docker exec -it \$(docker images | grep cpp-env | awk '{print $3}') /bin/bash"

## What I learnt
1. yes command used when creating new user in Dockerfile, since echo would display once, wheras yes would keep on displaying the same message.
2. passwd command used to set password for the user, it requires input to be entered twice hence yes is used.

## Reference
1.[Clion Remote youtube](https://www.youtube.com/watch?v=p7Bi-mOyelM&t=14s)

