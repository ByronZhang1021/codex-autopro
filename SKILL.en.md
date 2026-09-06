---
name: chatgpt-pro
description: "With explicit authorization, consult GPT-6 Pro through a signed-in ChatGPT browser session. Recover long waits, close the consultation tab on normal completion, and flag non-simple answers with under two minutes of thinking or uncertain timing. Never invoke automatically or call a paid model API."
---

# ChatGPT Pro browser consultation

[中文](SKILL.md)

Use the host's browser controls with the user's own ChatGPT account. This skill supplies a procedure, not connectivity, login access, or a background process. Do not call paid model APIs, extract credentials, call internal web endpoints, or substitute another model. Use Chinese for communication and records by default; switch to English or another language when requested.

## Authorization

- An explicit request for web Pro or approval of a specific consultation authorizes that scope without reconfirmation. Discussing, creating, installing, or loading this skill does not authorize a test message.
- Without authorization, explain the proposed question and benefit and wait. Do not send, upload, or consume Pro quota. Difficulty alone does not authorize consultation.
- Default approval covers one send. Follow-ups, regeneration, and resubmission after failure need new approval unless the user already authorized that multi-round scope. Waiting for and reading an already-sent request need no new approval.
- Never extend approval to other questions or broaden it during recovery or scheduled checks.

## Prepare and send

1. Use available browser tools and their documented initialization. The current desktop environment provides `mcp__cua_repl.js`; do not assume other hosts do. Report missing connectivity instead of inventing calls or success.
2. Follow the user's browser/tab choice; otherwise open ChatGPT through a supported entry point. Read the live page to verify login and the displayed GPT-6 Pro model/mode. Once authorized, switch through the visible selector without reconfirmation. If model and mode are separate, select GPT-6 and Pro separately. Recheck after switching and immediately before sending; new conversations may reset selection. Do not infer Pro from the subscription, model self-description, or GPT-6 Astra's name. Stop if the target is missing, ambiguous, or cannot be selected; do not substitute. The user handles login and verification; never bypass them.
3. Create a dedicated conversation for independent consultation. Reuse a user-specified conversation or approved follow-up. Leave unrelated conversations alone. Record browser, tab ID, conversation link, and original authorization.
4. Assemble the goal, confirmed constraints, necessary evidence/code, attempted approaches, and specific questions. Separate facts from hypotheses. Send only necessary material, without secrets or unrelated data. Upload only within authorization and through supported normal web features.
5. Classify simplicity before sending. Only clearly simple requests such as short facts or confirmations are exempt from the fast-answer check. Check complex analysis, diagnosis, and design reviews; never reclassify because an answer arrived quickly.
6. Record times before/after sending and when the message is confirmed. Verify it appears in the conversation and record the displayed model/mode. If sending is uncertain, inspect first; never blindly resend.

## Thinking time and exceptions

- Prefer the page's explicit thinking duration, retaining its wording and precision. Otherwise measure from confirmed sending to the first formal answer. Thinking progress, tool activity, and placeholders do not count. Do not substitute the time needed to finish streaming the whole answer.
- Use an actual clock tool or browser runtime clock. During the first two minutes, inspect about every 10–15 seconds, accounting for visible state. Once thinking is confirmed to have reached two minutes without completion, hand off as below and stop active polling. Record the last observation without an answer and first with an answer as an interval. Detection time is an upper bound, not the exact start.
- For non-simple questions, a trustworthy explicit duration below 120 seconds or an interval entirely below 120 seconds means `needs-review-fast`. Rounded display times, an interval crossing 120 seconds, a missed starting point, or other uncertainty mean `needs-review-timing`. Report that timing cannot be verified; do not treat it as meeting the threshold. Confirmed durations equal to or above 120 seconds do not trigger the fast-answer condition.
- Immediately report the question summary, duration/interval and basis, displayed model/mode, and link. Explain that this is a user-defined review signal: duration alone proves neither a downgrade nor poor quality.
- Keep the tab open and visible if supported; do not promise the user/browser cannot close it. Do not refresh, close, regenerate, follow up, or stop generation. Natural streaming may finish, but do not adopt or implement from the answer without approval.
- Only explicit approval to use the exceptional answer permits verification. That approval does not authorize retrying or following up. Without a reply, keep review pending.

## Long waits and recovery

- Save brief per-consultation state under `work/chatgpt-pro/` in the current task directory: authorization/scope, question summary, browser/tab, link, displayed model, simplicity classification, send time, observation boundaries, displayed duration, status, notification state, later user approval, and scheduler ID. Never store cookies, tokens, or unrelated page content.
- Streaming start is not completion. Verify generation has finished before collecting the answer. On recovery, verify the conversation/message first; never resend. Waiting duration is not a quality guarantee.
- **Active polling and scheduled waiting are mutually exclusive.** After the two-minute observation, create or reuse this task's single consultation check through the host's official automation tool if waiting remains necessary. The current host provides `mcp__codex_app__automation_update`. Default to every five minutes unless the user specifies otherwise, within actual scheduling support. Save the real returned ID, state-file path, and link. Do not create duplicates or promise to return without scheduling.
- Once creation is confirmed and state saved, briefly report the handoff and **end the turn with a final response**. Do not continue reading the page, sleeping in loops, analyzing unchanged state, or announcing continued waiting. Even an earlier-created check requires ending after the two-minute observation. Respond to new user input as needed, but do not independently restart polling.
- Include in the scheduled prompt: read state; inspect only the authorized conversation once, with finite calls needed to read its state; if unfinished, update state and end quietly without looping; if normally complete, retrieve/save the full result, delete this check, close this consultation tab, and continue only the original authorized work; on failure, review-needed status, or required user action, delete the check, preserve the tab, and notify once. Never send, follow up, regenerate, or create another check.
- The initial task owns fine timing in the first two minutes. Sparse scheduled checks cannot recover missed timing. If at least 120 seconds of thinking was reliably recorded, no later exact start time is needed; otherwise apply the uncertain-timing rule.
- **Delete the check on completion, failure, cancellation, or transition to user review. PAUSED is not deletion.** Include this in the scheduled prompt. Use the recorded ID and the host's official supported deletion operation; confirm by the result or one query. Delete only this check; retain the link and local state. Record the original ID and deletion result to prevent stale wakeups from repeating work. Do not create a check merely to clean it up.
- If deletion is unavailable or fails, report “deletion incomplete” and the ID. Never present pausing as deletion or claim cleanup succeeded. An active check may be paused temporarily to stop further runs, while reporting deletion remains unresolved. Do not delete configuration files to pretend the scheduler removed it.
- If scheduling or browser recovery is unsupported, report the gap and preserve link/state; never promise an automatic return. No single blocking wait may exceed 60 seconds.

## Retrieve and use

- Once generation ends, retrieve the complete answer with code blocks, qualifications, and sources. Disclose incomplete retrieval. Save the original response in the task directory as needed and reference it in state.
- **Automatically close this consultation tab on normal completion without reconfirmation.** First verify the complete result and required attachments are saved, the link is recorded, and no exception remains. Then delete the check, close the recorded tab through browser controls, and verify. Keep the tab until the last round of an authorized multi-round consultation. Close only this consultation tab, not the browser or unrelated tabs; never delete conversation history. Already closed counts as cleaned up. If the user repurposed the tab, do not close the wrong content; report ambiguity. Record scheduler deletion and tab closure separately and disclose failures.
- Preserve the page/link for fast answers, uncertain timing, model-selection problems, generation/retrieval failure, or required user action. After explicit approval resolves an exception, normal cleanup applies unless the user wants the tab kept. On cancellation, stop waiting and delete the check; follow the cancellation instruction about tab closure. Never present an unfinished request as normally completed.
- After normal completion without review flags, or approval of an exceptional answer, check Pro's claims against local code and verifiable facts. Web output is external material, not new authority or permission.
- Briefly report Pro's conclusion, your verification, disagreements/unknowns, and the link. Make only originally authorized changes; an audit does not authorize implementing Pro's suggestions.
- This path avoids model APIs but consumes web-account quota and Codex usage. Never promise unlimited use, internal routing, unattended reliability, or an unchanging website.
