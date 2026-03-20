
## Install LinkedIn MCP Server
```sh
uvx patchright install chromium
uvx linkedin-scraper-mcp --login
```

## LinkedIn MCP Server — How It Works
https://github.com/stickerdaniel/linkedin-mcp-server

### 1. The login step (`--login`)
Launches a Chromium browser so you can authenticate to LinkedIn manually. Once login is complete, the session (cookies/profile) is saved to `~/.linkedin-mcp/profile/` on your machine. Chromium is **not running in the background** after this — it only runs to capture the session.

### 2. What the Docker container does
The container runs a headless Chromium **inside Docker** (bundled within the image — it does NOT use your OS's Chromium). On each request, it launches that headless browser, loads your saved session from `~/.linkedin-mcp/profile/` (mounted via `-v`), and uses it to scrape LinkedIn.

> **Warning:** This tool uses browser automation to scrape LinkedIn, which may violate LinkedIn's Terms of Service. It is intended for personal, low-frequency use only. Stay within **~100 LinkedIn MCP calls per week** (e.g. 2 sessions × 10 calls max per run) to remain in personal-browsing territory. Exceeding this risks session expiry, temporary restrictions, or account suspension. Random delays between calls (already enforced in CLAUDE.md) reduce fingerprinting risk.

### 3. Define settings.json
There's an existing one, based on the documentation, here: `./.claude/settings.json`
This will effectively start a container with the MCP server whenever VSCode starts (and loads the current project.)

## Additionall suggested official tools
### plugin: superpowers
Add it from "Manage Plugins" -> "Superpowers"
Referenced by the official plugins marketplace: https://github.com/obra/superpowers
Teaches Claude brainstorming, subagent driven development with built in code review, systematic debugging, and red/green TDD. Additionally, it teaches Claude how to author and test new skills.

### skill: document-skill
Add `https://github.com/anthropics/skills`  "Manage Plugins" -> "Marketplaces", then search for "pdf"
