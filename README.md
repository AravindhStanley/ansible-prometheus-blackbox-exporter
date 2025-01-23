# Ansible Prometheus Blackbox exporter

This role aims to provide a seamless installation of Blackbox exporter on a baremetal or virtual machine based on systemd based linux operating systems.

## Role Variables

Default variable values:

```yaml
## You can change the variables as you see fit for your environment.
backbox_exporter_module_action: "install"
blackbox_machine_arch: "{{ go_arch_map[ansible_architecture] }}" ## Automatically inferred
blackbox_exporter_user: prometheus 
blackbox_remote_package_path: "/tmp"
blackbox_configuration_path: "/etc/prometheus-blackbox-exporter"
blackbox_exporter_version: 0.25.0
blackbox_exporter_download_url: "https://github.com/prometheus/blackbox_exporter/releases/download/v0.25.0/blackbox_exporter-{{ blackbox_exporter_version }}.linux-{{ blackbox_machine_arch }}.tar.gz"
```

*User configurable variable description:*

`backbox_exporter_module_action`: Action to be performed by the module. Possible values are `install` and `uninstall`. (Note: Uninstall will leave not remove the user that might be created as part of the deployment. This is intentional.). Defaults to `install`

`blackbox_exporter_user`: Blackbox service will run as this user. Defaults to `prometheus`

`blackbox_remote_package_path`: Path to download and extract the prometheus tar file from github release. Defaults to `/tmp`

`blackbox_exporter_version`: Desired version of prometheus blackbox exporter to be deploted. Please ensure the version matches the github release.

## License

GPL-2.0

## Playbook Example

```yaml
- name: Deploy Prometheus Blackbox Exporter
  hosts: localhost
  become: yes

  roles:
    - role: ansible-prometheus-blackbox-exporter
```

## Compatability

The role is tested against Ubuntu 20.04, Ubuntu 22.04, Rocky 8, 9. But it will likely work with all debian and redhat based systems.

## Author Information

Aravindh Murugesan.
Contact me at [aravindh.murugesan@protonmail.com]
