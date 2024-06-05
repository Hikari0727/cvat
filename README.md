# **CVAT - 计算机视觉标注工具**

使用 cvat 有几种方法--直接使用网页版或在本地部署应用程序。

# 网页版

要在网页模式下使用 cvat，需要访问: https://app.cvat.ai/auth/login 并注册/登录一个账户。可以使用 github 或谷歌账户登录。

# 本地安装

对于 Linux（Ubuntu）： 在终端窗口中输入以下命令安装 Docker 和 Docker Compose。其他说明请访问：https://docs.docker.com/engine/install/ubuntu/

```bash
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
```

安装后输入以下命令，即可在没有 root 权限的情况下运行 docker。

```bash
sudo groupadd docker
sudo usermod -aG docker $USER
```

重新登录（或重启），以重新评估你的群组成员身份。然后，你可以在终端窗口中输入 groups 命令，检查输出中是否有 docker 组。

下面的命令将从 GitHub 上的版本库克隆最新的 CVAT 开发分支：

```bash
git clone https://github.com/opencv/cvat
cd cvat
```

启动 Docker 容器。从 DockerHub 下载最新版本的 CVAT 和其他必要的镜像（如 postgres、redis 等）并创建容器，注意创建容器需要一些时间。

```bash
docker compose up -d
```

一旦所有容器都安装完毕，CVAT 将在 localhost:8080 上可用。要查看其他操作系统的安装情况，请参阅：[https://opencv.github.io/cvat/docs/administration/basics/installation/。](https://opencv.github.io/cvat/docs/administration/basics/installation/%E3%80%82)

# 创建项目

在 CVAT 中，您可以创建一个包含相同类型任务的项目。与项目相关的所有任务都会继承一个标签列表。要创建项目，请点击顶部菜单中的”Projects”，进入项目部分。在项目页面上，您可以使用搜索功能查看项目列表，或者点击 “+”按钮并选择 “Create a new project ”来创建新项目。

![img_6.png](https://github.com/Hikari0727/cvat/blob/main/cvat/img_6.png)

填写项目名称以及添加自己任务的标签。

![img_7.png](https://github.com/Hikari0727/cvat/blob/main/cvat/img_7.png)

![img_8.png](https://github.com/Hikari0727/cvat/blob/main/cvat/img_8.png)

# 创建标注任务

要在 CVAT 中开始标注，您需要创建一个标注任务并指定其参数。要创建任务，请在 “Tasks ”页面按 “+”并选择 “Create a new task”。

![截屏2024-06-04 14.07.13.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/02c6bfa9-02ad-44b9-bc04-a65d811feb93/f93bf629-8500-49d7-b35e-c86846987cdf/%E6%88%AA%E5%B1%8F2024-06-04_14.07.13.png)

或者，如果标注任务要添加到已经存在的项目中，可以直接从项目页面创建。

![截屏2024-06-04 14.09.49.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/02c6bfa9-02ad-44b9-bc04-a65d811feb93/49f2495c-c74e-40cd-8feb-3cb712173812/%E6%88%AA%E5%B1%8F2024-06-04_14.09.49.png)

接下来，在任务配置窗口中填写必填字段。

![截屏2024-06-05 12.10.15.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/02c6bfa9-02ad-44b9-bc04-a65d811feb93/085f614c-7ef3-435c-840a-cf8ede9a6e0d/%E6%88%AA%E5%B1%8F2024-06-05_12.10.15.png)

上传文件有几种方法，其中一种是从电脑上上传文件。

![截屏2024-06-05 12.11.20.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/02c6bfa9-02ad-44b9-bc04-a65d811feb93/aad69b0b-b9e8-417e-894b-28527649ea67/%E6%88%AA%E5%B1%8F2024-06-05_12.11.20.png)

任务可分为多个子任务，为此，您需要在高级配置部分选择一个子任务中包含的图像数量（分类大小）。

![img_13.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/02c6bfa9-02ad-44b9-bc04-a65d811feb93/5b344f0d-9294-426e-bce4-d04c7a149c02/img_13.png)

创建的任务如下：

![截屏2024-06-05 12.31.02.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/02c6bfa9-02ad-44b9-bc04-a65d811feb93/f5592b8f-04cd-487d-bfa2-c8427af19d05/%E6%88%AA%E5%B1%8F2024-06-05_12.31.02.png)

需要注意的是，您不仅可以导入图片，还可以导入视频。

# 图像标注

标注图像有几种方法：

- Rectangle или Bounding box
- Polygon
- Polyline
- Points
- Ellipse
- Cuboid
- Cuboid in 3d task
- Skeleton
- Tag

选择标记工具的按钮位于侧面板上。要标记矩形，请单击 “下一个 ”按钮，然后单击 “shape”。

![截屏2024-06-05 12.40.31.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/02c6bfa9-02ad-44b9-bc04-a65d811feb93/d67aa739-5f1f-4f6d-bac2-b32024b250a2/%E6%88%AA%E5%B1%8F2024-06-05_12.40.31.png)

![截屏2024-06-05 12.40.52.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/02c6bfa9-02ad-44b9-bc04-a65d811feb93/dd528a73-231f-4e74-beb1-9b9e8e933ccf/%E6%88%AA%E5%B1%8F2024-06-05_12.40.52.png)

对于分割任务，适合使用标记变体--多边形选择。为此，请按下以下按钮，然后选择 “shape”。

![截屏2024-06-05 12.44.12.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/02c6bfa9-02ad-44b9-bc04-a65d811feb93/641d2ffe-712f-4f7b-8d60-644afcc4b151/%E6%88%AA%E5%B1%8F2024-06-05_12.44.12.png)

![截屏2024-06-05 12.44.44.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/02c6bfa9-02ad-44b9-bc04-a65d811feb93/7343400b-0660-4894-91bd-484db10e1bfa/%E6%88%AA%E5%B1%8F2024-06-05_12.44.44.png)

其他标记类型的示例可在 CVAT 官方文档中找到。

如果要修改当前的标记，需要用 pcm 点击它，然后选择新的标记。

![img_19.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/02c6bfa9-02ad-44b9-bc04-a65d811feb93/dcae98fc-1e34-4160-b0db-0e452b809510/img_19.png)

在 “Objects ”侧边栏中，您可以看到当前帧中可用对象的列表。下图是该列表的示例：

![截屏2024-06-05 12.59.19.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/02c6bfa9-02ad-44b9-bc04-a65d811feb93/d0584043-3ae5-4736-9734-faf7c989a1df/%E6%88%AA%E5%B1%8F2024-06-05_12.59.19.png)

要查看任务的详细信息，您需要点击右上角的信息按钮。

![截屏2024-06-05 13.00.04.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/02c6bfa9-02ad-44b9-bc04-a65d811feb93/966b37d8-80a0-44ac-9f75-10f20c22f4a3/%E6%88%AA%E5%B1%8F2024-06-05_13.00.04.png)

弹出窗口将显示每种类型标签的数量信息。

![截屏2024-06-05 13.00.38.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/02c6bfa9-02ad-44b9-bc04-a65d811feb93/e3e5d5da-5943-456b-a225-4932d683e9ce/%E6%88%AA%E5%B1%8F2024-06-05_13.00.38.png)

# 导出/导入数据集和下载标签

## 数据集导出

您可以从项目、任务中导出数据集：

1. 要导出最新标签，必须先保存所有更改。
    
    ![截屏2024-06-05 13.15.11.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/02c6bfa9-02ad-44b9-bc04-a65d811feb93/87761c9f-cf3f-4128-b366-cf7039c0efae/%E6%88%AA%E5%B1%8F2024-06-05_13.15.11.png)
    
2. 然后按下菜单按钮。任务和项目数据集的导出和导入可通过操作菜单完成。
3. 按下导出任务数据集按钮。
    
    ![截屏2024-06-05 13.15.56.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/02c6bfa9-02ad-44b9-bc04-a65d811feb93/ffbacc7f-0107-4d3d-9456-4f10890317ae/%E6%88%AA%E5%B1%8F2024-06-05_13.15.56.png)
    
4. 选择导出数据集的格式并填写其他字段

## 导入数据集

您可以只将数据集导入一个项目。在这种情况下，数据将被分割成子集。要导入数据集，请在页面上执行以下项目操作：

![截屏2024-06-05 13.17.45.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/02c6bfa9-02ad-44b9-bc04-a65d811feb93/86d24d4d-ee09-44bf-bffe-9df59d57f949/%E6%88%AA%E5%B1%8F2024-06-05_13.17.45.png)

1. 打开操作菜单。
2. 单击“Import dataset”按钮。
3. 选择数据集格式（如果在导出时没有指定自定义名称，格式将出现在存档名称中）。
4. 将文件拖到文件上传区域，或单击上传区域在资源管理器中选择文件。
    
    ![截屏2024-06-05 13.19.35.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/02c6bfa9-02ad-44b9-bc04-a65d811feb93/bd5e3633-653d-48c1-8c15-81d53adf024c/%E6%88%AA%E5%B1%8F2024-06-05_13.19.35.png)
    

还可以从连接的云存储导入数据集。

## 上传标签

在任务或子任务中，您可以上传标签。为此，请从操作菜单中选择上传标签，选择要上传标签的格式，然后通过资源管理器选择标签文件或存档。或者也可以使用连接的云存储上传标签文件。

![截屏2024-06-05 13.21.40.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/02c6bfa9-02ad-44b9-bc04-a65d811feb93/bfd26fbc-a73f-4d80-a422-d21d5b542fd2/%E6%88%AA%E5%B1%8F2024-06-05_13.21.40.png)

![截屏2024-06-05 13.21.57.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/02c6bfa9-02ad-44b9-bc04-a65d811feb93/5b9eb403-7b26-487c-b22f-5b36e2dc7b26/%E6%88%AA%E5%B1%8F2024-06-05_13.21.57.png)

# 创建组织

要允许多个用户访问同一个项目，可以创建一个新的组织。要创建组织，请打开用户菜单，转到组织并单击“Create”。

![截屏2024-06-05 13.23.21.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/02c6bfa9-02ad-44b9-bc04-a65d811feb93/bc652579-11ef-4a86-9529-86f11ff76844/%E6%88%AA%E5%B1%8F2024-06-05_13.23.21.png)

填写创建组织所需的信息。您需要输入组织的简短名称，该名称将显示在菜单中。您还可以输入其他字段： 全名、描述和组织联系人。这些信息将在组织设置页面上显示。

![截屏2024-06-05 13.24.23.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/02c6bfa9-02ad-44b9-bc04-a65d811feb93/d7fb811f-6417-4a22-b5fc-caa8a0fda457/%E6%88%AA%E5%B1%8F2024-06-05_13.24.23.png)

要访问 “组织 ”页面，请打开用户菜单，转到 “组织 ”并单击 “设置”。

![截屏2024-06-05 13.24.54.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/02c6bfa9-02ad-44b9-bc04-a65d811feb93/4f642597-4992-4a26-819a-66617945c327/%E6%88%AA%E5%B1%8F2024-06-05_13.24.54.png)

要添加成员，请单击“Invite members”，在出现的窗口中，输入要添加的用户的电子邮件地址并选择角色（角色定义了一系列规则）： • Worker-该角色只能访问分配给他们的任务、项目和工作。• Supervisor-该角色允许您创建工作、任务和项目并将其分配给组织成员。• Maintainer- 拥有此角色的成员拥有主管角色的所有功能，可查看组织中其他成员创建的所有任务和项目，拥有对功能的完全访问权限，并可修改 Cloud Storages 成员及其角色。• Owner- 分配给组织创建者的角色，具有最大权限。

添加成员后，他们将出现在组织的设置页面上，列出每个成员和邀请的详细信息。您可以随时更改参与者的角色或删除参与者。

![截屏2024-06-05 13.27.25.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/02c6bfa9-02ad-44b9-bc04-a65d811feb93/080d1559-33e8-4b77-b6a6-129bcc2e5542/%E6%88%AA%E5%B1%8F2024-06-05_13.27.25.png)

在组织内创建的项目中，用户可以被分配到特定的任务和子任务中。

![截屏2024-06-05 13.27.53.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/02c6bfa9-02ad-44b9-bc04-a65d811feb93/6831af57-95b7-4b90-9575-a00a315c982d/%E6%88%AA%E5%B1%8F2024-06-05_13.27.53.png)

# 相关链接

官方 cvat 文档：https://opencv.github.io/cvat/docs/
