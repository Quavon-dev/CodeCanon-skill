# Contributing to CodeCanon

Thanks for contributing to CodeCanon.

CodeCanon is intentionally compact. Contributions should improve correctness, security, clarity, portability, or agent behavior without turning the skill into a large framework.

## Principles

Before proposing a change, ask whether it:

- addresses a real failure mode or ambiguity;
- applies broadly across coding agents or repositories;
- can be expressed more simply;
- duplicates an existing rule;
- adds unnecessary process or token overhead.

Prefer tightening an existing rule over adding a new section when both solve the same problem.

## Pull requests

Keep pull requests focused and small.

A good pull request should:

- explain the behavior or failure mode being addressed;
- modify only the necessary files;
- preserve the secure-by-default and minimal-code principles;
- avoid unrelated wording or formatting churn;
- update `CHANGELOG.md` when the change is user-visible or materially changes agent behavior.

## Skill changes

Changes to `SKILL.md` should remain language- and framework-agnostic unless a technology-specific reference is required to explain a universal rule.

Avoid absolute claims such as "100% secure" or "guaranteed safe." Security guidance should require verification rather than imply certainty.

The skill should remain concise enough to be loaded frequently without excessive context cost.

## Security-related contributions

Do not disclose exploitable security issues publicly before they are addressed. Follow `SECURITY.md` for private reporting.

## Style

- Use clear, direct English.
- Prefer normative language such as `must`, `never`, and `prefer` when the rule is intentional.
- Avoid filler, marketing language, and redundant examples.
- Keep examples short.
- Do not add comments or implementation code unless the repository later contains tooling that genuinely requires them.

## License

By contributing, you agree that your contributions are licensed under the repository's MIT License.
