# Demo build-out — Acme Corp's client view, in the standalone demo repo

Owner request, 15 Sep 2026; revised 18 Sep 2026 for the standalone repo decision.
Kept in `stonemark-demo` as `docs/packs/demo-buildout.md`. Runner:
`docs/packs/demo-runner.md`.

Reference material, read-only, in `stonemark-platform`: `docs/GOALS.md` §4 and §6,
`docs/THREE_VIEWS.md` §C, the dot matrix spec, the completeness-tint spec, the roles
pack item R9, and `docs/packs/claims-register.md`.

## 0. Gates

- **G1.** D0 has run and the owner has read its report. No other step runs first.
- **G2. Standalone.** This repo builds and deploys on its own. It never imports from
  `stonemark-platform` or `Stonemark_Website`, and no step in this pack changes either
  of those repos. Where a platform document needs updating, the step says so and the
  owner does it separately.
- **G3. No back end.** No Supabase client, no server code, no environment variable, no
  credential, no network request to any other origin. The demo runs in the visitor's
  browser from static files.
- **G4. No real data.** `DEMO_DATA_NOTICE.md` governs every step: invented client,
  invented carriers, no real facility named, no real carrier in any finding.
- **G5. Story confirmed.** D3 runs only after the owner has confirmed or struck every
  finding in §3 and the decisions in §3, in a merged docs PR. The owner is the domain
  authority on how carrier diversity fails. The run never adds, strengthens or
  "improves" a finding.
- **G6. Fidelity.** Because this repo holds its own copy of the client screens, every
  screen must stay faithful to the platform's portal: same vocabulary, same colour
  language, same card anatomy, same honesty rules. Where the two differ, the platform
  is right and the demo is the defect. Drift is the standing risk of the standalone
  choice, and D4 plus `FIDELITY.md` are how it is held down.
- **G7. Buildless.** Keep the demo deployable as static files with no build step, so it
  can be edited and shipped without a terminal. Tests and checks may use tooling; the
  deployed artifact must not depend on it.

## 1. What this repo is, and what done means

`stonemark-demo` is **Acme Corp's portal for one complete, published sample
engagement** — what Acme's CIO would see after Stonemark delivered. It is the
destination of **Explore demo** on the website, and the surface the owner walks a
prospect through.

It is **not** the operator workspace. No Portfolio, no My work, no console, no intake,
no persona switcher, no sign-in.

The starting point on `main` is `index.html`, a single self-contained page carrying all
eight stops. It is real and deployed; these steps turn it into something maintainable
and tested rather than starting over.

Done means all six hold:

1. **The walk works.** Eight stops, each with real content: Status (with the dot
   matrix), Sites, a read-only site detail, Findings, executive register, board paper,
   Documents, Decisions.
2. **Everything computes from the seed.** Every figure on every screen is derived from
   one Acme dataset by shared functions. No figure is typed into a screen.
3. **Every finding is realistic** — an owner-confirmed pattern from §3.
4. **The screens match the product** (G6), recorded in `FIDELITY.md`.
5. **Nothing internal.** No operator control, no unpublished data, no method material:
   no scoring weights, caps, thresholds, reconciliation rules or requirement packs.
6. **The guardrails are automated** and run on every pull request.

## 2. Decisions (binding)

- **DD1. Names.** The client is **Acme Corp**. Carriers, access providers, colocation
  operators and facilities are invented, and checked against the platform's carrier
  registry and its historical brands. Real metros may be used; no real building,
  serving office or CLLI code is ever named.
- **DD2. One engagement: 22 sites, status published.** One publication dated 14 days
  before the page is loaded; next review about 11 months out.
- **DD3. Dates anchored to load time.** The dataset stores relative offsets and
  resolves them against the current date when the page runs, so the demo never looks
  stale. Tests inject the clock. No literal date strings are stored.
- **DD4. Standalone screens, faithful copies.** The demo has its own implementation of
  the client screens. It may not diverge in vocabulary, colour language, card anatomy,
  or honesty rules (G6). New product features do not have to appear here; when a client
  screen changes materially, the demo follows.
- **DD5. Money follows GOALS §6.** Acme's business inputs are declared ranges, labelled
  as declared. At least one site has no inputs and renders not computable. Benchmarks
  come only from the claims register; anything absent renders unconfirmed.
- **DD6. Guide layer.** Six tab hover-overs and a page banner on each of the eight
  stops, as built: step number, what you're looking at, what Stonemark did, look for,
  previous and next. Collapsible, dismissible for the session, collapsed by default on
  narrow screens, distinct from product surfaces, hidden in print. No coach marks,
  overlays, animations or auto-advancing tours. All copy comes from §6.
- **DD7. Static hosting.** Vercel, framework preset Other, no build command, no output
  directory. One HTML entry point plus ES modules, loaded directly by the browser.
- **DD8. Search engines.** `noindex` stays on until the owner decides otherwise, so the
  demo cannot outrank the marketing site or be found without the website's link.
- **DD9. Auto-merge off.** One step per invocation, one PR per step, the owner merges.

## 3. The Acme estate and findings — owner confirms before D3 (G5)

**Estate (22):** 2 data centres in different metros, 1 headquarters, 3 regional
offices, 4 manufacturing plants, 5 distribution centres, 6 branches, 1 contact centre.
Every site is dual-carrier, or carrier plus LTE, as ordered.

**Method.** Findings rest on carrier, access-provider and facility records, and on
Acme's configuration records. No finding rests on an onsite survey, a site visit or a
walkdown, and no copy implies one.

**Realism.** The two data centres are in different metros with separate access plant,
entrances, serving offices and POPs, and the dataset documents them as separate. A
clean result is part of a credible assessment: most of Acme's estate assesses clear or
honestly unresolved, not broken.

| # | Where | Pattern | Evidence state | Records |
|---|---|---|---|---|
| F1 | Headquarters | **Two carriers, one access provider.** The backup carrier's circuit is an off-net tail from the same local access provider as the primary. Both enter through one building-entrance conduit. | Confirmed | Produced |
| F2 | 3 distribution centres + 2 branches, one metro | **One serving office under five "diverse" sites.** Every access circuit at all five sites homes to the same local serving office, so loss of that office takes primary and backup at all five together. Lead finding in the board paper; the five sites carry the open-risk ring on the dot matrix. | Confirmed at 3, suspected at 2 | Partly produced |
| F3 | One manufacturing plant | **Lit and dark fiber in one cable** from the plant to the first splice point. | Confirmed | Produced |
| F4 | Secondary data centre | **Single facility entrance.** Both carriers enter the colocation facility through one entrance vault; the second entrance was never ordered. | Suspected | No response (facility operator) |
| F5 | Regional offices | **Carrier consolidation.** Primary and backup came from two carriers that have since combined; whether the backup's metro network has been folded in is unknown. | Unverified | No response |
| F6 | DC-to-DC replication | **Records withheld.** One carrier produced route records; the other declined under its contract. Diversity of the replication pair **cannot be established**. This does not assert that the paths converge; it is a ceiling until the agreement renews. | Insufficient evidence | Declined under contract |
| F7 | Branches | **LTE failover and HA configuration confirmed.** Scope is confirmation only: that the LTE backup is configured to take over and HA is in place. No claim about the cellular path's physical diversity, and the copy says so. | Confirmed | Acme's configuration records |
| F8 | Primary data centre, 3 plants, 2 distribution centres, contact centre | **Assessed clear.** Separate entrances, serving offices and POPs, documented in carrier records. | Assessed clear | Produced |

**Board paper:** the assertion, then F2, F1 and F6 in that order.

**Acme's recorded decisions.** A decision never changes an evidence grade.

| # | Answers | Decision | State |
|---|---|---|---|
| A1 | F1 | Order headquarters' backup from an access provider independent of the primary's, through a separate entrance. | Approved |
| A2 | F4 | Order the colocation facility's second entrance for the second carrier. | Open, awaiting a quote |
| A3 | F6 | Accept that the replication pair's diversity cannot be established until the agreement renews, and make route records a renewal requirement. | Risk accepted |
| A4 | F2 | Review access for the five sites that home to one serving office. | Open |

**States.** These facts produce four record dispositions: produced, partly produced, no
response, declined under contract. Not-asked does not appear, which is correct for a
finished engagement. The dot matrix follows the platform's spec: one dot per site,
coloured by evidence completeness, an assurance-band lens, and a ring for an open
critical or high risk. It has no pair or cell states. If a surface looks wrong without
some state that §3 doesn't produce, the run **stops and asks**; it never contrives a
fact to fill a state.

## 4. Steps

One step per invocation, one PR per step, auto-merge off. Before/after screenshots and
the Vercel preview link go in every PR that changes what is seen.

### D0 — Survey (read-only; no branch, no code, no PR)

Every line labelled **FACT**, **INFERENCE** or **UNVERIFIED**; every FACT with
`file:line`.

1. **This repo.** What is on `main`: `index.html`, the IP and governance files, the
   packs. Report the page's structure — where the dataset, the derived values, the
   views, the guide copy and the styles live inside the one file, with line ranges.
2. **Hosting.** Confirm how Vercel is building it: preset, build command, output
   directory, and whether the deployed URL serves `index.html` at the root.
3. **The story.** Mark each of F1–F8 and A1–A4 **present**, **partial** or **absent**
   in the current dataset. For F7, say how a configuration-confirmation item is
   represented.
4. **Fidelity deltas (G6).** Compare each screen with the platform's portal
   specifications named at the top of this pack, and list every difference: vocabulary,
   card anatomy, tint bands, dot encoding (hollow, hatch, ring), state pill values,
   chip wording, report structure. This list is the D4 worklist.
5. **Honesty sweep.** Any figure on screen not derived from the dataset; any use of
   "monitoring", "real-time", "live status", "last checked", "uptime", "site survey",
   "onsite survey", "site visit" or "walkdown"; any unknown presented as safe; any real
   carrier, facility or company name.
6. **Leaks.** Any method material, scoring weight, cap, threshold, requirement pack,
   operator control, credential or off-site request.
7. **Accessibility and mobile.** Keyboard reach and visible focus across the eight
   stops and the dot matrix; anything that breaks at 390px; contrast failures in both
   themes.
8. **Tooling.** What is available for checks in this repo today, and what a GitHub
   Actions workflow would need in order to run Playwright on a pull request.
9. **Contradictions.** Anywhere this pack disagrees with `main` or with a platform
   specification, quoting both.

**Watch for:** fixing anything.

### D1 — Guardrails and checks

Branch: `demo/d1-guardrails`. Tests and CI only; no change to what is on screen.

- Add a GitHub Actions workflow that runs on every pull request and on `main`. It must
  need no local terminal and no secret.
- Add Playwright tests covering the eight stops:
  - zero requests to any origin other than the page's own, and no Supabase client;
  - no console errors or warnings along the walk;
  - the vocabulary check from D0 item 5, over all demo-visible copy including guide
    copy;
  - keyboard reach and visible focus on the tabs, the dots, the cards and the guide;
  - renders at 390px with no horizontal page scroll;
  - the guide hides in print and can be dismissed and restored.
- Add a link check for every internal route, and a check that no file in the repo
  contains a credential pattern.
- Tests that fail against today's page are marked `test.fixme` naming the step that
  fixes them. No assertion is ever weakened.

**Acceptance:** the workflow runs on a pull request and reports pass or fail. Each
guardrail is green or `fixme` against a named later step.

### D2 — Structure without a build step

Branch: `demo/d2-structure`. Refactor only: the rendered result must be unchanged, and
the visual baselines prove it.

- Split `index.html` into ES modules the browser loads directly (G7):
  `src/data/acme.js` (the dataset), `src/domain/derive.js` (bands, assurance,
  completeness, legend counts, dot encoding), `src/views/*.js` (one per stop),
  `src/guide/copy.js` (all §6 copy), `styles.css` (the tokens and rules).
- **The views compute nothing.** Every band, count, percentage and legend figure comes
  from `src/domain/derive.js`, as the platform's architecture gate requires of its own
  components.
- Keep `index.html` as the only entry point, still deployable with no build command.
- Pin visual baselines for the eight stops in both themes, desktop and mobile.

**Acceptance:** identical rendering before and after, shown by screenshots; the
dataset, the derived functions and the guide copy each live in exactly one file.

**Watch for:** adding a bundler, a framework or a package the deployed page depends on.

### D3 — The Acme dataset

Branch: `demo/d3-acme-dataset`. Requires G5.

- Bring the dataset to §3 in full, as confirmed by the owner, in `src/data/acme.js`.
- Apply DD3 date anchoring.
- Add a **story coverage test** that, through `src/domain/derive.js`, asserts:
  - each finding F1–F8 and each decision A1–A4;
  - each record disposition §3 produces;
  - each completeness band and assurance band §3 produces;
  - the board paper's three findings are F2, F1, F6 in order;
  - the two data centres assess as separate at the access layer (DD6 realism);
  - F6 renders as *cannot be established*, never as converged;
  - F7 states its scope as failover and HA configuration only, with no
    physical-diversity claim for the cellular path;
  - every figure shown on Status equals the figure the legend and the cards show.
- Run the DD1 name check.

**Watch for:** changing a derived function or a threshold to make a finding appear;
typing a total into the dataset; wording a finding more strongly than §3 states it.

### D4 — Fidelity to the product

Branch: `demo/d4-fidelity`. Scope is exactly the D0 item 4 delta list.

- Fix each delta in the demo's direction of travel: the platform is right.
- Add `FIDELITY.md`: one row per screen, naming the platform specification it follows,
  the date last checked, and any accepted difference with the owner's reason.
- Add a test asserting the vocabulary that must match: band names, state pill values,
  disposition labels, chip wording, report section names.
- Record in `FIDELITY.md` the standing rule: check fidelity when a client-facing
  platform screen changes materially, and at minimum before any prospect walkthrough
  that follows a platform release.

**Acceptance:** every delta is fixed or recorded as an accepted difference with a
reason. No operator control exists anywhere in the demo.

**Watch for:** copying platform code into this repo without its header and without a
note in `FIDELITY.md`; importing from the platform repo (G2).

### D5 — Guide layer and copy discipline

Branch: `demo/d5-guide`.

- Move every guide sentence into `src/guide/copy.js`, matching §6 word for word, and
  assert that match in a test so the two cannot drift.
- Confirm the DD6 behaviours: hover and keyboard on the six tabs only, never on data;
  banner previous and next follow the §6 order; collapse and dismissal persist for the
  session; collapsed by default under 760px; hidden in print; visibly distinct from
  product surfaces.
- Every "look for" line carries its finding or decision key, and a test fails if a key
  no longer resolves in the dataset.

**Watch for:** a guide sentence written anywhere but §6; a "look for" line claiming
more than the finding it points at; guide styling that could be mistaken for a finding.

### D6 — Publish properly

Branch: `demo/d6-publish`.

- Footer on every stop: copyright, sample-data line, and a link to `DEMO_TERMS.md`
  content rendered as a page in the demo.
- Keep `noindex` (DD8). Add `robots.txt` to match.
- Confirm no analytics and no third-party script; if the owner wants visit counts
  later, that is a separate decision recorded in `DEMO_TERMS.md` first.
- Favicon and page title from the brand; Open Graph title and description for when the
  link is pasted into a message.
- `README.md` gets a short "how to run it locally" line: open `index.html` in a
  browser. That is the whole of it, and that is the point.

**Owner items, not build steps:** the `demo.stonemark.ai` hostname in Cloudflare and
Vercel; the website's **Explore demo** button pointing here; retiring the old `/demo`
route inside `stonemark-platform`, which is a change to that repo and outside this pack
(G2).

## 5. Out of scope

- Any change to `stonemark-platform` or `Stonemark_Website`.
- A database, an account, a server function, or any credential.
- The operator workspace, in any form.
- Route geometry or proximity analysis. F6 stays a records ceiling, not a spatial claim.
- Method material of any kind.
- Any real client, carrier, facility or person.

## 6. Guide copy — owner edits here

This is the only source of guide text. Keep each line to one sentence. The same
rules apply as for product copy:
- no likelihood;
- no monitoring words;
- nothing implying a site visit;
- unknown is never presented as safe.

### Tab hover-overs

| Tab | Hover-over |
|---|---|
| Status | Where Acme's assurance stands, and which sites share a point of failure. |
| Sites | Every Acme site, and how much of its claimed diversity is proven. |
| Findings | What the assessment found, graded by the evidence behind each finding. |
| Reports | The executive register and the board paper. |
| Documents | The authorizations Acme signed and the records each carrier returned. |
| Decisions | What Acme has approved, accepted or left open against each finding. |

### Page banners

**1 of 8 — Status**
- *What you're looking at:* Acme's assessment as published, with the dot matrix
  showing which sites would lose connectivity together if one shared element
  failed.
- *What Stonemark did:* Under Acme's authorization, collected carrier,
  access-provider and facility records, and checked every claimed diverse path
  against them.
- *Look for:* The five sites in one metro that all home to a single serving
  office. `[F2]`

**2 of 8 — Sites**
- *What you're looking at:* One card per site, showing how far that site's
  diversity is proven, from claimed to defensible.
- *What Stonemark did:* Graded each site by the strongest evidence behind it:
  carrier records, Acme's own declarations, or nothing yet.
- *Look for:* Headquarters, where two carriers turn out to rely on one access
  provider. `[F1]`

**3 of 8 — Site detail (the manufacturing plant in F3)**
- *What you're looking at:* The circuits, carriers and records behind one site's
  grade.
- *What Stonemark did:* Compared each carrier's layout records with the
  diversity Acme ordered.
- *Look for:* The dark-fiber backup running in the same cable as the lit
  primary. `[F3]`

**4 of 8 — Findings**
- *What you're looking at:* Every finding, graded confirmed, suspected,
  unverified, or cannot be established.
- *What Stonemark did:* Kept what records prove separate from what is claimed or
  unknown, and never presented an unknown as safe.
- *Look for:* The replication paths whose diversity cannot be established,
  because one carrier withheld route records. `[F6]`

**5 of 8 — Executive register**
- *What you're looking at:* Each exposure alongside what Acme says an outage of
  that element would cost.
- *What Stonemark did:* Used Acme's own declared cost ranges, marked as declared,
  and estimated no probability or likelihood.
- *Look for:* The five-site serving-office exposure, and where its cost figure
  comes from. `[F2]`

**6 of 8 — Board paper**
- *What you're looking at:* One assertion, three findings, the decisions the
  board is asked to take, and the cost to close.
- *What Stonemark did:* Stated exposure, not odds, and declined to present a
  return calculation.
- *Look for:* The decisions table, and the replication finding the board is
  asked to accept until renewal. `[F6]`

**7 of 8 — Documents**
- *What you're looking at:* The Letters of Authorization Acme signed, and what
  each carrier and facility operator produced, partly produced, withheld or
  left unanswered.
- *What Stonemark did:* Tracked every records request to its outcome, so each
  gap has a named reason.
- *Look for:* The colocation operator's records request that is still
  unanswered. `[F4]`

**8 of 8 — Decisions**
- *What you're looking at:* Acme's decisions against each finding: approved,
  risk accepted, or open.
- *What Stonemark did:* Recorded each decision against the finding it answers,
  without changing any evidence grade.
- *Look for:* The approved fix at headquarters and the still-open second entrance
  at the secondary data centre. `[A1]` `[A2]`
