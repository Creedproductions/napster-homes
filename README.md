# Napster Homes Logbook

Private shared calendar and money tracker for the Napster Homes Airbnb.
Hosted on GitHub Pages; live data sync via Firebase Firestore
(project `webaura-ba777`, collections prefixed `nh_`).

**Live site:** https://creedproductions.github.io/napster-homes/

## Access

The page is public, but the data is not: opening the logbook requires
Google sign-in, and Firestore security rules only admit
the owner account plus the Google emails the owner lists in
Settings → "Allowed Google emails" (stored in `nh_meta/allowlist`).

## Where things live

- `index.html` — the whole app (calendar, day editor, weekly/monthly totals).
- Firestore rules are managed in the `webauraapp` repo (`firestore.rules`,
  the `nh_*` section) and deployed from there.

## Data model

| Collection / doc      | Contents                                              |
| --------------------- | ----------------------------------------------------- |
| `nh_days/{YYYY-MM-DD}`| check-in/out, guest staying, booking ahead, day note  |
| `nh_payments/{id}`    | money received (amount, kind, received by, note)      |
| `nh_expenses/{id}`    | money spent (item, amount, momo charge, number sent to, paid by) |
| `nh_meta/settings`    | currency label, team member names                     |
| `nh_meta/allowlist`   | Google emails allowed in (owner-editable only)        |
