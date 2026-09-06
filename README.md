# ChatGPT Pro

[中文](README.zh-CN.md) · [Skill instructions](SKILL.md)

A Codex skill for consulting GPT-6 Pro through your signed-in ChatGPT browser session, with explicit authorization and recoverable waiting.

- Sends one approved consultation; retries and follow-ups require authorization.
- Hands long waits to a host scheduler and saves the answer and conversation link.
- Pauses adoption of non-simple answers when thinking takes under two minutes or timing cannot be verified. This is a user-defined review rule, not proof of model quality or routing.

## Install

Clone this repository into your personal skills directory:

```sh
git clone https://github.com/ByronZhang1021/chatgpt-pro.git ~/.agents/skills/chatgpt-pro
```

## Use

```text
$chatgpt-pro Ask GPT-6 Pro to review this proposal. Send once and report its conclusions alongside your verification.
```

Requires a host with browser control, a signed-in account showing the target model, and a scheduler with browser recovery for unattended waiting. The skill supplies instructions, not those capabilities. If a requirement is unavailable, it reports the gap.

English and Chinese instructions are included. Responds in the user's language. Normal completion saves the result, removes the check automation, and closes the consultation tab; exceptions keep the tab open for inspection.

Uses web account quota and Codex usage; no model API calls. An independent community skill, not an official OpenAI integration.

## License

[MIT](LICENSE).
