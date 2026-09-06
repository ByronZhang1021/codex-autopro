# ChatGPT Pro

[English](README.md) · [Skill 规则](SKILL.zh-CN.md)

让 Codex 经明确授权，通过已登录的 ChatGPT 网页咨询 GPT-6 Pro，并接续长时间等待。

- 每次发送一个已批准的问题；重试和追问需要授权。
- 长任务交给宿主定时检查，保存完整回答和会话链接。
- 非简单问题思考不足两分钟或计时无法确认时，暂停采纳、交由用户检查。这是自定义检查规则，不是模型质量或内部路由的证明。

## 安装

将仓库克隆到个人 Skill 目录：

```sh
git clone https://github.com/ByronZhang1021/chatgpt-pro.git ~/.agents/skills/chatgpt-pro
```

## 使用

```text
$chatgpt-pro 请 GPT-6 Pro 审查这个方案。只发送一次，结合你的核验报告结论。
```

需要宿主提供浏览器控制、已登录且能选择目标模型的账户；无人值守等待还需要定时调度和浏览器恢复能力。Skill 本身不提供这些能力，缺失时会明确报告。

包含中英文规则，按用户语言交流。正常结束后保存结果、删除检查自动化并关闭咨询标签页；异常时保留网页供检查。

消耗网页账户额度和 Codex 用量，不调用模型 API。独立社区 Skill，非 OpenAI 官方集成。

## 许可证

[MIT](LICENSE)。
