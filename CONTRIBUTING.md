# Contributing

This repository is not open to public contribution. It is a private, proprietary
codebase operated by Stonemark Infrastructure Assurance LLC.

## Before access is granted

Every person, and every company acting through a person, signs all of the following
**before** repository access, tool access or any briefing on the method:

1. Independent Contractor Agreement (master).
2. Statement of Work for the specific engagement.
3. **IP and invention assignment**, in present tense: "hereby assigns". Without a signed
   assignment, work by an independent contractor is owned by the contractor by default,
   not by Stonemark. This is the single clause that must never be skipped.
4. Confidentiality agreement, surviving termination.
5. Non-circumvention and non-solicitation, reasonable in time and scope.

Short forms to adapt with counsel: `docs/ip/CONTRIBUTOR_IP_ASSIGNMENT.md`.

Access is granted per person with a unique login, at least privilege, and is revoked the
day the engagement ends. See `docs/ip/TRADE_SECRET_POLICY.md`.

## AI coding agents

Work produced by an AI coding agent on the owner's instruction is treated as the owner's
work product for chain-of-title purposes, and every such run is recorded in
`docs/ip/CHAIN_OF_TITLE.md`. An agent must not be given the method, the scoring model,
client data, or credentials.

## Rules that apply to every change

- No real client, carrier, facility or personal data, in code, fixtures, tests,
  screenshots, commit messages or issue text.
- No credentials or tokens, including in a comment or a test.
- No dependency added without recording its licence in `THIRD_PARTY_NOTICES.md`. No
  copyleft dependency (GPL, AGPL, LGPL, SSPL) without written owner approval.
- No code copied from a blog, a forum, another repository or a model's output presented
  as original, unless its licence permits it and the licence is recorded.
- Demo-only scope. Nothing in this repo changes what a signed-in Stonemark user sees.
- Every source file carries the header in `docs/ip/COPYRIGHT_HEADERS.md`.

## Pull requests

Use `.github/PULL_REQUEST_TEMPLATE.md` and complete its checklist honestly. An unticked
box is a question for the owner, never a thing to tick anyway.
