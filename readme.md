## Golang devcontainer

由 [microsoft/vscode-dev-containers](https://github.com/microsoft/vscode-dev-containers/) 修改而来，在中国的网络环境下能较快的正常构建 golang 开发环境。

### 使用

把项目克隆到当前项目的 `.devcontainer`

```bash
git clone --depth 1 https://github.com/geehon/golang-devcontainer.git .devcontainer
```

使用前检查是否存在数据网络 `data_net`,  不存在则创建网络

```bash
docker network create data_net
```

若不需要连接数据网络直接从配置文件 `devcontainer.json` 移除配置

```diff
"runArgs": [
    "--cap-add=SYS_PTRACE",
    "--security-opt",
    "seccomp=unconfined",
-   "--network=data_net",
    "--memory=1G",
    "--name=go-dev"
],
```

> **Note** 根据选择的镜像版本自行选择镜像

```
# 默认注释了源码镜像以提高 apt update 速度，如有需要可自行取消注释
deb https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye main contrib non-free
# deb-src https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye main contrib non-free

deb https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye-updates main contrib non-free
# deb-src https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye-updates main contrib non-free

deb https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye-backports main contrib non-free
# deb-src https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye-backports main contrib non-free

# deb https://mirrors.tuna.tsinghua.edu.cn/debian-security bullseye-security main contrib non-free
# # deb-src https://mirrors.tuna.tsinghua.edu.cn/debian-security bullseye-security main contrib non-free

deb https://security.debian.org/debian-security bullseye-security main contrib non-free
# deb-src https://security.debian.org/debian-security bullseye-security main contrib non-free
```
