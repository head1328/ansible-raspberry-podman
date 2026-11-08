# Ansible Role: Raspberry - Podman

An Ansible role that manages [Podman](https://podman.io) on Raspberry Pi OS (Debian 13 / Trixie).

## Role Variables

Please see [defaults/main.yml](https://codeberg.org/head1328/ansible-raspberry-podman/src/branch/main/defaults/main.yml) for a complete list of variables that can be overridden.

## Dependencies

This role relies on the following dependencies:

- Roles: None
- Collections: [requirements.yml](https://codeberg.org/head1328/ansible-raspberry-podman/src/branch/main/requirements.yml)

## Installation

```bash
$ ansible-galaxy role install head1328.podman
```

## Example Playbook

```yaml
- hosts: all
  roles:
    - role: head1328.podman
      tags: podman
```

## Testing

This role uses [Molecule](https://molecule.readthedocs.io/) for testing with Podman.

### Prerequisites

- `podman` e.g. via homebrew
- `python3` e.g. via homebrew
- `ansible` `molecule` and `molecule-plugins[podman]`, e.g. `pip install molecule "molecule-plugins[podman]"`

### Test Scenarios

- **default**: Tests the role with `podman_restrict_user: true` (restricted mode)
- **unrestricted**: Tests the role with `podman_restrict_user: false` (unrestricted mode)
- **local**: Runs the role inside the instance as root with `connection: local` and without `ansible_user` (cloud-init)

### Running Tests Locally

```bash
# Run default scenario
make test

# Run all scenarios
make test-all

# Run unrestricted scenario only
make test-unrestricted

# Run local root scenario only
make test-local

# Development workflow
make converge  # Apply the role
make verify    # Run verification tests
make destroy   # Clean up test instances
make login     # Login to test instance
```

### CI/CD

This role uses [Woodpecker CI](https://woodpecker-ci.org/) for automated testing on Codeberg. Tests run automatically on push and pull requests.

## License

AGPL-3.0-or-later
