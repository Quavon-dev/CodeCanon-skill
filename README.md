# CodeCanon

A universal engineering standard for AI coding agents to write secure, minimal, performant, and maintainable production code.

CodeCanon is a reusable coding skill designed to keep AI coding agents disciplined: understand the necessary context, reuse what already exists, write only the code that is needed, treat security as a first-class requirement, preserve performance, verify the result, and document material changes.

## Why CodeCanon

AI coding agents can produce working code while still creating unnecessary abstractions, duplicating existing logic, weakening authorization boundaries, missing injection risks, over-commenting, or expanding a small task into a large implementation.

CodeCanon defines a compact engineering standard intended to reduce those failure modes without forcing agents into a heavyweight process.

## Core principles

- Security and correctness before convenience.
- The smallest complete change wins.
- Reuse existing code before creating new abstractions.
- Validate every untrusted boundary.
- Enforce permissions server-side and at the actual resource boundary.
- Defend against injection, abuse, data leakage, race conditions, and cross-tenant access.
- Keep hot paths efficient and resource use bounded.
- Add only proportionate tests and verification.
- Avoid comments unless they explain something genuinely non-obvious.
- Document material features, migrations, security changes, and breaking changes.
- Never claim absolute security without evidence.

## Installation

### One command — recommended

Install CodeCanon globally for the agents you actually use. For Claude Code, Codex, and GitHub Copilot:

```bash
npx skills add Quavon-dev/CodeCanon-skill --skill codecanon -g -a claude-code -a codex -a github-copilot -y
```

Specifying the target agents explicitly prevents the CLI from attempting a global install for detected project-only agents such as PromptScript.

Install for only one agent:

```bash
npx skills add Quavon-dev/CodeCanon-skill --skill codecanon -g -a claude-code -y
npx skills add Quavon-dev/CodeCanon-skill --skill codecanon -g -a codex -y
npx skills add Quavon-dev/CodeCanon-skill --skill codecanon -g -a github-copilot -y
```

For an interactive install, where you choose the target agents yourself:

```bash
npx skills add Quavon-dev/CodeCanon-skill --skill codecanon -g
```

For a project-local installation, omit `-g` and select the desired agent:

```bash
npx skills add Quavon-dev/CodeCanon-skill --skill codecanon -a claude-code -y
```

Verify the global installation:

```bash
npx skills ls -g -a claude-code -a codex -a github-copilot
```

### Ask your AI coding agent to install it

Paste this prompt into a coding agent that can use the terminal:

```text
Install CodeCanon globally from https://github.com/Quavon-dev/CodeCanon-skill as an Agent Skill for the coding agents available in this environment.

Use the standard Agent Skills CLI. Install only the `codecanon` skill and explicitly target only agents that support global skill installation. Do not use an unrestricted global auto-install that includes project-only agents. If the CLI is unavailable, use the active coding agent's documented global skill directory instead. Do not execute untrusted remote shell scripts.

After installation, verify that SKILL.md exists in the installed skill directory, that its YAML frontmatter is valid, and that the active agent can discover the `codecanon` skill. Do not modify unrelated files. Tell me the exact installation path and verification result when finished.
```

### Manual installation

Clone the repository directly into your agent's supported skill directory.

Claude Code:

```bash
git clone --depth 1 https://github.com/Quavon-dev/CodeCanon-skill.git ~/.claude/skills/codecanon
```

Agents using the shared `.agents` skill location:

```bash
git clone --depth 1 https://github.com/Quavon-dev/CodeCanon-skill.git ~/.agents/skills/codecanon
```

If your agent uses a different native skill directory, follow that agent's documentation.

## Usage

CodeCanon is intended to be loaded whenever an agent writes, modifies, reviews, refactors, debugs, or generates production code.

The skill itself is the product. Start with [`SKILL.md`](./SKILL.md).

## Scope

CodeCanon is language- and framework-agnostic. It covers general engineering behavior including:

- authentication and authorization;
- tenant and ownership isolation;
- input validation;
- injection prevention;
- web and API security;
- rate limiting and resource exhaustion;
- secret and privacy handling;
- cryptography boundaries;
- concurrency and data integrity;
- dependency and supply-chain hygiene;
- AI and prompt-injection security;
- performance and query efficiency;
- error handling;
- testing and verification;
- documentation and breaking-change discipline.

CodeCanon does not replace framework-specific security guidance, project instructions, threat models, testing standards, or specialist skills. Agents should load those when relevant.

## Contributing

Focused improvements are welcome. Please read [`CONTRIBUTING.md`](./CONTRIBUTING.md) before opening a pull request.

Security issues should be reported according to [`SECURITY.md`](./SECURITY.md), not through a public issue.

## License

CodeCanon is available under the [MIT License](./LICENSE).

## Maintainer

**rgxdev**  
hello@d-aaron.dev