---
name: sok-jobb
description: Search open jobs in Sweden with the Remotejobb connector. Use when the user is looking for a job, wants to see open positions, asks about jobs in a Swedish city, category or company, wants remote or hybrid work, or writes in Swedish about "lediga jobb", "söka jobb" or "jobba hemifrån".
---

# Search jobs on Remotejobb

Use the Remotejobb connector's tools: `search_jobs`, `get_job` and `list_search_filters`.

## 1. Understand the request

- Pick out role or keywords, city, category, employment type, remote or hybrid, where the user lives, minimum salary and how recent the jobs should be.
- Search right away when the request has enough to go on. Ask one short question only when it is too vague to search at all.
- Answer in the user's language. Use `language: "sv"` for Swedish-speaking users so labels come back in Swedish.

## 2. Map the request to filters

- `category` and `city` take slugs. If you are unsure of a slug, call `list_search_filters` first instead of guessing.
- `work_mode`: `remote` for fully remote, `hybrid` for partly on site. Leave it out when the user doesn't care.
- `remote_scope` is where the applicant may live. It also matches more open scopes, so `sweden` includes jobs open to all of Europe or worldwide.
- `min_monthly_salary_sek` only matches jobs that state a salary in SEK. Tell the user that jobs without a stated salary are excluded.
- `posted_within_days` for "this week" (7) or "today" (1).
- Put the role in `query` with short keywords (for example `utvecklare`, `kundtjänst`, `python`). Every word must match, so keep it to one or two words.

## 3. Show results

- List the jobs compactly: title, company, location or work mode, employment type, salary if stated, and the link to the listing.
- Say how many jobs matched in total, and offer the next page when `has_more` is true.
- If nothing matches, loosen one filter at a time (salary, date, city, then keywords), say which one you loosened, and search again.

## 4. Open a job

- Use `get_job` when the user wants details, requirements or the apply link.
- Summarize the description in the user's language and give `apply_url` as the way to apply.
- If `is_excerpt_only` is true, say that only an excerpt is available and link to the original listing.
- If `apply_method` is `email`, the apply link leads to the job page on Remotejobb.se, where the application details are.

## Limits

- The connector is read-only. You cannot apply, save jobs or contact employers on the user's behalf. Give the apply link instead.
- Listings change daily. Don't present a job as still open without checking it with `get_job` when the user asks again later.
