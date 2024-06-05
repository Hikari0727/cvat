# **CVAT - 计算机视觉标注工具**
使用 cvat 有几种方法--直接使用网页版或在本地部署应用程序。
# 网页版
要在网页模式下使用 cvat，需要访问: https://app.cvat.ai/auth/login 并注册/登录一个账户。可以使用 github 或谷歌账户登录。
# 本地安装
对于 Linux（Ubuntu）： 在终端窗口中输入以下命令安装 Docker 和 Docker Compose。其他说明请访问：https://docs.docker.com/engine/install/ubuntu/
sudo apt-get update
sudo apt-get --no-install-recommends install -y \
  apt-transport-https \
  ca-certificates \
  curl \
  gnupg-agent \
  software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository \
  "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) \
  stable"
sudo apt-get update
sudo apt-get --no-install-recommends install -y \
  docker-ce docker-ce-cli containerd.io docker-compose-plugin
