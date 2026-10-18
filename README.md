# 项目提示词库

保存从完成项目中提炼的可复用提示词，并通过 Git 历史持续迭代。

配套 Codex skill：[project-prompt-evolver](https://github.com/michael061122-star/project-prompt-evolver)。本库维护策略为检查通过后自动提交到 `main` 的 `prompts/` 目录；此说明不向其他用户或程序授予写权限。

## 检索与复用

在 prompts/ 中按任务类型浏览，或搜索标题、summary、tags。安装配套 skill 后，可以直接让 Codex 从本库检索、读取固定提交的提示词，并记录本次实际使用版本。

手动复用时复制 prompt.md 的完整内容（包括前言元数据），填写所需输入；最好同时携带 GitHub 的固定提交链接。文件、模板、数据和工具等依赖需要另外提供，不应虚构不存在的素材。

## 沉淀与迭代

项目完成且有验收依据后，调用配套 skill：

```text
使用 $project-prompt-evolver，当前项目已验收。
将有效经验沉淀到 michael061122-star/project-prompt-library。
如果本项目使用了已有提示词，基于实际使用版本进行迭代；
没有新增可复用经验时保持原版。沿用已配置的自动发布策略。
```

每个条目保留完整当前提示词和按版本记录的变更说明，历史原文保存在 Git 中。更新保留 ID，实质不同的任务建立关联变体。迭代可以删除过时规则，并非只增加内容。

## 目录

```text
prompts/<id>/prompt.md
prompts/<id>/changes/<version>.md
examples/report-ppt/prompt.md
```

prompts/ 初始为空，等待真实完成项目沉淀。examples/ 的汇报 PPT 仅用于演示格式，未经过实际项目验证，不作为成功经验条目参与默认检索。

## 内容规则

提示词应包括适用条件、参数、执行方法、关键决策、验收及交付要求。不得上传原始聊天、密钥、客户信息、内部数据或未经允许公开的资料。只发布经过脱敏和复查的通用方法及变更说明。

验证级别：reviewed 为内容检查，single-project 为明确项目使用并验收，replayed 为代表任务重新执行；说明实际范围，不能把未做的验证写成通过。

格式规范由 [配套 skill](https://github.com/michael061122-star/project-prompt-evolver/blob/main/skills/project-prompt-evolver/references/formats.md) 维护。开源许可为 MIT，仅向本库提交你有权按该许可公开的内容。
