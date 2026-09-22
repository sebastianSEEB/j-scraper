# j-scraper / Nord Jobbradar

Norway job discovery for business administration/BBA, supply chain, shipping, logistics and procurement.

## Live dashboard

https://nord-jobbradar.sebastianpropropro.chatgpt.site (owner-private)

## Automatic collection

An enabled **ChatGPT scheduled task** collects jobs twice daily, around **08:00 and 19:00 Europe/Oslo**, verifies public adverts, updates the hosted dashboard and synchronizes `dist/jobs.json` here. The task starts its new schedule on 22 September 2026 at approximately 19:00.

**This repository does not run a standalone scraper or GitHub Actions schedule.** The collector uses ChatGPT web search and accessible original listings. Cloning the repository alone does not install or run the scheduled task. The refresh button reloads the published snapshot; it does not launch a scrape.

Coverage: FINN, NAV, Jobbnorge, public LinkedIn listings and recruiter/employer career pages, subject to public accessibility. The dashboard reports actual coverage. No login bypass, automatic applications or employer outreach.

## Run locally

Requires Python 3 for the static server and Node.js for validation. No npm installation or API keys are needed.

```sh
python3 -m http.server 8000 --directory dist
```

Open http://localhost:8000.

```sh
node scripts/validate.mjs
node --check dist/app.js
```

## Files

- `dist/`: dashboard and current job snapshot
- `scripts/validate.mjs`: job-schema and duplicate validation
- `COLLECTOR.md`: search, verification, expiry and publication contract
- `.openai/hosting.json`: existing Sites project identity, not a credential

Do not infer qualifications from interests. Relevance labels are qualitative and explicitly flag extra requirements. Expired or closed adverts are hidden. Always confirm availability on the original advert.
