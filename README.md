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

Clone the repository:

```bash
git clone https://github.com/Quavon-dev/CodeCanon-skill.git
```

Then place `SKILL.md` in the skill directory used by your coding agent.

Common locations include:

```text
~/.claude/skills/codecanon/SKILL.md
~/.agents/skills/codecanon/SKILL.md
```

You can also copy the skill into a repository-specific skill location when your agent supports project-level skills.

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
