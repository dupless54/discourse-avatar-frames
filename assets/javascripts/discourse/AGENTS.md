# Avatar Frames frontend

- Follow current Discourse/Glimmer connector conventions verified from source.
- UI may filter/display frame choices but server validation remains the entitlement authority.
- Handle missing/invalid selected frame values safely and without breaking profile/card/post rendering.
- Do not derive permission from client trust/group data when a server decision exists.
- Escape labels/config-derived display values; avoid arbitrary raw HTML/styles/remote URLs.
- Preserve mobile/light/dark behavior and use locale-backed visible strings.
