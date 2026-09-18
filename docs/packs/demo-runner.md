# Demo build-out — runner

Kept in the repo as `docs/packs/demo-runner.md`. It holds the blocks you paste
into Claude Code for `docs/packs/demo-buildout.md`. You don't need to edit
anything except the bracketed parts of Block B.

---

## Step 0 — put both files in the repo (you, in the browser, 2 minutes)

1. Download `demo-buildout.md` and `demo-runner.md`.
2. On github.com, open `coreydelizza-design/stonemark-demo`. Create the folder path
   `docs/packs/` as you upload, by typing it into the file-name box.
3. Click **Add file → Upload files**, drag both files in, and choose **Create a
   new branch** named `demo/docs-landing`. Click **Propose changes**, then
   **Create pull request**.
4. When the checks are green, merge the pull request.

Everything below reads the files from that folder.

---

## Block A — session preamble

Paste this once at the start of every new Claude Code session. It writes
nothing, and comes back with a short readiness check.

```
You are working in coreydelizza-design/stonemark-demo — the standalone demo repo. Read,
in this order, before doing anything: docs/packs/demo-buildout.md (all of it),
docs/packs/demo-runner.md (Block C), README.md, DEMO_DATA_NOTICE.md, CONTRIBUTING.md,
NOTICE.md. Use the real paths on main; if a path differs, say so.

Ground rules for every step:
- STANDALONE. Never import from or change coreydelizza-design/stonemark-platform or
  Stonemark_Website. No Supabase, no server code, no environment variable, no
  credential, no request to any other origin.
- BUILDLESS. The deployed page stays static files a browser loads directly: one HTML
  entry point plus ES modules. Tests may use tooling; the deployed artifact may not.
- One step per invocation, one branch, one PR. Auto-merge stays off. Do not open the
  next step's PR.
- Before starting a step, check whether an open PR or remote branch already exists for
  it. If one does, stop and tell me.
- Evidence discipline: label every claim in your report FACT, INFERENCE or UNVERIFIED.
  Every FACT carries file:line.
- Never weaken a test, edit a visual baseline to pass, or change a derived function or
  threshold to make the data look right. The data changes to meet the domain.
- No real client, carrier, facility or person names. The client is Acme Corp; carriers
  are invented. No real carrier in any finding.
- Findings come only from pack §3 as confirmed by the owner. Never add, strengthen or
  reword a finding, and never contrive a fact to make a state appear.
- No method material: no scoring weights, caps, thresholds, reconciliation rules,
  requirement packs, playbooks or carrier record templates.
- No figure typed into a screen. Every figure derives from the dataset.
- No monitoring vocabulary (monitoring, real-time, live status, last checked, uptime)
  and nothing implying a site survey or visit.
- Views compute nothing; the derived functions do.
- Every new or changed source file carries the header in docs/ip/COPYRIGHT_HEADERS.md.
  Every new dependency gets a row in THIRD_PARTY_NOTICES.md with an allowed licence.

STOP AND ASK rather than improvising when:
- a gate in pack §0 is not satisfied
- the pack contradicts main
- a step needs a decision pack §2 does not cover
- a test fails for a reason you did not introduce
- the work is growing past the step's stated scope
Stopping costs one message. Guessing costs a run.

Now reply with a readiness check of no more than five lines: files found (with paths),
gates G1–G7 status as far as you can tell without running a step, any open PR or branch
that collides, and anything that blocks D0. Then stop.
```

---

## Block B — step invocation

Paste once per step, after Block A comes back clean. Replace the brackets.

```
Run step [D0] from docs/packs/demo-buildout.md.

Scope is exactly what the pack says for that step and nothing adjacent. If you
find something else broken, record it as a finding — do not fix it in this PR.

Before you write anything:
- restate the step's acceptance criteria in your own words
- name every file you expect to touch and why
- confirm this step needs no migration and no Supabase access
- STOP and wait for my go-ahead

Then implement, run `npm run check` from apps/registry, paste its real output
(pass or fail, never summarised), and report in Block C format.
Branch: [none — D0 is read-only]
```

---

## Block C — report format

```
STEP: D_ — name
BRANCH / PR: name, link (or "none — read-only")
RESULT: done | stopped (reason) | blocked (reason)

WHAT CHANGED (plain language, max 5 lines)

EVIDENCE
- FACT: ... (file:line)
- INFERENCE: ...
- UNVERIFIED: ...

ACCEPTANCE (each criterion from the pack, ticked or not, with evidence)

GUARDRAILS (each D1 check: green | fixme→D_ | missing)

npm run check (real output, final 30 lines)

SCREENSHOTS / PREVIEW LINK (any visual change)

SIGNED-IN SURFACES (confirm no non-demo file, test or baseline changed; list
any file touched outside demo-mode code and why)

FINDINGS NOT FIXED (out of scope for this step, including anything outside
the demo)

NEEDS OWNER (decisions, approvals, anything blocked)
```

---

## Step order

Nothing runs before its predecessor is merged.

| Step | Branch | What it is | What you check before merging |
|---|---|---|---|
| D0 | none | Read-only survey of index.html, the hosting, the story, and the fidelity deltas against the platform's portal | Read the whole report. Item 4, the delta list, becomes D4's worklist. Bring it back to planning chat before D1. |
| — | docs PR | **You confirm or strike F1–F8 and A1–A4** in pack §3, and edit the guide copy in §6 | Nothing in D3 runs until this is merged. |
| D1 | `demo/d1-guardrails` | Automated checks running on every pull request | The workflow reports pass or fail on a PR; every guardrail is green or marked fixme with a later step named. |
| D2 | `demo/d2-structure` | Splits the one file into dataset, derived functions, views and guide copy — still no build step | Before/after screenshots are identical; the deployed preview still works with no build command. |
| D3 | `demo/d3-acme-dataset` | The Acme dataset and the story coverage test | Preview it: the board paper leads with the five-site serving-office finding, and the data centres show as separate. |
| D4 | `demo/d4-fidelity` | Fixes every delta against the platform's client screens; adds FIDELITY.md | Compare a demo site card and the dot matrix against the platform's own, side by side. |
| D5 | `demo/d5-guide` | Guide copy moved to one module and locked to pack §6 | Walk all eight stops; every banner and hover-over reads as §6 says. |
| D6 | `demo/d6-publish` | Footer, terms page, robots, favicon, link preview | Paste the URL into a message and see what the preview shows. |

Expect D0 to take one message. D1, D2 and D3 each take a session. D4 depends on how
long the delta list is. D5 and D6 are short.

Owner items, outside these steps: the demo.stonemark.ai hostname, the website's
Explore demo link, and retiring the old /demo route inside the platform repo.
