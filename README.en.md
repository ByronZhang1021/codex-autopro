# Codex AutoPro

[中文](README.md) · [Skill instructions](SKILL.en.md)

Let Codex assign browser GPT-6 Pro analysis, code writing, or concrete deliverables, then retrieve, verify, and integrate the results. Codex decides the work and deliverable requirements; collaboration is not limited to advice.

- Collaborates automatically when complex analysis or implementation would benefit, without prior approval; permits necessary same-problem follow-ups and at most one automatic retry after a confirmed failed send.
- Codex supplies context and specifies deliverables, then performs local edits, validation, and Git commits within the original task authorization.
- Uploads code files, images, documents, and other material as needed; larger collections can be packaged as a ZIP, excluding secrets and unrelated content.
- Hands long waits to a host scheduler and saves the answer and conversation link.
- Pauses adoption of non-simple answers when thinking takes under two minutes or timing cannot be verified. This is a user-defined review rule, not proof of model quality or routing.

## Install

Clone this repository into your personal skills directory:

```sh
git clone https://github.com/ByronZhang1021/codex-autopro.git ~/.agents/skills/codex-autopro
```

## Use

Codex selects this skill automatically when useful, or you can invoke it explicitly. User restrictions on use, message count, and material take priority.

```text
$codex-autopro Ask GPT-6 Pro to review this proposal. Send once and report its conclusions alongside your verification.
```

Concrete implementation can also be assigned: “Have Pro use the relevant code to implement this fix and provide a patch, then verify, apply, and validate it.”

Requires a host with browser control, a signed-in account showing the target model, and a scheduler with browser recovery for unattended waiting. The skill supplies instructions, not those capabilities. If a requirement is unavailable, it reports the gap.

Chinese is the default; request English to switch. English instructions are linked above. Normal completion saves the result, removes the check automation, and closes the consultation tab; exceptions keep the tab open for inspection.

Uses web account quota and Codex usage; no model API calls. An independent community skill, not an official OpenAI integration.

## License

[MIT](LICENSE).
