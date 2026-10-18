# project-prompt-library · 可复用项目提示词库

保存从已完成项目中提炼的可复用提示词，通过 Git 记录来源、迭代与变更说明。配套工具是 [project-prompt-evolver](https://github.com/michael061122-star/project-prompt-evolver)，一个在 Codex 中执行检索、沉淀和发布流程的 skill。

## 项目解决什么问题

项目完成后，分散在对话与文件中的有效方法难以直接用于下次任务。没有统一的存放方式和版本来源，提示词也容易重复、失去适用边界，或在修改时覆盖已有改进。

project-prompt-library 提供统一的提示词存放位置，让方法可以被检索、复制、按参数使用，并在后续项目验收后继续迭代。原文历史由 Git 保存，变更说明解释每次修改及实际验证范围。

## 主要功能与真实能力边界

| 功能 | 实际行为 |
|---|---|
| 查找方法 | 按任务目标、标题、摘要和标签查找条目，再读取完整内容确认适用性。 |
| 复制使用 | 每个 prompt.md 包含元数据及完整 Markdown 指令，声明输入、执行方法、依赖、验收和交付要求。 |
| 追踪迭代 | 使用稳定 ID 和版本，记录来源仓库、路径、提交与原文哈希；更新、关联变体与无变化分别处理。 |
| 查看历史 | 当前完整原文与版本变更记录保存在仓库，历史原文通过 Git 提交查看。 |
| 配合 Codex 维护 | 安装 project-prompt-evolver 后，可在验收后按已有授权自动提交，或自动创建 PR。 |

本仓库是**内容库**，没有独立运行的服务，也不会自行调用模型、监控聊天、训练模型或触发发布。检索、提炼和语义比较由 Codex 配合 skill 及可用工具执行；辅助脚本只处理本地文件。

条目不能代替实际素材、模板、数据、权限或工具。只有实际可读取的过程可以作为提炼依据；成功项目不自动证明新提示词已在其他项目复现，也不保证免除后续沟通与修改。

验证状态为 `reviewed`（内容检查）、`single-project`（明确项目使用并验收）、`replayed`（代表任务重新执行），以条目写明的实际范围为准。初始化时不预置已验收条目，后续可用内容以 `prompts/` 的实际文件为准。

配套 skill 第一版的受限发布清单只包含提示词和该版本变更说明两个 UTF-8 文件，针对 github.com；不自动上传素材附件、不自动跨库导入、不支持 GitHub Enterprise，PR 模式不自动合并。公开前需要脱敏和语义复查，常见敏感内容扫描不能代替判断。

## 安装方法

### 直接阅读或克隆提示词库

在 GitHub 阅读和复制提示词不需要安装程序。需要本地工作副本时，使用 Git：

```sh
git clone https://github.com/michael061122-star/project-prompt-library.git
cd project-prompt-library
git status -sb
```

克隆建立本地仓库与 origin 的关联，不授予远端写入权限。

### 在 Codex 中安装配套 skill

到 [project-prompt-evolver Releases](https://github.com/michael061122-star/project-prompt-evolver/releases) 下载 **v1.0.0** 的 `project-prompt-evolver-v1.0.0.zip`。解压后将完整 `project-prompt-evolver/` 目录放到 `$CODEX_HOME/skills/project-prompt-evolver/`；未设置 `CODEX_HOME` 时使用 `~/.codex/skills/project-prompt-evolver/`。

在新 Codex 聊天中调用 `$project-prompt-evolver`。辅助工具需要 Python 3.10 或更高版本，仅依赖标准库；远端检索和发布分别需要实际读取、原子写入及分支前提检查能力。详情见 [project-prompt-evolver 安装说明](https://github.com/michael061122-star/project-prompt-evolver#安装方法)。

首次维护时，明确目标和已有授权：

```text
使用 $project-prompt-evolver。
将 michael061122-star/project-prompt-library 设为提示词库。
允许在 prompts/ 下维护经过脱敏和复查的提示词及版本变更说明，检查通过后自动提交到 main。
将已有授权与配置保存在个人配置中，后续同范围调用沿用。
```

只有对本库有写入权限且获得相应授权时才使用上述目标；维护自己的库时应替换为实际仓库名。配置记录不会授予 GitHub 权限。支持 `direct` 自动提交及 `pr` 自动创建 PR；不因下载提示词而自动获得发布授权。

## 使用方法

### 1. 查找并应用提示词

在 `prompts/` 中浏览，或让 Codex 检索：

```text
使用 $project-prompt-evolver，从已配置的提示词库查找适合当前项目的方法。
核对适用条件与依赖，记录实际使用版本，填写本次输入后继续执行项目。
```

手动使用时复制 prompt.md 的完整内容，保留元数据，最好携带固定提交链接；按 `inputs` 提供参数，并满足 `requires` 中的依赖。正文参数采用 `{{input_name}}`。找不到合适条目时，应先完成实际项目，验收后再提炼新条目。

### 2. 验收后沉淀或迭代

```text
使用 $project-prompt-evolver，当前指定目标已验收。
基于实际可读取的过程和结果提炼通用方法，按已有配置发布。
如本次使用过提示词，核实实际使用版本后迭代；没有新增可复用经验时保持原版。
```

通用修正更新原 ID；流程或验收有实质差异时建立关联变体。远端已有更新时，比较实际使用原版、最新版与候选，保留其他有效改进。上下文、来源、验证或权限不足时保留草稿，不把它报告成已发布成果。

只想查看拟修改内容时：

```text
使用 $project-prompt-evolver，为当前已完成目标生成沉淀预览，暂不发布。
```

### 3. 查看条目与变更

```text
prompts/<id>/prompt.md
prompts/<id>/changes/<version>.md
```

prompt.md 前言采用 `---` 包围的 JSON 对象，其后为完整 Markdown 提示词。更新保留 ID 并确定合适版本，历史原文通过 Git 查看；每个版本的变更说明记录修改原因及真实验证范围。

不得上传原始聊天、访问令牌、客户资料、内部数据、个人路径或未经允许公开的素材。本地 `.prompt-evolver/` 中的来源快照、review 和回执不进入公开库。

格式由 [project-prompt-evolver 的规范](https://github.com/michael061122-star/project-prompt-evolver/blob/main/skills/project-prompt-evolver/references/formats.md) 维护。本库采用 [MIT 许可证](LICENSE)，只提交有权按此许可公开的内容。
