# docker-buildx

使用 buildx 构建多架构镜像
Windows和Mac的桌面版Docker自带buildx命令，但是Linux环境下的Docker需要自行安装buildx （https://github.com/docker/buildx）
https://docs.docker.com/buildx/working-with-buildx/

一，
登录dockerhub
docker login
PS C:\Users\TIMES\（dockerfile目录）> docker login

Authenticating with existing credentials...

Login Succeeded

进入源码目录（Dockerfile所在目录）

git clone（库地址……）

cd 进入Dockerfile目录


二，构建
创建本地一个项目
PS C:\Users\TIMES\（dockerfile目录）> docker buildx create --name <自定义名字> --use
mybuilder

是否创建项目成功
PS C:\Users\TIMES\（dockerfile目录）>  docker buildx ls

NAME/NODE       DRIVER/ENDPOINT                STATUS   PLATFORMS
mybuilder *     docker-container
mybuilder0    npipe:////./pipe/docker_engine inactive
desktop-linux   docker
desktop-linux desktop-linux                  running  linux/amd64, linux/arm64, linux/riscv64, linux/ppc64le, linux/s390x, linux/386, linux/arm/v7, linux/arm/v6
default         docker
default       default                        running  linux/amd64, linux/arm64, linux/riscv64, linux/ppc64le, linux/s390x, linux/386, linux/arm/v7, linux/arm/v6

开始构建，构建命令示例如下
PS C:\Users\TIMES\（dockerfile目录）> docker buildx build --push --platform linux/arm/v7,linux/arm64/v8,linux/amd64 -t fifaty/openaibot:main .
