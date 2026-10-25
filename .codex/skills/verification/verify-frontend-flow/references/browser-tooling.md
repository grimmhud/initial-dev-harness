# Browser Tooling

## Distinction

- Playwright MCP exposes browser tools through the Model Context Protocol.
- `agent-browser` is an independent Chrome/Chromium CLI over CDP.
- Installing the `agent-browser` skill installs instructions only, not the CLI or browser.
- Playwright MCP does not require `playwright` or `@playwright/test` in the project. Add `@playwright/test` only when the project itself versions Playwright tests/configuration or runs them in CI.

## Browser MCP preflight

Treat MCP as available only when browser tools are loaded in the session and real navigation can start. A configuration entry alone is not proof.

This harness declares Playwright MCP only in `.codex/agents/frontend_verifier.toml`, using headless Firefox. Before first use, confirm Node.js and `npx` belong to the environment running Codex:

```bash
command -v node
command -v npx
node -p 'process.platform'
npx -y @playwright/mcp@latest --version
```

On Linux/WSL, paths must resolve to Linux executables and the platform must be `linux`. A path under `/mnt/c/...` or a `UNC paths are not supported` warning indicates Windows Node and is unsuitable for MCP stdio inside WSL.

Install the configured browser:

```bash
npx -y -p @playwright/mcp playwright install firefox
```

This installs the browser without making Playwright an application dependency. If the project owns a Playwright suite, use its package manager and official commands instead. Missing system libraries may require, in an authorized environment:

```bash
npx -y -p @playwright/mcp playwright install --with-deps firefox
```

This may request administrative privileges and must never run silently.

Optional global Codex configuration:

```bash
codex mcp add playwright -- npx -y "@playwright/mcp@latest" --headless --browser firefox
```

```toml
[mcp_servers.playwright]
command = "npx"
args = ["-y", "@playwright/mcp@latest", "--headless", "--browser", "firefox"]
startup_timeout_sec = 120
```

Global configuration belongs to the user's environment, not this repository. Restart Codex and confirm tools loaded. Normal harness use keeps MCP scoped to `frontend_verifier`.

## agent-browser

Check the CLI and browser, then load instructions matching the installed version:

```bash
command -v agent-browser
agent-browser doctor --json
agent-browser skills get core --full
```

The repository already includes the versioned skill instructions. The official external skill installer does not install the CLI or browser:

```bash
npx skills add https://github.com/vercel-labs/agent-browser --skill agent-browser --yes
```

Recommended CLI installation:

```bash
npm install -g agent-browser
agent-browser install
```

On Linux, missing system libraries may require `agent-browser install --with-deps`. Add a local versioned dependency only when the technical foundation approves it.

## When unavailable

`frontend_verifier` must not install global tools or system dependencies without authorization. Return `blocked` with the attempted backend, observed error, applicable install/configuration command, any session-restart request, and the next verification step. Re-run preflight after bootstrap; never convert the blocker into `skipped`.

## Artifacts and screenshots

- `.playwright-mcp/` contains internal accessibility snapshots and console logs. It does not replace evidence screenshots and remains Git-ignored.
- Save screenshots under `tmp/<feature-slug>/<deliverable>/<test-name>/` as required by the main skill.
- `tmp/` is local and Git-ignored. The handoff records exact paths without turning ephemeral evidence into canonical documentation.
