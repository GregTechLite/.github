# 如何对整合包进行贡献

[**中文**](/docs/CONTRIBUTING_zh_cn.md) | [**英文**](/CONTRIBUTING.md)

感谢您有兴趣为 GregTech Lite 及其附属模组做出贡献。本文档面向初学者和首次贡献者。参与贡献即表示您同意遵守 [行为准则](/CODE_OF_CONDUCT.md)。

## 目录

- [开始之前](#开始之前)
- [如何贡献](#如何贡献)
  - [报告 Bug](#报告-bug)
  - [提出改进建议](#提出改进建议)
  - [代码贡献](#代码贡献)
  - [文档与本地化](#文档与本地化)
- [Pull Request](#pull-request)
- [分支策略](#分支策略)
- [提交信息](#提交信息)
- [代码风格](#代码风格)
- [配置开发环境](#配置开发环境)
- [审查与合并](#审查与合并)
- [许可证](#许可证)
- [问题咨询](#问题咨询)

## 开始之前

在贡献之前，请：

- 阅读 [行为准则](/CODE_OF_CONDUCT.md)。
- 搜索已有 Issue 和 Pull Request，避免重复。
- 对于较大的改动，先开 Issue 或 Discussion，让维护者给出反馈。
- 保持改动聚焦。一个 Pull Request 应只解决一个问题或实现一个功能。
- 在审查过程中保持尊重和耐心。

## 如何贡献

首先确认您想进行的贡献类型，然后阅读下方对应章节。

### 报告 Bug

欢迎报告错误，请在 Issue 区域预先填写对应的 Issue 模板。整合包所有的 Bug 反馈都集中于该仓库中，而不是我们的 [Core Mod](https://github.com/GregTechLite/GregTech-Lite-Core) 的 Issue 区域中，该区域仅供开发者与贡献者使用。

如果日志很长，请使用 GitHub Gist、Pastebin 等粘贴服务，不要直接把完整日志贴进 Issue。

### 提出改进建议

欢迎提出功能建议和平衡性讨论，请在 Issue 区域预先填写对应的 Issue 模板。

一份好的建议应包含：

- 您遇到的问题或需求。
- 您建议的解决方案。
- 使用场景和预期行为。
- 可能的替代方案。
- 对进度、平衡性或兼容性的影响。
- 您是否愿意实现它。

### 代码贡献

在编写代码之前：

- 对于较大的改动，先在 Issue 或 Discussion 中讨论设计。
- 遵循现有代码风格和项目结构。
- 保持改动聚焦，避免无关重构。
- 如果适用，添加或更新测试。
- 如有需要，更新文档和本地化文件。
- 除非项目明确要求，否则不要提交生成文件、IDE 文件或本地环境文件。
- 发起 Pull Request 前，确保项目能够成功构建。

### 文档与本地化

文档和本地化贡献同样很有价值。

- 修复拼写错误、表述不清和过时信息。
- 保持翻译术语一致。
- 添加或修改面向用户的文本时，尽可能更新相关语言文件。
- 不要格式化无关文档。

## Pull Request

除非维护者另有说明，所有 Pull Request 都应目标分支为 `main`。

Pull Request 标题必须使用以下格式：

```text
<type>: <Summary>
```

可用的类型：

- `feat`
- `refactor`
- `chore`
- `build`
- `ci`
- `fix`

规则：

- 类型必须是上方允许的类型之一。
- 类型后跟一个冒号和一个空格：`: `。
- 描述部分首字母大写。
- 不允许使用 scope，例如 `feat(ui): Add screen` 是不允许的。
- 标题末尾不加标点符号。

示例：

```text
feat: Add new machine configuration
fix: Make circuit recipe correct
refactor: Clean up recipe registration
```

一个 Pull Request 应该：

- 有清晰且符合上述格式的标题。
- 说明改了什么、为什么改、如何测试。
- 关联相关 Issue，例如 `Closes #123`。
- 聚焦于一个主题。
- 通过 CI/CD 检查。
- 回应审查意见并根据审查意见修改相关内容。

Pull Request 检查清单：

- [ ] 我已阅读 `CONTRIBUTING.md` 和 `CODE_OF_CONDUCT.md`。
- [ ] 我的分支基于最新的 `main`。
- [ ] 我没有直接在 `main` 上工作。
- [ ] 我使用了正确的分支命名规则。
- [ ] 我没有复用旧分支。
- [ ] 我运行了构建或相关测试。
- [ ] 如有需要，我更新了文档或本地化。
- [ ] 我的改动聚焦，不包含无关修改。
- [ ] 我的 PR 标题符合要求的格式。
- [ ] 我的提交信息符合要求的格式。

## 分支策略

默认分支为 `main`。由于 `main` 应保持稳定，因此不要直接向 `main` 推送。所有 Pull Request 都目标为 `main`。

### Force Push

通常不允许 force push。仅拥有 maintainer 权限的人员可以执行 force push，且仅限必要时。不要重写共享历史。如果你需要更新 Pull Request，请新增提交或将最新 `main` 合并到你的分支，而不是 force push。

### 如果您是 Member

如果您拥有仓库的 member 权限：

- 从最新的 `main` 新建分支。
- 分支命名规则为 `id/xxx`，例如：`ms/ui-rework`。
- 推送分支并向 `main` 发起 Pull Request。
- 不要直接在 `main` 上工作。

示例：

```bash
git switch main
git pull
git switch -c ms/ui-rework
# 进行修改
git push -u origin ms/ui-rework
```

### 如果你是外部贡献者

如果您没有 member 权限：

- Fork 仓库。
- 不要在您 fork 仓库的 `main` 分支上直接工作。
- 保持您 fork 的 `main` 干净，并定期与上游仓库同步。
- 每次贡献前，先将 fork 的 `main` 与上游 `main` 同步，然后基于它新建分支。
- 您 fork 仓库中的分支名不需要前缀，直接使用 `xxx`，例如：`ui-rework`。
- 不要重复使用同一个分支提交多个 Pull Request。
- Pull Request 合并或关闭后，同步 fork，并为下一次贡献新建分支。
- 从您的分支向上游 `main` 发起 Pull Request。

示例：

```bash
git remote add upstream <上游仓库地址>
git fetch upstream
git switch main
git merge --ff-only upstream/main
git push origin main
git switch -c ui-rework
# 进行修改
git push -u origin ui-rework
```

## 提交信息

Pull Request 中的 commit 消息必须遵循以下规则：

- 全部使用小写字母。
- 不加标点符号。
- 不使用 `feat:` 或 `fix:` 这类类型前缀。
- 保持简短并具有描述性。

示例：

```text
add new machine configuration
fix circuit recipe
update contribution guide
```

注意：PR 标题使用 `<type>: <Summary>` 格式，但 commit 消息不使用类型前缀。

## 代码风格

- 遵循项目现有风格。
- 如果项目提供了格式化、Lint 或 Checkstyle 配置，请使用它们。
- 不要格式化无关文件。
- 保持导入、命名和格式与附近代码一致。
- 保持本地化键一致。
- 除非项目已经使用，否则避免通配符导入。

## 配置开发环境

具体配置取决于您正在开发的部分。请始终查看 `README` 中要求的 JDK 版本、Gradle 版本和运行说明。

一般步骤：

1. 安装项目要求的 JDK 版本。
2. 安装 IDE，例如 IntelliJ IDEA。
3. Clone 仓库。
4. 将项目作为 Gradle 项目导入。
5. 构建项目。
6. 如果适用，运行客户端或服务端进行测试。
7. 如果您 fork 了仓库，添加 upstream 远程仓库。

示例：

```bash
git clone <仓库地址>
cd GregTech-Lite
./gradlew build
```

常见运行任务，如果可用：

```bash
./gradlew runClient
./gradlew runServer
```

在 Windows 上，请使用 `gradlew.bat` 代替 `./gradlew`。

如果您只修改整合包内容，请按照 Modpack 项目 `README` 或文档中的说明，在启动器或开发实例中测试整合包。

## 审查与合并

维护者会审查 Pull Request。在审查过程中：

- 及时回应反馈。
- 除非被要求，否则请在新提交中完成修改。
- 处理完意见后重新请求审查。
- 保持讨论聚焦且尊重他人。

当 Pull Request 被批准且 CI/CD 通过后，可能会被合并，最终合并策略由维护者决定，并非所有 Pull Request 都一定会被接受。

## 许可证

您贡献的内容将按项目相同许可证授权，详情请查看 `LICENSE` 文件。如果您贡献了需要额外标识的内容，将被放入 `NOTICE` 文件中。

## 问题咨询

如果您有问题，可以使用 Issue 或 Discussion，或在项目社区频道中提问，提问前请先搜索已有讨论。
