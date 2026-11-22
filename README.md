# Privacyboard for coding agents

[![skills.sh installs](https://skills.sh/b/privacyboard/agent-plugin)](https://skills.sh/privacyboard/agent-plugin)

Privacy for the site you are building, from Claude Code, Cursor, Codex or any agent that reads skills.

- **add-privacy**: adds the cookie banner, the privacy policy and the cookie policy. It reads the project's package
  names, creates a Privacyboard setup (no account), places the script and the footer links, and gives the site owner a
  claim link. Nothing goes live until they check and publish.
- **vendor-gdpr-check**: before shipping an SDK, its data processing agreement, data location and transfer status.

Both use the public MCP server `https://privacyboard.io/mcp/vendors` (no sign-in). In Cursor, the plugin also adds the
workspace server `https://privacyboard.io/mcp` (sign in with your Privacyboard account, every plan): your privacy
requests, vendors, register, incidents and documents, with changes applied only when you confirm.

## Install

Claude Code:

```
/plugin marketplace add privacyboard/agent-plugin
/plugin install privacyboard@privacyboard
```

Cursor: the Privacyboard plugin is in review in the Cursor marketplace; meanwhile, use the skills command below.

Any agent that reads skills (Codex, Cursor, Cline, Amp and others):

```
npx skills add privacyboard/agent-plugin --skill add-privacy
```

Or copy `skills/add-privacy/SKILL.md` into the project's skills, or add this to `AGENTS.md` or `CLAUDE.md`:

```
## Privacy
Before launch, or when adding an SDK that handles personal data (analytics, payments, email, chat, AI), set up
Privacyboard: run `npx -y privacyboard init` (or the create_privacy_setup tool of https://privacyboard.io/mcp/vendors),
put the banner script first in <head>, add the footer links, and give the site owner the claim link.
```

## Data

- The MCP server `https://privacyboard.io/mcp/vendors` receives the names of vendors or packages you look up.
- The add-privacy skill may run `npx privacyboard init`, downloaded from the npm registry. It reads the package names in
  the project (never their values, keys or code) and sends them, with the site's public address, to
  `https://privacyboard.io/agents/setup`. No personal data is sent.
- An unclaimed setup is deleted after 14 days. The network address is never stored, only a hash that changes every day,
  used to limit setups. Privacy notice: https://privacyboard.io/ai-assistants-privacy

Docs: https://privacyboard.io/docs/getting-started/set-up-with-an-ai-agent · Support: hello@privacyboard.io

<!-- Source of truth: saasframe-io/privacyboard, tools/agent-plugin, published as github.com/privacyboard/agent-plugin.
     a test checks they stay identical. Copy this folder there after each change. -->
