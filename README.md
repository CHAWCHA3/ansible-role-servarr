tinyoverflow.servarr
=========

This Ansible role automates the installation, configuration, and management of Servarr applications (e.g., Radarr, Sonarr) on Linux systems. It handles tasks such as downloading the application, setting up systemd services, creating necessary directories, and configuring the application. It supports automatic upgrades on version changes and prevents downgrades, as those might lead to an unstable or broken state.

In addition, this role supports being executed multiple times on the same run, so you can use it to install multiple applications and multiple instances of the same application on a single server. See the examples below on how to do that.

Requirements
------------

This role is currently only compatible with Debian and has only been tested with Debian 12. Older versions might work, but are not officially supported by this role. To run this role, the `community.general` galaxy collection has to be installed. It also requires the `lxml` Python 3 package on the server. It will be automatically installed if required.

Role Variables
--------------

The following variables can be configured to customize the role's behavior:

### General Variables
- `servarr_install_dir`: The directory where the application will be installed. Default: `/opt`.
- `servarr_data_dir`: The directory where application data will be stored. Default: `/var/lib`.

### Instance Variables
| Variable                | Description                                                                                     | Default Value   |
|-------------------------|-------------------------------------------------------------------------------------------------|-----------------|
| `servarr_app`           | The name of the Servarr application to install. Supported values are: `lidarr`, `prowlarr`, `readarr`, `radarr`, `sonarr`, and `whisparr`. | N/A             |
| `servarr_version`           | The version of the Servarr application to install. Leave empty to install the latest version. | Empty; `4` for Sonarr             |
| `servarr_user`          | The system user that will own the application files. Will be created if it doesn't exist.       | `servarr`       |
| `servarr_group`         | The system group that will own the application files. Will be created if it doesn't exist.      | `servarr`       |
| `servarr_instance_name` | A unique name for the application instance (e.g., `default`, `4k`).                             | N/A             |
| `servarr_instance_port` | The HTTP port on which this instance will listen on.                                            | Default App Port             |


Dependencies
------------

To run this role successfully, you need to have the following dependencies installed:

- `community.general`: It's very likely that this is already installed, as it should come bundled with Ansible.

Example Playbook
----------------

You can use this role either in a standalone fashion, or even loop over it to install multiple instances of the same or different *arr-applications.

```yaml
# Installing a single instance
---
- hosts: servers
  roles:
    - role: tinyoverflow.servarr
      vars:
        servarr_app: radarr
        servarr_user: radarr
        servarr_group: media
        servarr_instance_name: default
        servarr_instance_port: 7878

# Installing multiple instances
---
- hosts: servers
  roles:
    - role: tinyoverflow.servarr
      vars:
        servarr_app: "{{ item.app }}"
        servarr_user: "{{ item.app }}"
        servarr_group: media
        servarr_instance_name: "{{ item.name }}"
        servarr_instance_port: "{{ item.port }}"
      with_items:
        - app: radarr
          name: 1080p
          port: 7878
        - app: radarr
          name: 2160p
          port: 7879
        - app: sonarr
          name: default
          port: 8989
```

License
-------

GNU GPLv3
