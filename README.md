<p align="center">
  <a href="https://buymeacoffee.com/erespawn">
    <img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me a Coffee" width="217" height="60">
  </a>
</p>

# Discourse Avatar Frames

A Discourse plugin that lets users select animated avatar frames while keeping frame eligibility server-authoritative.

## Features

- Public `avatar_frame` presentation field for profiles, user cards, and posts.
- Animated/CSS frame presentation through the plugin stylesheet.
- Server-side validation of selected frames against the configured frame catalog.
- Trust-level eligibility rules such as `tl1`, `tl2`, and higher levels.
- Group-based eligibility rules through configured Discourse group names.
- Invalid, unknown, or unauthorized frame selections are rejected when the user profile is saved.
- Site-level enable/disable control through `avatar_frames_enabled`.

## Security and Permission Model

The browser only presents frame choices. Eligibility is decided on the server from the configured frame rules, the user's trust level, and group memberships. Client-supplied permission state is never authoritative.

Only the selected frame identifier is intentionally exposed as public presentation data.

## Recent Repository Updates

Recent maintenance has modernized the repository's development workflow without changing the frame-selection contract:

- token-efficient context routing and repository maps;
- risk-based development/review guidance;
- CI-first delivery rules;
- Buy Me a Coffee funding metadata.

## Installation

Add the plugin to your Discourse container configuration:

```yaml
hooks:
  after_code:
    - exec:
        cd: $home/plugins
        cmd:
          - git clone https://github.com/dupless54/discourse-avatar-frames.git
```

Rebuild Discourse:

```bash
cd /var/discourse
./launcher rebuild app
```

Then enable `avatar_frames_enabled` and configure the available frames in the plugin site settings.

## Development Notes

This is a focused avatar-frame plugin. Changes to the frame configuration format should preserve existing installations, and permission validation should remain server-side.

For repository-specific development rules, see [`AGENTS.md`](AGENTS.md).

## Support

If you enjoy this plugin, you can support continued development through the Buy Me a Coffee banner at the top of this README.
