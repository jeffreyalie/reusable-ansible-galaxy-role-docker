# docker

Ansible role to install and configure Docker CE on Ubuntu systems using the official Docker APT repository.

## Requirements

None. Uses only `ansible.builtin` modules.

## Role Variables

| Variable | Default | Description |
|---|---|---|
| `docker_packages` | `[docker-ce, docker-ce-cli, containerd.io]` | Packages to install |
| `docker_state` | `present` | `present` to install, `absent` to remove |
| `docker_service_enabled` | `true` | Enable Docker on boot |
| `docker_service_state` | `started` | Service state after provisioning |
| `docker_repo_url` | `https://download.docker.com/linux/ubuntu` | Docker APT repo URL |
| `docker_gpg_url` | `https://download.docker.com/linux/ubuntu/gpg` | GPG key URL |
| `docker_gpg_dest` | `/etc/apt/keyrings/docker.gpg` | GPG key destination |
| `docker_arch` | `amd64` | CPU architecture for APT repo |
| `docker_channel` | `stable` | Docker release channel |

## Dependencies

None.

## Example Playbook

```yaml
- hosts: docker_vms
  become: true
  roles:
    - role: jeffrey.docker
```

## Overriding Variables

```yaml
- hosts: docker_vms
  become: true
  roles:
    - role: jeffrey.docker
      vars:
        docker_arch: arm64        # for ARM-based VMs
        docker_channel: stable
```

## License

MIT

## Author

jeffrey
