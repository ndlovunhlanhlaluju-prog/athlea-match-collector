# Athlea women's match collector

Reads RBTV's public women's football fixtures using a disposable cloud Chromium browser and the Athlea extension. RBTV redirects GitHub's browser to www.fctv33go.cfd; both observed football pages are explicitly allowed. No personal Chrome profile, authentication cookies or app source are included.

The workflow **Sync women's match links** has a 15-minute schedule and a manual Run workflow option. GitHub schedules are best-effort and may be delayed. The collector has a five-minute job timeout; its browser collection is bounded to three minutes. Only a fresh, successful, women-only snapshot can reach the publication job. The publication job alone has repository Contents write permission, using GitHub's temporary job token to update stream-listings.json on the data branch. No personal access token or paid runner is required.

Manual hosted runs verified collection and publication. A successful snapshot can legitimately contain zero fixtures when the source confirms an empty schedule. Collection does not independently verify video playback. The source browser has no debugger attachment, security bypass or personal browser data. Per-run loopback keys and temporary browser profiles are excluded from artifacts.

Outputs: probe.json plus stream-listings.json when received. The public data branch contains only the public collector source and normalized fixture feed. Athlea expires old links and keeps score freshness independent of the link schedule.
