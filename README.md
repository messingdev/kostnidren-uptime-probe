# kostnidren-uptime-probe

External uptime probe for `registr.kostnidren.cz`. Hits the homepage every
5 min from GitHub's runners and posts to Telegram on failure (curl error,
HTTP 5xx, or response slower than 10 s).

The on-VPS monitoring stack (Trellis roles `monitor-base` + `netdata` in
the `wp_kostnidren` Bitbucket repo) catches application-level errors but
cannot self-report VPS death. This workflow closes that gap.

See `docs/monitoring/external-probe/SETUP.md` in `wp_kostnidren` for
full setup notes; this README is just the operational quick-reference.

## Required secrets

GitHub repo → Settings → Secrets and variables → Actions:

- `TELEGRAM_BOT_TOKEN` — same value as Trellis `vault_telegram_bot_token`
- `TELEGRAM_CHAT_ID` — same value as Trellis `vault_telegram_chat_id`
