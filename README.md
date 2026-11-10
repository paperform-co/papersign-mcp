# Papersign MCP: skills for AI assistants

Get documents signed from your AI assistant. Pick a template, say who signs and what to fill in, and it sends the document for signature once you confirm. Ask who still needs to sign, or cancel a document that went out by mistake.

This repo connects your assistant to Papersign's MCP server and adds skills that show it how to do each job well.

## Install

**Skills (Claude Code, Cursor, Codex and other agents)**

```
npx skills add paperform-co/papersign-mcp
```

**MCP server:** add `https://api.paperform.app/mcp/papersign` as a remote MCP server in your client (a custom connector in ChatGPT or Claude, or `mcp.json` in Cursor). You sign in with your Papersign account the first time you use it.

It's also listed in the official MCP registry as `com.papersign/papersign`.

## Skills

| Skill | Use it to |
| --- | --- |
| `send-for-signature` | Prepare a document from a template and send it for signature |
| `track-signatures` | See who still needs to sign, and cancel a document on request |

Try:

- "Send our consulting agreement to Sam Lee (sam@example.com) to sign, starting 1 December."
- "Who still needs to sign this week's contracts?"

## How it works

The repo contains skills (Markdown instructions) and one remote MCP server, `https://api.paperform.app/mcp/papersign`. It runs no code on your computer.

When you connect, you sign in through Paperform's own sign-in page and choose what your assistant may do. It then works only in the account and spaces you approved. The tools check with you before anything is sent or cancelled.

Papersign is made by Paperform. If your account also has Paperform or Stepper, the same connection can use those too.

## Links

- About Papersign and MCP: https://papersign.com/mcp/
- Privacy policy: https://paperform.com/privacy/
- Terms: https://paperform.com/terms/

## Licence

MIT. See [LICENSE](LICENSE).
