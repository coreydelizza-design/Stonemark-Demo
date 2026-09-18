# Third-party notices

Every third-party dependency, font, icon and asset, with its licence. Add the row in the
same pull request that adds the dependency. A row you cannot fill is a dependency that
does not get added.

## Rules

- **Allowed without approval:** MIT, BSD-2, BSD-3, ISC, Apache-2.0, Unlicense, CC0,
  SIL OFL 1.1 (fonts).
- **Owner approval required in writing:** MPL-2.0, and any licence not listed above.
- **Not allowed:** GPL, AGPL, LGPL, SSPL, "source available" or non-commercial licences,
  and anything with no licence at all. A file with no licence is not free to use; it is
  simply unlicensed.
- Attribution required by a licence (Apache-2.0 NOTICE text, OFL copyright lines) is
  reproduced in the "Required notices" section below, not summarised.

## Runtime dependencies

| Package or asset | Version | Licence | Where used | Notice required |
|---|---|---|---|---|
| [PENDING: complete at first commit of the demo code] | | | | |

## Fonts

| Font | Licence | Hosting | Notice |
|---|---|---|---|
| Inter | SIL Open Font License 1.1 | Self-hosted in the repo | Yes — reproduce the OFL copyright and licence text alongside the font files |
| Archivo | SIL Open Font License 1.1 | Self-hosted, report surfaces | Yes |
| Source Serif 4 | SIL Open Font License 1.1 | Self-hosted, report surfaces | Yes |

Self-hosting fonts is a licence obligation here as much as a performance choice: the OFL
requires the licence to travel with the font files.

## Required notices

[PENDING: paste the full OFL text once per font family, and any Apache-2.0 NOTICE
content, under headings named after each package.]

## Reviewing this file

Check it whenever a dependency is added, upgraded across a major version, or removed, and
once before any public release of the demo.
