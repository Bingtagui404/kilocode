# Documentation Platform Tabs Plan

## Context

Kilo Code now ships three products:

1. **Classic Extension** (v5.x) â the current release VS Code extension (`../kilocode-legacy`)
2. **CLI** (v7.x+) â the new core, terminal-based (`packages/opencode/`)
3. **Pre-release Extension** (v7.x+) â VS Code extension built on the CLI core (`packages/kilo-vscode/`)

The CLI and pre-release extension share the same config files, tools, agents, and permission system. They differ only in VS Code-specific features (autocomplete, Agent Manager, code actions, etc.). For documentation purposes, they are grouped as **"New CLI & Extension"**.

## Infrastructure (Already Done on This Branch)

- `Platform` type: `"classic" | "next" | "all"` in `lib/types.ts`
- `NavLink.platform?` property for tagging nav items
- `PageVersionSwitcher` component â renders a banner on platform-exclusive pages
- `_app.tsx` reads `frontmatter.platform` and renders `PageVersionSwitcher`
- Existing `Tabs`/`Tab` Markdoc components with hash-based URL state
- Tab labels: `"Classic Extension"` / `"New CLI & Extension"`

## Pages Already Updated (This Branch)

### Pages with inline tabs (content differs between platforms)

1. `getting-started/settings/index.md`
2. `getting-started/settings/auto-approving-actions.md`
3. `automate/extending/shell-integration.md`
4. `automate/mcp/using-in-kilo-code.md` (merged former `using-in-cli.md`)
5. `code-with-ai/features/browser-use.md`
6. `code-with-ai/features/checkpoints.md`
7. `customize/context/context-condensing.md`
8. `customize/context/kilocodeignore.md`
9. `customize/custom-instructions.md`

### Pages marked platform-exclusive (frontmatter banner only)

- **Classic only:** `auto-launch.md`, `how-tools-work.md`, `tools/index.md`, all 15 individual tool pages, `fast-edits.md`, `speech-to-text.md`, `task-todo-list.md`, `codebase-indexing.md`, `large-projects.md`, `auto-cleanup.md`, `system-notifications.md`
- **New only:** `cli.md`, `custom-subagents.md`, `workflows.md`

### Nav links already tagged

- `automate.ts`, `code-with-ai.ts`, `customize.ts`, `getting-started.ts`, `tools.ts` â all updated with `platform` tags

### Deleted

- `automate/mcp/using-in-cli.md` â content merged into `using-in-kilo-code.md`

---

## Remaining Work

### Phase 1: High-Priority Pages (Getting Started flow)

These are the pages every new user hits first. They must have tabs.

| Page                                      | Treatment                 | Notes                                                                                                                                     |
| ----------------------------------------- | ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| `getting-started/installing.md`           | **Add tabs**              | Classic: VS Code marketplace install. New: `npm i -g @kilocode/cli` / `brew install`, plus pre-release extension install from marketplace |
| `getting-started/quickstart.md`           | **Add tabs**              | Classic: VS Code sidebar walkthrough. New: `kilo` TUI first task + extension sidebar quick start                                          |
| `getting-started/setup-authentication.md` | **Add tabs**              | Classic: VS Code settings UI API key entry. New: `kilo auth login`, config file, or extension Settings webview                            |
| `getting-started/byok.md`                 | **Add tabs**              | Classic: VS Code settings provider profiles. New: `provider` key in `kilo.jsonc`                                                          |
| `getting-started/index.md`                | **Light tabs or callout** | Universal intro, but should mention both platforms exist and link to the right quickstart                                                 |

### Phase 2: Core Feature Pages

| Page                                             | Treatment    | Notes                                                                                                                                                                                                                          |
| ------------------------------------------------ | ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `code-with-ai/agents/chat-interface.md`          | **Add tabs** | Classic: VS Code sidebar webview. New: TUI (terminal) or extension sidebar                                                                                                                                                     |
| `code-with-ai/agents/using-modes.md`             | **Add tabs** | Classic: "modes" with `.kilocodemodes`. New: "agents" with `.kilo/agents/*.md` and config. Different built-in set (classic has Architect/Review, new has Plan/Debug)                                                           |
| `code-with-ai/agents/context-mentions.md`        | **Add tabs** | Classic: @-mentions (@file, @url, @problems, @git-changes, @terminal). New: different context system (editor context passing, no @-mentions in TUI)                                                                            |
| `code-with-ai/agents/model-selection.md`         | **Add tabs** | Classic: VS Code settings dropdown. New: TUI model picker, config file `model` key                                                                                                                                             |
| `code-with-ai/agents/orchestrator-mode.md`       | **Add tabs** | Both have orchestrator but interface differs                                                                                                                                                                                   |
| `code-with-ai/features/autocomplete/index.md`    | **Add tabs** | Classic: ghost text service. New: FIM-based with Codestral, extension-only feature                                                                                                                                             |
| `code-with-ai/features/git-commit-generation.md` | **Add tabs** | Both have it. Classic: SCM button. New: SCM button (extension) or not available in CLI                                                                                                                                         |
| `code-with-ai/features/code-actions.md`          | **Add tabs** | Classic: Explain/Fix/Improve context menu. New: Same commands in extension, not available in CLI                                                                                                                               |
| `code-with-ai/platforms/vscode.md`               | **Add tabs** | Should cover both extensions â classic features vs new extension features                                                                                                                                                      |
| `customize/custom-modes.md`                      | **Add tabs** | Classic: `.kilocodemodes` YAML, settings UI. New: `.kilo/agents/*.md` markdown files with YAML frontmatter, config `agent` key                                                                                                 |
| `customize/custom-rules.md`                      | **Add tabs** | Classic: `.kilocode/rules/` directory. New: `instructions` config key, `.kilo/` directory                                                                                                                                      |
| `customize/agents-md.md`                         | **Add tabs** | Classic: `AGENTS.md` file. New: Same concept but also `.kilo/agents/`                                                                                                                                                          |
| `automate/agent-manager.md`                      | **Add tabs** | Both platforms have Agent Manager. Classic: process-based agent spawning, simpler UI. New: CLI-backed sessions, richer diff panel, multi-model comparison, apply workflow. Currently written for new only â needs Classic tab. |

### Phase 3: Secondary Pages

| Page                                                  | Treatment        | Notes                                                                                                                                                                                                               |
| ----------------------------------------------------- | ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `customize/skills.md`                                 | **Add tabs**     | Both platforms have skills. Classic: `.kilocode/skills/` + marketplace UI. New: `.kilo/skills/` + config `skills.paths`/`skills.urls` + remote skill URLs. Page currently written for new only â needs Classic tab. |
| `code-with-ai/agents/auto-model.md`                   | **Review**       | Probably universal (both have auto-model)                                                                                                                                                                           |
| `code-with-ai/agents/free-and-budget-models.md`       | **Universal**    | No changes needed                                                                                                                                                                                                   |
| `code-with-ai/features/enhance-prompt.md`             | **Review**       | Check if new platform has this feature                                                                                                                                                                              |
| `code-with-ai/features/autocomplete/mistral-setup.md` | **Review**       | May need tabs since setup differs                                                                                                                                                                                   |
| `code-with-ai/app-builder.md`                         | **Mark classic** | App Builder is classic-only                                                                                                                                                                                         |
| `code-with-ai/platforms/jetbrains.md`                 | **Mark classic** | JetBrains is classic-only                                                                                                                                                                                           |
| `code-with-ai/platforms/cloud-agent.md`               | **Review**       | Check if this applies to new platform                                                                                                                                                                               |
| `code-with-ai/platforms/mobile.md`                    | **Review**       | Check applicability                                                                                                                                                                                                 |
| `code-with-ai/platforms/slack.md`                     | **Review**       | Check applicability                                                                                                                                                                                                 |
| `customize/prompt-engineering.md`                     | **Universal**    | General guidance applies to both                                                                                                                                                                                    |
| `collaborate/sessions-sharing.md`                     | **Light tabs**   | Session concepts are similar, but CLI has `kilo export`/`kilo import` commands                                                                                                                                      |
| `getting-started/migrating.md`                        | **Universal**    | Migrating from Cursor/Windsurf applies to both                                                                                                                                                                      |
| `getting-started/using-kilo-for-free.md`              | **Universal**    | Kilo provider works the same way                                                                                                                                                                                    |
| `getting-started/adding-credits.md`                   | **Universal**    | Same billing system                                                                                                                                                                                                 |
| `getting-started/rate-limits-and-costs.md`            | **Universal**    | Same system                                                                                                                                                                                                         |
| `getting-started/troubleshooting/*.md`                | **Add tabs**     | Different troubleshooting steps per platform                                                                                                                                                                        |
| `getting-started/faq/*.md`                            | **Review each**  | Some FAQ answers differ by platform                                                                                                                                                                                 |

### Phase 4: AI Provider Pages

| Page                                 | Treatment                      | Notes                                                                                                                                                                                                                    |
| ------------------------------------ | ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `ai-providers/index.md`              | **Light tabs**                 | Overview needs to mention both config approaches                                                                                                                                                                         |
| Individual provider pages (35 pages) | **Add tabs to setup sections** | The "how to configure" section differs (VS Code settings UI vs `kilo.jsonc` provider config), but model info is universal. Use tabs only for the configuration/setup section of each page, keep model details universal. |

### Phase 5: Nav Enhancement (Optional)

Currently the SideNav does NOT render `platform` badges. Consider adding visual indicators:

- Small pill/badge next to platform-specific nav items (e.g., `[Classic]` or `[New]`)
- This helps users identify which pages apply to their setup without clicking through
- Implementation: Update `SideNav.tsx` to read `NavLink.platform` and render a badge

---

## Implementation Guidelines

### Tab Pattern

```markdown
{% tabs %}
{% tab label="Classic Extension" %}
Content for the v5.x release extension...
{% /tab %}
{% tab label="New CLI & Extension" %}
Content for the CLI and v7.x+ pre-release extension...
{% /tab %}
{% /tabs %}
```

### When to Use Tabs vs Platform Banner

- **Tabs**: When a page has content that applies to BOTH platforms but differs in details (config, UI, setup steps)
- **Platform banner** (`platform: classic` or `platform: next` frontmatter): When a page is entirely specific to one platform with no equivalent on the other
- **No annotation**: When content is universal (same for all platforms)

### Content Strategy for Tabs

- Keep shared/universal content OUTSIDE of tabs (e.g., conceptual explanations, "what is X")
- Put platform-specific content INSIDE tabs (e.g., setup steps, config examples, UI instructions)
- Within "New CLI & Extension" tabs, note extension-only features where relevant (e.g., "In the VS Code extension, you can also...")
- Keep tab content concise â avoid duplicating large blocks of identical text

### Source Material

- **Classic Extension content**: Existing docs pages + `../kilocode-legacy` codebase for verification
- **New CLI & Extension content**: `packages/opencode/` (CLI core) and `packages/kilo-vscode/` (extension) codebases
- Config schema: `packages/opencode/src/config/` for all available settings
- Tools: `packages/opencode/src/tool/` for tool definitions
- Agents: `packages/opencode/src/agent/` for agent/mode definitions

### Redirects

Any deleted pages must have redirects added to `previous-docs-redirects.js`. The `using-in-cli.md` deletion on this branch already has a redirect.

---

## Estimated Scope

| Phase   | Pages to Update | Effort                                                         |
| ------- | --------------- | -------------------------------------------------------------- |
| Phase 1 | 5 pages         | Medium â need to write new "New" tab content for each          |
| Phase 2 | 13 pages        | Large â significant content differences, need careful research |
| Phase 3 | ~15 pages       | Small-Medium â many are reviews/light changes                  |
| Phase 4 | ~36 pages       | Medium â repetitive pattern (add config tab to each provider)  |
| Phase 5 | 1 component     | Small â SideNav badge rendering                                |

**Recommended order**: Phase 1 â Phase 2 â Phase 5 â Phase 3 â Phase 4

Phase 1 is the most critical because it's the onboarding flow. Phase 2 covers core daily-use pages. Phase 5 (nav badges) is quick and improves discoverability for all tagged pages. Phases 3-4 are lower priority and more mechanical.
