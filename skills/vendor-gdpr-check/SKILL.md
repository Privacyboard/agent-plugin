---
name: vendor-gdpr-check
description: Check the GDPR paperwork of the third-party tools a codebase uses (SDKs, APIs, hosting) before shipping them, with the Privacyboard vendor guide.
---

# Vendor GDPR check

Use this when code adds or changes a third-party service: an SDK in package.json, requirements.txt, go.mod or another
manifest, an API client, an analytics or error-tracking script, a hosting or email provider.

1. List the services the change brings in (package names map to vendors: `@sentry/*` is Sentry, `stripe` is Stripe).
2. For each one, call `search_vendors` then `get_vendor` on the `vendors` server. Report its data processing agreement
   link, the role it usually plays, where it stores data and whether it holds an active Data Privacy Framework
   certification when data goes to the United States.
3. Flag what the team must act on: a vendor with no public DPA (it has to be requested or accepted in the account),
   data stored outside the EEA without DPF (standard contractual clauses and a transfer impact assessment), a vendor
   missing from the company's subprocessor list.
4. If the `workspace` server is connected, check whether the vendor is already in the Privacyboard workspace and offer
   to add it; never add or change anything without the user's confirmation.

The facts come from each vendor's public pages, with the date they were checked. This is not legal advice.
