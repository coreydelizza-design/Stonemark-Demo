# Trade secret and information security policy

One page, because a policy nobody reads protects nothing. A trade secret is only
protected if the owner takes **reasonable measures** to keep it secret. This document is
both the instruction and the evidence that those measures exist.

## 1. What is secret

The method and everything that expresses it: the provenance ladder, the scoring model and
its caps, reconciliation rules, archetype-to-requirement mappings, compliance and
requirement packs, connector parsing, expert playbooks and checklists, the client and
prospect list, pricing, and all client infrastructure data.

**What is not secret:** what a client or a demo visitor sees on screen, the marketing
positioning, and the published reports a client owns.

## 2. Access

- Access is granted per person, by name, with a unique login. No shared accounts, ever.
- Least privilege: access to a repository, an engagement or a document only where the
  work requires it.
- Access is revoked the day an engagement ends, before the final invoice is paid, not
  after.
- Every access grant and revocation is dated in `CHAIN_OF_TITLE.md`.

## 3. Agreements first

Nobody sees method material without a signed confidentiality agreement and IP assignment
already in place. This includes partners, prospective contractors, carriers and vendors.

## 4. Marking

Mark method material, decks, exports and working documents: **"Confidential — Stonemark
Infrastructure Assurance LLC."** Unmarked material is harder to defend as a secret.

## 5. Deliver the finding, never the engine

A client receives the assessment, the reports and their own data. A client never receives
the scoring model, the requirement packs, the templates or the platform. Enterprise
contracts that claim "all work product" need a background-IP carve-out before signature.

## 6. Public disclosure

Do not describe how the method works in a blog post, a conference talk, a deck or a demo
before deciding the patent question. A patent publishes; a trade secret stays hidden, and
for something held behind the platform, secrecy is usually the stronger protection.
Show the "how" only under NDA.

## 7. Tools

- Credentials live in the password manager and in Vercel or Supabase environment
  variables. Never in the repo, a chat, an email or a comment.
- Client data lives in the platform. Not in spreadsheets, personal drives, or an AI tool.
- No method material and no client data goes into any AI tool that is not covered by an
  agreement the owner has reviewed.
- Repositories stay private. The demo repository may become public only after the checks
  in `IP_INVENTORY.md` §"Before making a repo public" pass.

## 8. Offboarding

On the last day: revoke access, confirm local clones and downloads are deleted, collect
a signed acknowledgment of return or destruction, and record it in `CHAIN_OF_TITLE.md`.

## 9. Review

Review this policy once a year, and whenever the first contractor, the first client, or
the first public release arrives. Record the review date below.

| Reviewed | By | Note |
|---|---|---|
| [PENDING: date] | Owner | First adoption |

© 2026 Stonemark Infrastructure Assurance LLC. Confidential and proprietary.
