---
name: codecanon
description: Use when writing, modifying, reviewing, refactoring, debugging, or generating production code in any repository or application.
---

# CodeCanon

## Prime Directive

Implement the **smallest correct, secure, fast, maintainable change** that fully satisfies the request.

Security and correctness outrank brevity and performance. Never claim code is "100% secure"; absolute security cannot be guaranteed. Instead, use secure-by-default design, verify relevant attack surfaces, and report unresolved risk.

## Before Writing Code

1. Read applicable repository instructions and only the context needed for the task: relevant files, callers/callees, tests, schemas, permissions, configuration, and architecture.
2. Search before creating. Understand existing helpers, services, validators, policies, types, components, queries, and conventions.
3. Discover and load relevant installed skills when useful, including Superpowers, framework, database, testing, security, or infrastructure skills. Do not load unrelated material.
4. Prefer repository conventions over generic patterns.
5. Identify affected trust boundaries, permissions, persistence, public APIs, and hot paths.

Do not read or rewrite the entire repository by default.

## Minimal Code Law

Every added line must earn its place.

Prefer:

`reuse existing code > extend existing abstraction > extract shared helper > create new abstraction`

Also prefer:

`standard/platform capability > existing dependency > new dependency`

Never:

- duplicate existing logic;
- copy-paste behavior that should be shared;
- add speculative abstractions, wrappers, factories, options, fallbacks, or compatibility layers;
- add dependencies without a concrete need;
- perform unrelated refactors;
- add dead code, placeholders, unused exports, commented-out code, or "future-proofing";
- create files merely to make the implementation appear complete.

Use DRY, KISS, and YAGNI together. Do not create an abstraction more complex than the duplication it removes.

## Security Gate

Treat all external, client, network, file, database, queue, tool, model, and retrieved content as untrusted unless proven otherwise.

For every relevant change, verify:

- **AuthN/AuthZ:** enforce server-side; deny by default; least privilege; check permission on the actual resource/action; protect tenant/workspace/org/project ownership boundaries; prevent IDOR/BOLA.
- **Validation:** validate type, shape, length, range, enum, format, semantic constraints, upload limits, and dangerous/unknown fields at the trusted boundary.
- **Injection:** prevent SQL/NoSQL, command/shell, path traversal, template, LDAP/XML/XPath, CRLF/header, XSS/HTML, code/eval, prototype pollution, unsafe deserialization, and prompt/indirect-prompt injection where applicable. Use parameterized/safe APIs and context-aware encoding.
- **Web/API:** consider CSRF, CORS/origin policy, SSRF, open redirects, secure cookies/sessions, webhook signatures and replay, idempotency, safe error responses, and API compatibility.
- **Abuse/DoS:** use appropriate rate limits, quotas, pagination, body/file limits, bounded concurrency, timeouts, cancellation, retry limits/backoff, and recursion/depth limits.
- **Secrets/privacy:** never hard-code secrets; minimize returned data; redact logs; never expose tokens, credentials, raw auth headers, sensitive data, stack traces, or infrastructure details unnecessarily.
- **Crypto:** use established libraries and secure primitives; secure randomness; appropriate password hashing; never invent cryptography.
- **Integrity/concurrency:** check races, double submits, lost updates, TOCTOU, transactions, atomicity, idempotency, duplicate jobs/events, and database constraints.
- **Supply chain:** minimize dependencies; prefer maintained trusted packages; preserve lockfile integrity; do not execute untrusted scripts or generated code blindly.

Security controls must live in deterministic application logic, not only in UI checks or prompts.

### AI/Agent Systems

When LLMs, agents, retrieval, tools, or user documents are involved:

- treat model/retrieval/tool output as untrusted;
- separate instructions from data;
- never let prompt content override authorization or application policy;
- validate tool arguments before execution;
- expose only minimum required tools/data;
- prevent cross-user/cross-tenant context leakage;
- keep secrets out of prompts unless strictly required;
- require deterministic authorization for privileged/destructive actions;
- defend against direct and indirect prompt injection.

Use relevant current security guidance such as OWASP ASVS and NIST SSDF when deeper verification is warranted.

## Performance Gate

For affected hot paths, check:

- algorithmic complexity;
- N+1 queries and unnecessary database/network round trips;
- repeated parsing/serialization;
- unnecessary loops, allocations, or memory copies;
- unbounded concurrency;
- large in-memory materialization;
- blocking work on latency-sensitive paths;
- batching opportunities;
- indexes required by new query patterns.

Do not add caching unless it solves a real need and invalidation is correct. Performance must never bypass validation, authorization, consistency, or observability.

## Error Handling

- Fail closed for security-sensitive decisions.
- Handle expected failures explicitly.
- Do not swallow exceptions.
- Do not broadly catch errors unless they can be handled correctly.
- Do not retry unsafe non-idempotent operations without idempotency protection.
- Keep external errors safe and internal diagnostics useful.

## Tests and Verification

Use the repository's established testing approach and relevant installed testing/TDD skills.

For behavior changes, add the smallest meaningful tests. Include negative authorization and invalid/boundary cases for security-sensitive paths. Add regression tests for bugs. Prefer real behavior over excessive mocking.

Before completion, run applicable checks such as focused tests, affected suites, type checking, linting, formatting, build, and available security/static analysis.

Never claim a check passed unless it was actually run successfully.

## Comments

Do not write comments by default.

Comments are allowed only when:

- the user explicitly requests them; or
- an unavoidable non-obvious invariant, security reason, protocol constraint, workaround, or external requirement cannot be made clear through naming and structure.

Never add comments that merely narrate the code.

## Features and Breaking Changes

Follow the repository's existing changelog/docs/ADR convention first.

If none exists, use:

- `docs/changes/YYYY-MM-DD-feature-<slug>.md`
- `docs/changes/YYYY-MM-DD-breaking-<slug>.md`
- `docs/changes/YYYY-MM-DD-security-<slug>.md`

Breaking changes must always be documented.

Document material new behavior when developers, users, operators, API consumers, configuration, schema, permissions, or migration steps are affected. Do not create change documents for trivial fixes or internal refactors.

Keep change docs minimal:

```markdown
# Change title

## Summary
What changed and why.

## Impact
Who or what is affected.

## Migration
Required steps, if any.

## Rollback
Only when non-trivial.
```

## Compatibility

Before changing public APIs, schemas, persistent data, events, permissions, configuration, or serialized formats:

- search for consumers;
- preserve compatibility when reasonable;
- migrate persistent data safely;
- prefer staged/non-destructive migrations;
- document intentional breaking changes.

## Final Review

Before finishing, answer internally:

- Is this the smallest complete solution?
- Did I reuse existing code first?
- Is any new logic duplicated or removable?
- Are permissions enforced at the correct boundary?
- Is untrusted input validated?
- Are relevant injection, tenant-isolation, abuse, secret, race, and integrity risks handled?
- Is the affected path efficient?
- Are tests proportionate and meaningful?
- Did I actually verify the result?
- Did I avoid unnecessary comments, files, dependencies, and abstractions?
- Are material features or breaking changes documented?

If a relevant answer is no, fix it before completion.

## Completion Report

Keep the final report concise:

- what changed;
- important security/performance decisions;
- verification performed;
- docs/migration impact.

Do not produce a long implementation narrative unless requested.
