# Ansible Role for Servarr 🎛️

![Version](https://img.shields.io/badge/version-1.0.0-blue.svg) ![License](https://img.shields.io/badge/license-MIT-green.svg) ![GitHub Actions](https://img.shields.io/badge/build-passing-brightgreen.svg)

Welcome to the **Ansible Role for Servarr**! This role simplifies the installation and management of Servarr applications, including Radarr, Sonarr, Lidarr, Prowlarr, Readarr, and Whisparr, on Linux systems. 

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Configuration](#configuration)
- [Supported Applications](#supported-applications)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)
- [Releases](#releases)

## Overview

The **Ansible Role for Servarr** provides a straightforward way to deploy and manage popular media server applications. It streamlines the process of setting up these applications on your Linux machine, allowing you to focus on enjoying your media.

## Features

- Easy installation of Servarr applications.
- Manage configurations through Ansible playbooks.
- Support for multiple Servarr applications.
- Designed for Linux environments.
- Community-driven updates and support.

## Requirements

Before you begin, ensure you have the following:

- Ansible 2.9 or higher.
- A Linux system (Debian, Ubuntu, CentOS, etc.).
- Basic knowledge of Ansible and YAML.

## Installation

To install this role, use the following command:

```bash
ansible-galaxy install CHAWCHA3.ansible-role-servarr
```

You can also clone the repository directly:

```bash
git clone https://github.com/CHAWCHA3/ansible-role-servarr.git
```

## Usage

To use this role in your playbook, include it as follows:

```yaml
- hosts: your_hosts
  roles:
    - CHAWCHA3.ansible-role-servarr
```

This will execute the role and install the specified Servarr applications.

## Configuration

You can customize the installation by providing variables in your playbook or inventory file. Here’s an example of how to set variables:

```yaml
vars:
  servarr_applications:
    - radarr
    - sonarr
    - lidarr
```

You can also specify additional configurations as needed. Refer to the role's defaults for more options.

## Supported Applications

This role supports the following Servarr applications:

- **Radarr**: A movie collection manager.
- **Sonarr**: A TV series manager.
- **Lidarr**: A music collection manager.
- **Prowlarr**: An indexer manager for all your apps.
- **Readarr**: A book collection manager.
- **Whisparr**: A private tracker manager.

Each application can be installed and configured through this role.

## Contributing

We welcome contributions! If you have suggestions or improvements, please fork the repository and submit a pull request. Make sure to follow the coding standards and include tests for new features.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contact

For questions or feedback, feel free to reach out via GitHub issues or email.

## Releases

You can find the latest releases [here](https://github.com/CHAWCHA3/ansible-role-servarr/releases). Download and execute the appropriate files to stay updated with the latest features and fixes.

---

Thank you for checking out the **Ansible Role for Servarr**! We hope it simplifies your media management tasks. Happy streaming! 🎉