<p align="center">
  <img src="assets/readme-banner.png" alt="学术中文润色：保留原意、理顺表达、统一术语" width="100%">
</p>

<p align="center">
  <strong>让学术中文更准确、自然、易读。</strong><br>
  适用于论文、学位论文、研究报告与摘要的 Agent Skill<br>
  <sub>Claude · OpenAI Codex · MIT License</sub>
</p>

<p align="center">
  <a href="#润色示例">润色示例</a> ·
  <a href="#安装">安装</a> ·
  <a href="#怎么使用">怎么使用</a> ·
  <a href="#测试记录">测试记录</a> ·
  <a href="#使用边界">使用边界</a>
</p>

---

## 从表达入手，保留研究本身

将口语和冗余表达改为清楚、克制的书面语，理顺句子，统一术语，检查语法、“的地得”与标点。遇到研究含义不明确的地方，保留原表述并列出待确认点。

| 表达更清楚 | 术语更一致 | 论证有分寸 |
|---|---|---|
| 理顺长句、搭配与衔接 | 按定义和术语表统一用词 | 保留数据、引用与结论强度 |

> **“可能”仍是“可能”，“相关”仍是“相关”。**<br>
> 润色的目标是把已有研究说明白；有歧义的地方留给作者确认。

## 润色示例

**原文**

> 我们这个研究其实主要就是想看看，社区养老这块到底存在哪些问题，然后给出一些建议。

**润色后**

> 本研究主要考察社区养老中存在的问题，并提出相应建议。

去掉口语和重复，保留“主要”这一限定词。这是仓库测试用例中的表达示例；实际修改幅度可按你的要求调整。

## 安装

同一份 [SKILL.md](SKILL.md) 可用于 Claude 和 Codex。

### OpenAI Codex

```bash
git clone https://github.com/LaCroixs25/academic-chinese-polish ~/.codex/skills/academic-chinese-polish
```

### Claude Code

```bash
git clone https://github.com/LaCroixs25/academic-chinese-polish ~/.claude/skills/academic-chinese-polish
```

### Claude.ai

[下载仓库 ZIP](https://github.com/LaCroixs25/academic-chinese-polish/archive/refs/heads/main.zip)，在 **Settings → Capabilities → Skills** 上传。

<details>
<summary>关于 Codex 的界面配置</summary>

`agents/openai.yaml` 为 Codex 提供技能名称、简介与默认提示词；Claude 会忽略该文件。主要润色规则均保存在 `SKILL.md`。

</details>

## 怎么使用

安装后，直接给出原文和修改要求：

```text
请帮我润色以下论文段落，保留原意和论证强度。
有歧义的地方请单独列出，不要自行补充研究事实。

【粘贴原文】
```

按需要选择修改方式：

| 你的要求 | 处理方式 |
|---|---|
| 轻度润色 | 主要修正病句、冗余与标点 |
| 深度润色 | 调整句式和段落表达，保留研究内容与证据强度 |
| 只给润色稿 | 直接返回修改后的文本 |
| 逐句对照 | 按“原文／修改后／原因”展示 |

默认采用适度润色，先给修订稿；存在关键改动或实质歧义时再简要说明。整章或文件任务还需要 agent 具备相应的文档处理能力。

## 测试记录

测试材料包括 **18 条文本用例、3 个文件场景、20 条调用选择请求**，覆盖数值、引用、因果关系、术语、限定词、繁体与文件结构等情况。

| 执行环境 | 文本检查 | 调用选择 |
|---|---|---|
| Claude | 已报告红线检查点零失败 | 触发测试 60/60 |
| Codex | 原清单红线 48/48；非红线 85/90（94.4%） | 调用选择模拟 60/60 |

<details>
<summary>测试方法与文件验证状态</summary>

两组测试方法不同，不能直接据此比较模型优劣。Codex 的 18 条文本用例在三个独立上下文中分批执行，文件场景各运行一次；详细协议和评分边界见报告。

**文件验证状态**：Codex 已完成三个文件场景的结构检查。DOCX 版面检查因当次 agent 工具链环境限制未完成，单独记为“未验证”，不计作 skill 失败。执行时未遵守已有润色规则的现象也在报告中单独记录。

</details>

[查看测试用例](tests/cases.md) · [查看完整报告](tests/REPORT.md) · [查看 Codex 原始回复与评分](tests/codex-results.json)

## 使用边界

- 润色已有内容，不代写研究结论，不补实验、数据或参考文献。
- 不核验参考文献，不检查学校排版规范。
- 收到“降重”请求时可改写表达，不承诺降低查重系统给出的重复率。

---

[润色规则](SKILL.md) · [测试材料](tests/fixtures) · [MIT License](LICENSE)

