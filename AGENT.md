# AGENT.md — hugo-air

This repository is a public open-source Hugo theme intended for reuse by multiple websites.

## Component model

- **Theme templates** (`layouts/_default`, `layouts/partials`): rendering structure and reusable view fragments.
- **Theme shortcodes** (`layouts/shortcodes`): content-level composition primitives.
- **Theme styling** (`assets/sass`): shared visual layer and style variables.
- **Theme examples** (`exampleSite/`): reference usage for consumers.

## Consumer contract

Theme consumers should customize behavior through:

1. Hugo configuration (`params`, menus, language settings)
2. Content/front matter/page bundles
3. Hugo-supported override mechanisms

Direct edits to theme core files are discouraged for consumers because they are harder to maintain across updates.

## Escalation and contribution

If a consumer need cannot be solved through the consumer contract:

1. Implement feature/fix in this repository.
2. Contribute via commit/PR (community contributions are welcome).
3. Consumers update to the new theme revision.

## Provider-agnostic agent contract

Any AI agent working in this repository should rely on capability-first instructions, not vendor-specific workflows.

Required capabilities:

- Read/search code and templates
- Make precise file edits
- Run shell commands for local checks/builds
- Explain behavior/contract changes clearly
- Support collaboration through standard Git/GitHub flows

## Provider mapping appendix (examples)

| Capability | Copilot CLI | Claude Code | Gemini CLI |
| --- | --- | --- | --- |
| Read/search files | `view`, `glob`, `rg` | Read/Glob/Grep tools | `ls`, `read_file`, `grep` equivalents |
| Edit files | `apply_patch` | Edit tool | edit/write tool |
| Run commands | `bash` | Bash tool | shell tool |
| Collaboration flow | `gh` CLI or platform flow | GitHub integration/tools | GitHub integration/tools |

## Repository policy

- This repo is public OSS.
- Maintainer can edit directly.
- External contributors may propose features/fixes via PRs.
- Changes should preserve broad theme flexibility for many downstream sites.
