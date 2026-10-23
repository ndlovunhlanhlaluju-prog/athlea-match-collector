# Athlea women's match collector

Small standalone experiment for reading RBTV's public women's football schedule from GitHub Actions. It contains only public-source collection code, not the Athlea application or private browser data.

The manual workflow starts an ordinary headed Chromium browser under Xvfb with the Athlea reader extension. It does not attach Playwright/CDP, use a personal Chrome profile, solve challenges, or disable the browser sandbox. Playwright supplies the browser executable only. A random per-run loopback key authenticates the extension locally; it is never included in artifacts.

Run **Actions → Test RBTV cloud collection → Run workflow**. A successful report requires a newly received, normalized fixture snapshot. An empty schedule can legitimately verify collection when the source confirms no matches. A green test does not independently verify video playback. Failure means cloud access remains unconfirmed, not that there are no matches.

Outputs: `probe.json` and, only when received, `stream-listings.json`. They include public fixture fields and links. The browser profile and local bridge key are excluded. The browser exits after three minutes at most; the entire job has a ten-minute timeout. No recurring schedule or paid runner is enabled.

After the first successful cloud run, schedule publishing separately. GitHub schedules are best-effort and may be delayed; use an independent score feed for live status. Do not label a fifteen-minute link snapshot as a fresh live score.

Local Linux test: `npm ci`, `npx playwright install --with-deps chromium`, then `xvfb-run -a npm run probe`.
