# Napster Homes Logbook

Private shared calendar and money tracker for the Napster Homes Airbnb.
Hosted on GitHub Pages; live data sync via Firebase Firestore
(project `webaura-ba777`, collections prefixed `nh_`).

**Live site:** https://creedproductions.github.io/napster-homes/

## Access

The page is public, but the data is not. Two ways in:

- **Admin** — Google sign-in with the admin account
  (`info.creedmotions@gmail.com`).
- **Team** — type a login name (e.g. `mukama`) on the front page. The name
  must be on the roster the admin manages in Settings → "Team login names"
  (stored in `nh_meta/roster`); it signs the device in anonymously and
  claims the name in `nh_members/{uid}`. Firestore rules re-check the
  roster on every read/write, so removing a name revokes access instantly.

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
| `nh_meta/roster`      | login names allowed in (admin-editable only)          |
| `nh_members/{uid}`    | a device's claimed login name                         |
