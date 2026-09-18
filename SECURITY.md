# Security and disclosure

## Reporting

Report a vulnerability, an exposed credential, or any real data found in this repository
to **[PENDING: security contact email]**. Include what you found, where, and how you
came across it. Please do not open a public issue for a suspected exposure.

There is no bug bounty. Stonemark will acknowledge a report and, where the finding is
valid and the reporter wishes it, credit the reporter.

Please do not test against `app.stonemark.ai` or any client system. The demo runs in your
own browser; test there.

## What counts as an incident here

- A credential, token, service key or connection string committed at any point in
  history, even if later removed.
- Real client, carrier, facility or personal data in code, fixtures, tests, screenshots,
  commit messages or issues.
- Method material: scoring weights, caps, thresholds, reconciliation rules, requirement
  packs, playbooks or carrier record templates.
- A real carrier, access provider or facility named in a demo finding.

## If one happens

1. Tell the owner the same day. A disclosure that is contained quickly usually stays a
   trade secret; one that sits in public may not.
2. Rotate anything exposed. Treat a committed credential as public from the moment it was
   pushed, regardless of repository visibility.
3. Remove the content from history, not just from the current files.
4. Record it in `docs/ip/CHAIN_OF_TITLE.md` under incidents, with the date, what was
   exposed, for how long, and what was done. That record is evidence that reasonable
   measures were maintained.

## Scope of this repo

The demo holds no database connection, no credentials and no personal data. It is
therefore a low-value target and should stay that way: any change that gives it a
credential or a server-side secret is out of scope for this repository.
