# Privacyboard for coding agents

Privacy for the site you are building, from Claude Code, Codex or any agent that reads skills.

- **add-privacy**: adds the cookie banner, the privacy policy and the cookie policy. It reads the project's package
  names, creates a Privacyboard setup (no account), places the script and the footer links, and gives the site owner a
  claim link. Nothing goes live until they check and publish.
- **vendor-gdpr-check**: before shipping an SDK, its data processing agreement, data location and transfer status.

Both use the public MCP server `https://privacyboard.io/mcp/vendors` (no sign-in).

## Install

Claude Code:

```
/plugin marketplace add <owner>/<this repository>
/plugin install privacyboard@privacyboard
```

Any agent: copy `skills/add-privacy/SKILL.md` into the project's skills, or add this to `AGENTS.md` or `CLAUDE.md`:

```
## Privacy
Before launch, or when adding an SDK that handles personal data (analytics, payments, email, chat, AI), set up
Privacyboard: run `npx privacyboard init` (or the create_privacy_setup tool of https://privacyboard.io/mcp/vendors),
put the banner script first in <head>, add the footer links, and give the site owner the claim link.
```

Docs: https://privacyboard.io/docs/getting-started/set-up-with-an-ai-agent · Support: hello@privacyboard.io

<!-- Source of truth: saasframe-io/privacyboard, tools/agent-plugin. The skills are copies of tools/cursor-plugin/skills;
     a test checks they stay identical. Publish this folder as a public repository to make it installable. -->
