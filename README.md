![Ansible Lint](https://github.com/johanneskastl/ansible-role-podman_credentials/workflows/Ansible%20Lint/badge.svg)

# podman_credentials

Configure credentials for podman (by creating the auth.json file in
~/.config/containers/).

This role puts the `auth.json` file into the home directory of the user that you
are actually using finally. Using `become` in your playbook will put this into
root's home directory.

## Requirements

It only makes sense to configure this on a Linux machine where you are using
Podman.

## Role Variables

There is only one variable named `podman_credentials`, which contains a list of
"dicts" as they are called in Ansible terms.

It looks like this:

```yaml
podman_credentials:
  - registry_url: registry.hogwarts.example.org
    # Do NOT EVER EVER put credentials in playbooks...
    # Ansible Vault exists, you know?
    registry_username: hpotter
    registry_password_or_token: dobby
```

This example shows how to configure only one credential, for the
`registry.hogwarts.example.org` registry. This is how the resulting `auth.json`
file would look like:

```json
{
    "auths": {
        "registry.hogwarts.example.org": {
            "auth": "aHBvdHRlcjpkb2JieQo="
        }
    }
}
```

You can of course add more than one credential. All of them will end up in the
`auth.json` file.

```
podman_credentials:
  - registry_url: registry.hogwarts.example.org
    # Do NOT EVER EVER put credentials in playbooks...
    # Ansible Vault exists, you know?
    registry_username: hpotter
    registry_password_or_token: dobby
  - registry_url: registry.burrow.example.org
    # Do NOT EVER EVER put credentials in playbooks...
    # Ansible Vault exists, you know?
    registry_username: rweasley
    registry_password_or_token: hermione
```

## Dependencies

None

## Example Playbook

```yaml
- hosts: servers
  roles:
    - role: 'johanneskastl.podman_credentials'
      vars:
        podman_credentials:
          - registry_url: registry.hogwarts.example.org
            # Do NOT EVER EVER put credentials in playbooks...
            # Ansible Vault exists, you know?
            registry_username: hpotter
            registry_password_or_token: dobby
```

## License

BSD-3-Clause

## Author Information

I am Johannes Kastl, reachable via git@johannes-kastl.de
