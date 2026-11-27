# Architecture overview

## Role of this repository

`Filament-uno/site` is the **public front door for feedback** on filament.uno. It contains
no code: its value is the GitHub Issues tracker (and, historically, GitHub Projects for the
roadmap, which the README mentions). The name "site" is historical; it collects reports for
every part of the product.

```
                users
                  │  report bugs / ideas
                  ▼
     ┌────────────────────────────┐
     │ Filament-uno/site (Issues) │◀── linked from filament.uno home + about pages
     └────────────────────────────┘
                  │  triage: fix lands in the owning repo,
                  │  PR says "Fixes Filament-uno/site#N"
   ┌──────────────┼────────────────────┬──────────────────────┐
   ▼              ▼                    ▼                      ▼
filament_uno     ios                android         swift_/android_openprinttag
(Symfony site    (iOS app)          (Android app)   (NFC tag libraries used by
 + app API)                                           the apps)
```

## Contents

- `README.md`: instructions for reporters (open an issue; roadmap under Projects).
- `.github/FUNDING.yml`: GitHub Sponsors link.
- `logo_small.svg`: product logo.
- `CLAUDE.md`, `docs/`: maintainer and agent documentation.

No build system, dependencies, CI workflows, tests or deployment exist. GitHub renders
everything.

## Issue landscape (as of 2026-11-27)

22 issues in total since October 2021, 13 open. Themes:

- **Website / inventory UX**: edit and delete for rolls and inventory (#8, #9), bulk or
  repeat add (#3, #20), compact inventory views (#19), favourite brands (#18),
  readable IDs on QR stickers (#16), manufacturer creation bug (#15).
- **Material data**: new filament types such as ASA (#17, #21).
- **API**: endpoint for "printed" filament (#4).
- **Apps**: iOS app request (#6), plus closed iOS and Android/NFC bugs (#10, #12, #13).
- **Site content**: pronoun use (#22).

Labelling is sparse (`bug`, `iOS` only) and there are no issue templates, so reports vary
in quality and rarely include platform or version information.

## Connections

- Inbound links: `filament_uno` home page (`templates/home/index.html.twig`) and the about
  page text (`feedback.explain` in `translations/messages+intl-icu.en.xlf`).
- The mobile apps do not link here.
- Related channels: Discord (the site uses two different invite links, `nGFZQsqNx3` and
  `kss49BPAxV`, worth unifying in `filament_uno`) and support@filament.uno.

## Possible improvements

1. Add issue forms (`.github/ISSUE_TEMPLATE/bug.yml`, `feature.yml`, `config.yml` with
   links to Discord and email) asking for component, platform, app version and steps.
2. Introduce component labels and triage the unlabelled backlog.
3. Fix README typos and say that app issues are welcome; optionally show the logo.
4. Add an in-app "Report an issue" link in the iOS and Android apps pointing here.
