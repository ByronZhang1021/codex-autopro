# Codex AutoPro

[中文](README.md) · [Skill instructions](SKILL.en.md)

Let Codex ask ChatGPT Pro in your browser, wait for the answer, and check its advice against your task. Useful for code reviews, difficult questions, and proposal reviews.

- Sends one approved consultation; retries and follow-ups require authorization.
- Hands long waits to a host scheduler and saves the answer and conversation link.
- Pauses adoption of non-simple answers when thinking takes under two minutes or timing cannot be verified. This is a user-defined review rule, not proof of model quality or routing.

## Install

Clone this repository into your personal skills directory:

```sh
git clone https://github.com/ByronZhang1021/codex-autopro.git ~/.agents/skills/codex-autopro
```

## Use

```text
$codex-autopro Ask GPT-6 Pro to review this proposal. Send once and report its conclusions alongside your verification.
```

Requires a host with browser control, a signed-in account showing the target model, and a scheduler with browser recovery for unattended waiting. The skill supplies instructions, not those capabilities. If a requirement is unavailable, it reports the gap.

Chinese is the default; request English to switch. English instructions are linked above. Normal completion saves the result, removes the check automation, and closes the consultation tab; exceptions keep the tab open for inspection.

Uses web account quota and Codex usage; no model API calls. An independent community skill, not an official OpenAI integration.

## License

[MIT](LICENSE).
