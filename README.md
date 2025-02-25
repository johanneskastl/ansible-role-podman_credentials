![Ansible Lint](https://github.com/johanneskastl/ansible-role-podman_credentials/workflows/Ansible%20Lint/badge.svg)

# podman_credentials

Configure credentials for podman (by creating the auth.json file in ~/.config/containers/)

## Requirements

None.

## Role Variables

None.

## Dependencies

None

## Example Playbook

```yaml
- hosts: servers
  roles:
    - role: 'johanneskastl.podman_credentials'
```

## License

BSD-3-Clause

## Author Information

I am Johannes Kastl, reachable via git@johannes-kastl.de
