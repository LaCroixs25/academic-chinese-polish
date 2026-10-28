# academic-chinese-polish 学术中文润色

一个 Agent Skill，用于润色论文、学位论文、研究报告和摘要的中文表达。同一份 `SKILL.md` 同时适用于 Claude 和 OpenAI Codex。

## 它做什么

- 把口语改成克制的书面语，拆解长句，理顺衔接
- 统一术语，检查语法、“的地得”与标点
- 保留原意和论证强度：不改数值，不把“相关”写成“导致”，不加“首次”“填补空白”等拔高措辞，不改变引文标记的支持范围
- 有歧义的地方不替作者选择，单独列出待确认点

## 它不做什么

- 不代写研究内容，不补实验、数据或参考文献
- 不核验参考文献，不检查学校排版规范
- 收到“降重”请求时只做表达改写，不保证降低查重系统给出的重复率

## 安装

**Claude Code**

```bash
git clone https://github.com/LaCroixs25/academic-chinese-polish ~/.claude/skills/academic-chinese-polish
```

**Claude.ai**：下载本仓库的 zip，在 Settings → Capabilities → Skills 上传。

**Codex**

```bash
git clone https://github.com/LaCroixs25/academic-chinese-polish ~/.codex/skills/academic-chinese-polish
```

`agents/openai.yaml` 只供 Codex 读取界面信息，Claude 会忽略它。

## 用法

直接把原文发过去，例如：

> 帮我润色一下：实验结果表明，新模型的准确率从82.1%提升到了85.3%，提升了3.2%，效果非常明显。

可以指定“轻度润色”“深度润色”“只给润色稿”或“逐句对照”。

## 测试

[tests/cases.md](tests/cases.md) 里有 6 条用例和检查点，覆盖数值、因果、引用范围、口语、降重和术语。修改 `SKILL.md` 后，建议在新对话里逐条重跑。

当前状态：6 条用例均已在 Claude 上通过，每条运行 1 次。DOCX、LaTeX 文件和长文本尚未系统测试。

## 许可

[MIT](LICENSE)
