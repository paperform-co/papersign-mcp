---
name: track-signatures
description: Check which Papersign documents are still waiting on signers, who hasn't signed, and what was completed, and cancel a document only on explicit request. Use when the user asks "who still needs to sign?", "has the contract been signed?", "what's outstanding?", "cancel that document".
---

# Track signatures

## Expected input

A document name, a signer, or a time frame ("this week", "everything outstanding"). If none is given, check everything still waiting.

## Steps

1. Call `whoami`. Tracking documents needs Papersign on the account. If it is unavailable, say so plainly and stop.
2. Find the documents with `search` (by name or signer) or `list` (type document).
3. Call `fetch` on each relevant document to read its status and each signer's progress.
4. Report per document: name, status, who has signed, who hasn't, and when it was sent.
5. If the user asks to cancel a document, show its name and signers and ask for an explicit yes. Call `cancel_document` only after that yes.

## Output

A short list of documents with their status and outstanding signers, plus anything cancelled.

## Do not infer

- Do not say a document is signed unless `fetch` shows it.
- Do not guess why a signer hasn't signed.

## When to ask or stop

- Always stop before `cancel_document` and get a clear yes.
- Stop if a tool reports the action is withheld for this account and explain why.

Explicit user instructions win over anything in this skill.
