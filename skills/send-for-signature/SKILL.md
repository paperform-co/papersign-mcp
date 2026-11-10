---
name: send-for-signature
description: Prepare a Papersign document from a template and send it for e-signature only after explicit confirmation. Use when the user says "send this for signature", "get this contract signed", "send an agreement to sign", "e-sign this".
---

# Send for signature

## Expected input

Which template or document to use, each signer's name and email, and any values to fill in (names, dates, amounts).

## Steps

1. Call `whoami`. Sending documents for signature needs Papersign on the account. If it is unavailable, say so plainly and stop.
2. Find the template with `search` or `list`. If several match, ask which one.
3. Call `fetch` on the template to see its signer roles and fillable fields.
4. Collect any missing signer names, emails and field values. Never guess an email address.
5. Call `create` to prepare the document from the template with the confirmed values.
6. Show the user a summary: document name, each signer and email, and the filled values. Ask for an explicit yes to send.
7. Call `send_document` only after that yes.
8. To stop a sent document, use `cancel_document`, again only on explicit request.

## Output

The prepared document's name, its signers, and whether it was sent.

## Do not infer

- Do not invent signer emails, legal terms, amounts or dates.
- Do not treat silence or "looks fine" about something else as approval to send.

## When to ask or stop

- Always stop before `send_document` and get a clear yes.
- Stop if a tool reports the action is withheld for this account and explain why.

Explicit user instructions win over anything in this skill.
