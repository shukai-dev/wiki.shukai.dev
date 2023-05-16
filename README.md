# 欢迎来到 KAI Wiki

## 内容

机器人比赛与各大创新类赛事已经发展多年，有了许多商业化的套件和方案，但同时难度与竞争压力也在不断攀升，而且商业化的套件也并不一定是完善的，这些资料也可能因为封闭或是老旧过时而难以派上用场。初学者面对着这些赛事，可能会感到无从下手。另外，这个社团里的大多数学生来自于机械自动化学院与中欧工程学院，对计算机的相关知识了解不多，容易在电控、视觉等方面遇到困难。

为了方便热爱机器人创新的同学们入门，2023 年 5 月，我们启动了这个知识库项目。目前还有大量的内容需要完善，欢迎大家一起来为这个知识库添砖加瓦。

本项目受 [CTF Wiki](https://github.com/ctf-wiki/ctf-wiki/) 与 [OI Wiki](https://github.com/OI-wiki/OI-wiki) 启发，在此表示感谢。但与这两个项目不同的是，机器人与创赛的知识库需要涵盖的内容相当广泛（具体的内容范围可以参考 [学习路线](./docs/learning-path.md)），因此我们希望能够有更多相关专业的同学参与进来，共同完善这个知识库。

## 部署

本项目使用 [mkdocs-material](https://squidfunk.github.io/mkdocs-material/) 作为主题，使用 [mkdocs](https://www.mkdocs.org/) 作为静态网站生成器，使用 [Pipenv](https://pipenv.pypa.io/en/latest/) 管理依赖。目前本项目流量较小，因此为了优化中国大陆地区的访问速度，我们使用了 [Azure 静态 Web 应用](https://docs.microsoft.com/zh-cn/azure/static-web-apps/) 作为托管平台提供主站 <https://wiki.shukai.dev> 的服务，每个月有 100 GB 的免费流量。

### 构建

```bash
sudo apt install pipenv # 安装 Pipenv
pipenv install # 安装依赖
pipenv run mkdocs build # 构建
```

### 本地预览

```bash
pipenv run mkdocs serve # 本地预览
```

### 部署

```bash
pipenv run mkdocs gh-deploy # 部署到 GitHub Pages
```
