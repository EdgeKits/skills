# EdgeKits skills

Free agent skills from [EdgeKits](https://edgekits.dev), packaged as Claude plugins.

| Plugin | What it does | Works in |
| --- | --- | --- |
| [`repoaccess`](plugins/repoaccess/) | Sell access to a private GitHub repo with Stripe: gets you to the setup wizard of RepoAccess core, a free, self-hosted Cloudflare Worker. | Claude Code, Cowork, any agent that reads `SKILL.md` |
| [`telegram-bot-security-audit`](plugins/telegram-bot-security-audit/) | Security audit for Telegram bot code: webhook and Mini App authenticity, chat identity, Stars payments, token leaks. The platform-specific holes generic scanners miss. | Claude Code, Cowork, any agent that reads `SKILL.md` |
| [`project-journal`](plugins/project-journal/) | Persistent project memory: a small markdown journal loads at every session start, every session is captured when it ends, and decisions become ADRs. | Claude Code (its hooks are a Claude Code feature) |
| [`project-curator`](plugins/project-curator/) | A curator for projects built with a coding agent: verifies the agent's reports against the sources, argues options with you, and writes the relay prompts you hand to the agent. | Claude Cowork |
| [`astro-i18n`](https://github.com/EdgeKits/i18n/tree/main/plugins/astro-i18n) | Edge-native i18n on Cloudflare Workers, two skills: `astro-i18n` adopts `@edgekits/astro-i18n` in an Astro site (translations in Workers KV, a per-namespace edge cache, typed keys, localized forms, multilingual SEO); `tanstack-i18n` adopts `@edgekits/tanstack-i18n` in a TanStack Start app sharing the same translations. | Claude Code, Cowork, any agent that reads `SKILL.md` |

Each plugin installs on its own. Adding this repository as a marketplace installs nothing by itself.

## Install

**Claude Code.** Add the marketplace once, then install the plugins you want:

```
/plugin marketplace add EdgeKits/skills
/plugin install telegram-bot-security-audit@edgekits
/plugin install repoaccess@edgekits
/plugin install project-journal@edgekits
/plugin install astro-i18n@edgekits
```

Or run `/plugin`, open **Discover**, and pick from the list.

**Claude Cowork.** Customize > Plugins > Add marketplace, enter `EdgeKits/skills`, then add the plugins you
want from Discover. `project-curator` is made for Cowork.

**Any other agent**, with the [skills CLI](https://skills.sh):

```
npx skills add EdgeKits/skills --list
npx skills add EdgeKits/skills --skill telegram-bot-security-audit
# astro-i18n and tanstack-i18n live in the EdgeKits/i18n repository:
npx skills add EdgeKits/i18n --skill astro-i18n
npx skills add EdgeKits/i18n --skill tanstack-i18n
```

## Privacy

None of these plugins sends data anywhere. `repoaccess`, `telegram-bot-security-audit`, `project-curator` and
`astro-i18n` contain no code, hooks or MCP servers: they are instructions for your agent. `project-curator` writes only to
the project's `curator/` folder and to files you name as its own. `project-journal` runs two local hooks that
read Claude Code's session transcript and write a journal inside your project; nothing leaves your
machine. Each plugin's README has the details:
[RepoAccess](plugins/repoaccess/#privacy), [Telegram Bot Security Audit](plugins/telegram-bot-security-audit/#privacy),
[Project Journal](plugins/project-journal/#privacy), [Project Curator](plugins/project-curator/#privacy),
[Astro i18n](https://github.com/EdgeKits/i18n/tree/main/plugins/astro-i18n#privacy).

## License

MIT, see [LICENSE](LICENSE).
