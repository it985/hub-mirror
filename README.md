# hub-mirror

使用 docker.io 或其他镜像服务来提供（但不限于） gcr.io、registry.k8s.io、k8s.gcr.io、quay.io、ghcr.io 等国外镜像加速下载服务

为减少重复请求，合理利用资源，建议提前在 issues 搜索镜像是否已转换过


# 原理

[无法拉取 gcr.io 镜像？用魔法来打败魔法](https://mp.weixin.qq.com/s/Vt0FRTx1PsoYFdLa0QZzWw)

# 开始使用

## 方案一：白嫖我的，点个 Star ，直接提交 issues

要求：严格按照模板规范提交

> 当任务失败时，可以查看具体失败原因并修改 issues 主体内容，无需新建 issues

限制：每次提交最多 11 个镜像地址（为啥是11个？因为我的第一次需求刚好要转换11个镜像🤣）

本人 Docker 账号有每日镜像拉取限额，请勿滥用

## 方案二：自己动手，丰衣足食，Fork 本项目，绑定你自己的 DockerHub 账号或其他镜像服务账号

1. 绑定账号

    - 如果要使用 DockerHub 的镜像服务

      在 `Settings`-`Secrets`-`Actions` 选择 `New repository secret` 新建 `DOCKER_USERNAME`（你的 Docker 用户名）
      和 `DOCKER_TOKEN`（你的 Docker 密码） 两个 Secrets

    - 如果需要使用其他镜像服务,例如腾讯云、阿里云等

      在 `Settings`-`Secrets`-`Actions` 选择 `New repository secret` 新建 `DOCKER_USERNAME`（你的其他镜像服务用户名）
      和 `DOCKER_TOKEN`（你的其他镜像服务密码）以及 `DOCKER_REPOSITORY` 三个 Secrets

      其中 `DOCKER_REPOSITORY` 配置例子：

        - 腾讯云: `ccr.ccs.tencentyun.com/xxxxxx`
        - 阿里云: `registry.cn-hangzhou.aliyuncs.com/xxxxxx`
        - 等其他云...

2. 在 Fork 的项目中开启 `Settings`-`General`-`Features` 中的 `Issues` 功能

3. 在 Fork 的项目中修改 `Settings`-`Actions`-`General` 中的 `Workflow permissions` 为 `Read and write permissions`

4. 在 `Issues`-`Labels` 选择 `New label` 依次添加三个 label ：`hub-mirror`、`success`、`failure`

5. 在 `Actions` 里选择 `hub-mirror` ，在右边 `···` 菜单里选择 `Enable Workflow`

```

