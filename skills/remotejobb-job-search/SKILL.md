---
name: remotejobb-job-search
description: Search remote and hybrid jobs in Sweden with the Remotejobb tools (search_jobs, get_job, list_search_filters). Use when someone wants to find, compare or apply for remote, hybrid or work-from-home jobs in Sweden, or asks about jobs listed on Remotejobb.se.
---

# Job search with Remotejobb

Remotejobb.se lists remote and hybrid jobs that can be done from Sweden. The Remotejobb tools are read-only: they search and read listings, they cannot apply for jobs or change anything.

## The tools

- `list_search_filters`: the valid filter values. Returns categories and cities that currently have open jobs (with slugs and counts), plus the values for work mode, remote scope and employment type.
- `search_jobs`: searches open jobs. All filters are optional and combine with AND. Returns compact summaries, newest first, 10 per page by default (max 20), with `total` and `has_more`.
- `get_job`: one job in full by its `id` from `search_jobs`: description, salary, employment details, apply link and expiry.

## How to run a search

1. Work out what the person is looking for. Useful details are the role or keywords, fully remote or hybrid, where they live, salary expectations and employment type. Ask only for details that matter for the search and that you can't infer; a broad search is a fine first step.
2. Map their answers to filters:
   - `query`: keywords matched against title, company and description. Every word must match (as a prefix), so prefer one to three specific words, e.g. `react developer`, over long sentences. Swedish job titles often find more, e.g. `utvecklare` (developer), `ekonomi` (finance), `kundtjänst` (customer service).
   - `work_mode`: `remote` for fully remote, `hybrid` for partly on site.
   - `remote_scope`: where applicants may live. Each value also matches everything more open, so `eu` returns jobs open to the EU/EEA, Europe or worldwide. Someone living in Sweden can apply to every scope, so leave it out for them; use it for people living elsewhere.
   - `city`: a city slug from `list_search_filters`, mainly for hybrid jobs.
   - `category` and `company`: slugs from `list_search_filters` or from earlier results.
   - `min_monthly_salary_sek`: only matches jobs that state a salary in SEK, and many listings don't state one. Tell the person this when you use the filter, and offer to search without it.
   - `posted_within_days`: for "new" or "recent" jobs.
3. If a search returns nothing, loosen it: fewer keywords, a Swedish synonym, or one filter fewer. Say what you changed.
4. Use `get_job` for the jobs the person is interested in before describing requirements, salary or how to apply. Search summaries don't include the description.

## Presenting jobs

- Give each job's title, company, work mode and location or remote scope, salary when stated, and its link.
- Many listings are written in Swedish. Summarise or translate them in the person's language when helpful, and say that the original is in Swedish.
- Only state what the listing says. Don't guess salaries, requirements or benefits that aren't in it.
- Some listings are excerpts (`is_excerpt_only`). The full text is at the source, which `source.url` links to.
- For applying, use the `apply_url` that `get_job` returns. When `apply_method` is `email`, the link opens the job page on Remotejobb.se, where the apply button opens the person's email app; pass on the `apply_note`.
- Jobs with `is_expired: true` can no longer be applied for; say so.

## Labels in Swedish or English

The tools take an optional `language` (`en` or `sv`) for labels such as work mode and employment type. Use `sv` when talking with the person in Swedish, otherwise the default `en`. Job content is always returned in its original language.
