# Changelog

## v0.2.0

- Add `podman_admin_user`, defaulting to `ansible_user`; empty or root skips admin user tasks, which allows `connection: local` as root
- Fix admin user removal from podman group in restricted mode, which replaced all supplementary groups with podman
- Use `podman_admin_user` in sudoers rule instead of hardcoded `ansible`, validate with visudo
- Create home directory for podman user
- Add `podman_packages` and install rootless dependencies explicitly: uidmap, passt, slirp4netns, dbus-user-session, catatonit, aardvark-dns, nftables
- Add molecule scenario `local` for `connection: local` as root

## v0.1.0

- Initial release
