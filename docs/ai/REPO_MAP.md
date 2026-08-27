# Repository map

Use this to choose paths before searching. Source code remains authoritative if the map becomes stale.

- `plugin.rb` — server-side custom-field eligibility/validation and plugin registration.
- `assets/javascripts/discourse/` — frame preferences/connectors/client presentation; read local `AGENTS.md`.
- `assets/` — bundled frontend assets.
- `public/` — large shipped frame media tree; read `public/AGENTS.md` and inspect exact assets only.
- `config/` — settings/locales/configuration, including frame eligibility config.
- `docs/` — AI state/workflow and stable docs; do not preload wholesale.

Fast read order: root `AGENTS.md` -> task packet -> nearest local `AGENTS.md` -> exact validation/symbol -> exact asset if needed. Load eligibility/config decisions only when that surface is touched.
