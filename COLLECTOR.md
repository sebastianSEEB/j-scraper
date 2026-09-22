# Nord Jobbradar collection contract
This is a private static dashboard updated by the ChatGPT twice-daily automation. It is NOT a standalone cron scraper or an exhaustive platform feed. The scheduled agent opens current Site source and publishes an updated JSON snapshot using Sites. No secrets are needed in the browser. The refresh button only reloads that snapshot.

## Profile
Norway, business administration/BBA, supply chain, shipping, logistics, procurement, operations, commercial analysis and junior finance. Prioritize graduate, student and junior roles. Degree completion, experience, availability and relocation willingness are unknown. Do not invent them. Include English and Norwegian searches. Never apply to jobs or contact people.

## Collection
Search FINN, NAV Arbeidsplassen, Jobbnorge, public LinkedIn, Academic Work and relevant employer career pages. Use public web search and original-page reads. Do not bypass authentication, robots restrictions or anti-bot measures. Mark inaccessible platforms honestly, do not call a search snippet fully verified. Check status and full date on original page; inactive/expired ads are closed, even when search results look recent. No bulk ad text, recruiter contact details or copyrighted descriptions; concise original summaries and source links only.

Read dist/jobs.json. Preserve stable IDs and firstSeen. Deduplicate URLs and normalized employer/title/location, retaining the most direct source. Keep successful verification timestamps separate from run time. On partial errors keep prior records with original verifiedAt and degraded source status. Remove ads explicitly withdrawn; close expired records and prune closed records after 30 days. Do not mark old records verified on failed checks. Write jobs.json atomically.

## Schema
Root: updatedAt (ISO run time), sources [{name,status,note}], jobs array. Each job: id, title, company, location, type, source, categories (Business/Supply chain/Shipping/Logistics/Procurement), fit (potential or stretch), status (open/closed/unverified), summary, requirements, url (canonical https original ad), deadline (YYYY-MM-DD or null for genuinely rolling/unknown, describe unknown in requirements), firstSeen (ISO date), verifiedAt (ISO instant). Potential is a subject/level assessment, never a probability. Mandatory masters, substantial experience or unverified qualification requirements are stretch. The UI hides closed and deadline-expired ads by default.

## Publication
Keep the UI and project identity unchanged. Run node scripts/validate.mjs and node --check dist/app.js. Use Sites hosting skill to push exact source, package static directory dist and publish privately. Confirm terminal success. If publishing fails, report clearly; do not claim the dashboard refreshed. Each-run user summary: newly found promising roles, imminent deadlines, limitations and dashboard link.

## GitHub mirror
After publishing, synchronize the validated dist/jobs.json to sebastianSEEB/j-scraper using GitHub fetch_file and update_file with the current blob SHA. Preserve unrelated user edits. Report sync failures separately from Site publication. The schedule is approximately 08:00 and 19:00 Europe/Oslo, managed by ChatGPT Automations, not GitHub Actions.
