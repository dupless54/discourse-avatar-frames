# Validation commands

Run from a Discourse checkout with this repository installed under `plugins/discourse-avatar-frames`.

- One Ruby spec, only if relevant spec exists: `LOAD_PLUGINS=1 bin/rspec plugins/discourse-avatar-frames/spec/path/to/example_spec.rb`
- Plugin Ruby specs, only if specs exist: `bundle exec rake "plugin:spec[discourse-avatar-frames]"`
- Plugin QUnit, only if frontend tests exist: `CI=1 bundle exec rake "plugin:qunit[discourse-avatar-frames]"`

No `.github/workflows` directory was present on `main` when created (2026-08-27). Do not call CI GREEN unless an exact-head workflow/check actually exists and ran.

For eligibility/config changes, validate allowed, denied, and unknown-frame paths where tests exist; otherwise use focused source/static validation and report NOT RUN for unavailable runtime checks.
