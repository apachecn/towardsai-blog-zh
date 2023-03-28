# 分分钟可以用 Docker 安装气流！

> 原文：<https://pub.towardsai.net/you-can-install-airflow-with-docker-in-minutes-66a3de44374f?source=collection_archive---------0----------------------->

![](img/033827c233828c559f2d9de076f49c81.png)

戴夫·霍夫勒在 [Unsplash](https://unsplash.com/s/photos/flow?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) 上拍摄的照片

你会在几分钟内用 Docker 安装好气流。

简单易懂，循序渐进的解释。你会喜欢的。

你将安装完整版本的气流。

此外，您将学习安装精简版的气流。

# **内容**

[**简介**](#9e6f)

[**气流安装—完整版**](#b8b6)

[**气流安装—简装版**](#13a0)

[**结论**](#d10d)

# **简介**

" Airflow 是一个由社区创建的平台，用于以编程方式创作、调度和监控工作流."([https://airflow.apache.org/](https://airflow.apache.org/))

气流是最著名的工作编排工具之一。

但是…

气流的安装比想象的要复杂。

通过本教程，您将获得易于遵循的两种不同的气流安装选项。

完成本教程后，您将在几分钟内准备好使用气流。

![](img/f875642335d35fe5ecd87fb39ea336da.png)

[https://airflow.apache.org/](https://airflow.apache.org/)

# 气流安装—完整版

在本教程中，我们将使用 Docker 版本的安装。我假设您的本地环境中有一个 Docker 桌面。让我们检查一下。

![](img/da07a5c12368d57774620e5ac2d5d71d.png)

作者捕获的图像

此外，查看使用中和/或停止的容器(如果有)。

![](img/dc843c30e4cfaa50a809f3db9de32c77.png)

作者捕获的图像

Docker 工作站是干净的，最后，让我们检查 docker-compose。

![](img/43e5cb5ba69d1274844a10b6a7ae0982.png)

作者捕获的图像

🛑确保你有最新版本的 docker-compose。

我们准备用 Docker 安装 Airflow-Full 版本。

让我们做基础的。

首先，创建一个新文件夹，并在那里开始工作。

![](img/94e8e8904980e4808b32fd83e3f30937.png)

作者捕获的图像

我们准备从气流网站获取 [**安装 yaml 文件**](https://airflow.apache.org/docs/apache-airflow/stable/docker-compose.yaml) 。

![](img/aaf23db90730584a1496d9a2d1350229.png)

作者捕获的图像

YAML 文件包含以下服务定义:

✅ **气流调度器**:调度器监控任务和 Dag

✅ **气流-网络服务器**:网络服务器服务于本地主机:8080

✅ **气流工人**:工人做调度给的工作

✅ **气流初始化**:初始化气流

✅ **花**:监控环境

✅ **postgres** :数据库

✅ **redis** :将消息从调度器转发到工作器。([https://air flow . Apache . org/docs/Apache-air flow/2 . 1 . 1/start/docker . html](https://airflow.apache.org/docs/apache-airflow/2.1.1/start/docker.html))

让我们看看 docker-compose.yaml 文件。

![](img/82d325f321981e62e34f5b9e86070d48.png)

作者捕获的图像

我们将安装最新版本的气流(2.4.0)。

我们可以看到气流服务的常见环境变量。

Airflow 有三个卷:Dag、日志和插件。

![](img/275933b2c4e93321b7815f1248b2acb6.png)

作者捕获的图像

在新文件夹下，我们需要为风量同步创建三个文件夹。

就这么办吧。

![](img/ce7c9c2c890580de510abc8eb4729604.png)

作者捕获的图像

继续看 YAML 的档案。

![](img/29eab7584babb7f6c7fa11470a941374.png)

作者捕获的图像

我们需要确保本地环境和 docker 容器之间的卷同步权限是相同的。

为此，我们需要在本地环境中定义环境变量。

![](img/ca315435a4eb3d1e27be0bb9dcfd426d.png)

作者捕获的图像

![](img/9575d9e117f213718e351509aa2e9296.png)

作者捕获的图像

我们准备用 Docker 初始化气流安装。

![](img/efcdee3409352819f39d9419314d7454.png)

作者捕获的图像

![](img/b53a114f37fcb7cf2bf65b3a927bb74c.png)

作者捕获的图像

安装成功完成。

使用“管理员”角色创建新用户“气流”。

现在我们已经准备好开始这些服务了。

![](img/b28c08d8ef62f716cafa4deddf19da1a.png)

作者捕获的图像

使用 **docker-compose-up** 命令，YAML 文件中定义的所有服务都开始工作。

让我们看看集装箱。

![](img/9156f3f8164a41167dd826f83773839c.png)

作者捕获的图像

集装箱是健康的。

让我们转到 web 浏览器，查看本地主机:8080

![](img/0f3030ef6b0dbae735419172a0971013.png)

作者捕获的图像

气流开始流动了。

让我们输入用户名和密码。

两者都是'**气流**'。

![](img/10d9726c9cd47dd8a24ecbab4ca48417.png)

作者捕获的图像

瞧

![](img/36160ca4345a9f0cb062343b0af635b9.png)

作者捕获的图像

我们已经用 Docker 在几分钟内安装了全气流版本。

![](img/75268b997523f57d5f2289e0ef26fd77.png)

图片来源:[https://giphy.com/](https://giphy.com/)

# 气流安装—精简版

我们在完整安装版本的 Airflow 中部署了多个容器。

正如所料，多个容器需要大量资源。

尽管我们在生产环境中需要这些容器来提供像 Kubernetes 这样的服务，但是在本地环境中，我们不需要使用所有这些容器。

我们需要稍微修改一下 YAML 文件，以节省大量资源。

我们开始吧。

首先，确保之前运行的容器已经停止。

![](img/062b7e4257e5ac4293a5c07e6d5a38ff.png)

作者捕获的图像

然后，确保之前拉出的气流相关图像已被删除。

![](img/7e3229e1808d61262d28ea6f03860e16.png)

作者捕获的图像

我们将按照完整安装阶段的步骤创建一个新文件夹。

![](img/b241d1791d43dfa0a2452f010899cc57.png)

作者捕获的图像

让我们修改 YAML 文件。

![](img/3b7d4944b4f9cad20670f29848033f91.png)

作者捕获的图像

首先将核心执行器从**加速执行器**改为**本地执行器**

![](img/c979172e5152a5aa8e3aafbb3dcaf992.png)

作者捕获的图像

并删除其他芹菜环境变量。

![](img/e4152fae72eb104e93e3be11c9aea006.png)

作者捕获的图像

然后移除 **redis** 服务。

![](img/eedb1a25a5a050c96de12db104d95600.png)

作者捕获的图像

并从依赖零件中移除 **redis** 条件。

![](img/a09c089861841aa1a1b89c2c28b124a3.png)

作者捕获的图像

移除**气流工人**服务

![](img/bc5aebd034bd00fcb8e678f49f391801.png)

作者捕获的图像

此外，移除**气流触发器**服务。

![](img/233e4e7627dfc7bc191594783bb809a6.png)

作者捕获的图像

最后，移除**花**服务。

![](img/f473dceb3459ff42c4b0513a8536e368.png)

作者捕获的图像

好的。我们有 YAML 档案的精简版。

参见下面 YAML 文件的最终版本。

```
---
version: '3'
x-airflow-common:
  &airflow-common
  image: ${AIRFLOW_IMAGE_NAME:-apache/airflow:2.4.0}
  environment:
    &airflow-common-env
    AIRFLOW__CORE__EXECUTOR: LocalExecutor
    AIRFLOW__DATABASE__SQL_ALCHEMY_CONN: postgresql+psycopg2://airflow:airflow@postgres/airflow
    AIRFLOW__CORE__SQL_ALCHEMY_CONN: postgresql+psycopg2://airflow:airflow@postgres/airflow
    AIRFLOW__CORE__FERNET_KEY: ''
    AIRFLOW__CORE__DAGS_ARE_PAUSED_AT_CREATION: 'true'
    AIRFLOW__CORE__LOAD_EXAMPLES: 'true'
    AIRFLOW__API__AUTH_BACKENDS: 'airflow.api.auth.backend.basic_auth'
    _PIP_ADDITIONAL_REQUIREMENTS: ${_PIP_ADDITIONAL_REQUIREMENTS:-}
  volumes:
    - ./dags:/opt/airflow/dags
    - ./logs:/opt/airflow/logs
    - ./plugins:/opt/airflow/plugins
  user: "${AIRFLOW_UID:-50000}:0"
  depends_on:
    &airflow-common-depends-on
    postgres:
      condition: service_healthy

services:
  postgres:
    image: postgres:13
    environment:
      POSTGRES_USER: airflow
      POSTGRES_PASSWORD: airflow
      POSTGRES_DB: airflow
    volumes:
      - postgres-db-volume:/var/lib/postgresql/data
    healthcheck:
      test: ["CMD", "pg_isready", "-U", "airflow"]
      interval: 5s
      retries: 5
    restart: always

  airflow-webserver:
    <<: *airflow-common
    command: webserver
    ports:
      - 8080:8080
    healthcheck:
      test: ["CMD", "curl", "--fail", "http://localhost:8080/health"]
      interval: 10s
      timeout: 10s
      retries: 5
    restart: always
    depends_on:
      <<: *airflow-common-depends-on
      airflow-init:
        condition: service_completed_successfully

  airflow-scheduler:
    <<: *airflow-common
    command: scheduler
    healthcheck:
      test: ["CMD-SHELL", 'airflow jobs check --job-type SchedulerJob --hostname "$${HOSTNAME}"']
      interval: 10s
      timeout: 10s
      retries: 5
    restart: always
    depends_on:
      <<: *airflow-common-depends-on
      airflow-init:
        condition: service_completed_successfully

  airflow-init:
    <<: *airflow-common
    entrypoint: /bin/bash
    command:
      - -c
      - |
        function ver() {
          printf "%04d%04d%04d%04d" $${1//./ }
        }
        airflow_version=$$(AIRFLOW__LOGGING__LOGGING_LEVEL=INFO && gosu airflow airflow version)
        airflow_version_comparable=$$(ver $${airflow_version})
        min_airflow_version=2.2.0
        min_airflow_version_comparable=$$(ver $${min_airflow_version})
        if (( airflow_version_comparable < min_airflow_version_comparable )); then
          echo
          echo -e "\033[1;31mERROR!!!: Too old Airflow version $${airflow_version}!\e[0m"
          echo "The minimum Airflow version supported: $${min_airflow_version}. Only use this or higher!"
          echo
          exit 1
        fi
        if [[ -z "${AIRFLOW_UID}" ]]; then
          echo
          echo -e "\033[1;33mWARNING!!!: AIRFLOW_UID not set!\e[0m"
          echo "If you are on Linux, you SHOULD follow the instructions below to set "
          echo "AIRFLOW_UID environment variable, otherwise files will be owned by root."
          echo "For other operating systems you can get rid of the warning with manually created .env file:"
          echo "    See: https://airflow.apache.org/docs/apache-airflow/stable/howto/docker-compose/index.html#setting-the-right-airflow-user"
          echo
        fi
        one_meg=1048576
        mem_available=$$(($$(getconf _PHYS_PAGES) * $$(getconf PAGE_SIZE) / one_meg))
        cpus_available=$$(grep -cE 'cpu[0-9]+' /proc/stat)
        disk_available=$$(df / | tail -1 | awk '{print $$4}')
        warning_resources="false"
        if (( mem_available < 4000 )) ; then
          echo
          echo -e "\033[1;33mWARNING!!!: Not enough memory available for Docker.\e[0m"
          echo "At least 4GB of memory required. You have $$(numfmt --to iec $$((mem_available * one_meg)))"
          echo
          warning_resources="true"
        fi
        if (( cpus_available < 2 )); then
          echo
          echo -e "\033[1;33mWARNING!!!: Not enough CPUS available for Docker.\e[0m"
          echo "At least 2 CPUs recommended. You have $${cpus_available}"
          echo
          warning_resources="true"
        fi
        if (( disk_available < one_meg * 10 )); then
          echo
          echo -e "\033[1;33mWARNING!!!: Not enough Disk space available for Docker.\e[0m"
          echo "At least 10 GBs recommended. You have $$(numfmt --to iec $$((disk_available * 1024 )))"
          echo
          warning_resources="true"
        fi
        if [[ $${warning_resources} == "true" ]]; then
          echo
          echo -e "\033[1;33mWARNING!!!: You have not enough resources to run Airflow (see above)!\e[0m"
          echo "Please follow the instructions to increase amount of resources available:"
          echo "   https://airflow.apache.org/docs/apache-airflow/stable/howto/docker-compose/index.html#before-you-begin"
          echo
        fi
        mkdir -p /sources/logs /sources/dags /sources/plugins
        chown -R "${AIRFLOW_UID}:0" /sources/{logs,dags,plugins}
        exec /entrypoint airflow version

    environment:
      <<: *airflow-common-env
      _AIRFLOW_DB_UPGRADE: 'true'
      _AIRFLOW_WWW_USER_CREATE: 'true'
      _AIRFLOW_WWW_USER_USERNAME: ${_AIRFLOW_WWW_USER_USERNAME:-airflow}
      _AIRFLOW_WWW_USER_PASSWORD: ${_AIRFLOW_WWW_USER_PASSWORD:-airflow}
      _PIP_ADDITIONAL_REQUIREMENTS: ''
    user: "0:0"
    volumes:
      - .:/sources

  airflow-cli:
    <<: *airflow-common
    profiles:
      - debug
    environment:
      <<: *airflow-common-env
      CONNECTION_CHECK_MAX_COUNT: "0"
    command:
      - bash
      - -c
      - airflow

volumes:
  postgres-db-volume:
```

我们需要确保本地环境和 docker 容器之间的卷同步权限是相同的。

为此，我们需要在本地环境中定义环境变量。

![](img/ca315435a4eb3d1e27be0bb9dcfd426d.png)

作者捕获的图像

我们准备安装气流精简版。

首先，初始化气流。

![](img/fac939f4c106e830d1d1119e03db1a9b.png)

作者捕获的图像

和 docker-组成了

![](img/b807bdae683b6cd0c87f2628a224661f.png)

作者捕获的图像

![](img/ee453ad66317512247cf507db80e9312.png)

作者捕获的图像

让我们看看集装箱。

![](img/8ebcf612798b880fe41ddeff51fe6818.png)

作者捕获的图像

集装箱是健康的。

让我们转到 web 浏览器，打开本地主机:8080

![](img/7649cee4f5d272ceb9ecf7caccce63c5.png)

作者捕获的图像

输入用户名和密码“airflow”并登录。

![](img/da37bc900f76bda9b1416e0bfa9d93b0.png)

作者捕获的图像

就是这样。我们在几分钟内安装了气流精简版。

![](img/af9e7f3a8609c8cb7bb30296d84fa987.png)

雷南·利马摄:[https://www . pexels . com/photo/photo-of-man-standing-on-hill-3364025/](https://www.pexels.com/photo/photo-of-man-standing-on-hill-3364025/)

# **结论**

我们已经用 Docker 介绍了两种不同版本的气流装置。

我们在几分钟内就在两个不同的安装选项中安装了气流。

[**在下面的**](https://medium.com/towards-artificial-intelligence/lets-orchestrate-with-airflow-step-by-step-airflow-implementations-8100d8fe58b0) 文章中，我们将讨论 ***气流*** 在本地环境上的实现。

本文是 [**工作流工具列表**](https://medium.com/@kaanboke/list/workflow-tools-e3da3a530ea5) 的一部分。你可以在 这里找到 [**系列的其他文章。**](https://medium.com/@kaanboke/list/workflow-tools-e3da3a530ea5)

我希望它有所帮助。

对了，喜欢题目的时候可以通过支持**来展示👏**

欢迎发表评论。谢谢你的时间。

# 万事如意🤘

如果你喜欢看我的内容， [*请考虑关注我*](https://medium.com/@kaanboke/membership) 。还有，你可以通过 [**订阅 Medium**](https://medium.com/@kaanboke/membership) 来支持其他作家和我。使用我的推荐链接不会额外花费你。