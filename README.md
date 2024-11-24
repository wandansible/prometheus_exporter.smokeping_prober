Ansible role: Prometheus Exporter - Smokeping prober
====================================================

Install and configure Smokeping prober for Prometheus.

Requirements
------------

This role depends on the [base prometheus exporter role](https://github.com/wandansible/prometheus_exporter).

Role Variables
--------------

```
ENTRY POINT: *main* - Install and configure Smokeping prober for Prometheus

Options (= indicates it is required):

- smokeping_prober_arch_map  Mapping of the possible values of ansible_architecture to the
                              exporter package architectures
          default: null
          type: dict

- smokeping_prober_archive_urls  Override the list of exporter archive urls for different platforms
                                  and architectures
          default: null
          elements: str
          type: list

- smokeping_prober_bin_dir  Directory for the exporter executable
          default: null
          type: str

- smokeping_prober_binary  Filename for the exporter executable
          default: null
          type: str

- smokeping_prober_checksum_type  The exporter package checksum type
          default: null
          type: str

- smokeping_prober_checksum_url  Override the URL for the exporter checksum file
          default: null
          type: str

- smokeping_prober_checksums  Override exporter archive checksums file contents
          default: null
          type: str

- smokeping_prober_clean_src_dir  Remove old downloaded archive files from exporter src directory
          default: true
          type: bool

- smokeping_prober_config_file  Path for configuration file
          default: /etc/prometheus/exporters/smokeping_prober/config.yml
          type: str

- smokeping_prober_configure_caddy  If true, configure caddy to add a TLS endpoint for the exporter
          default: false
          type: bool

- smokeping_prober_description  Description for the exporter systemd service
          default: null
          type: str

- smokeping_prober_extra_flags  Extra flags to run exporter with
          default: null
          type: dict

- smokeping_prober_file_sd_dir  Directory, on scrape servers, for the file service discovery target
          default: /etc/prometheus/file_sd/smokeping_prober
          type: str

- smokeping_prober_flags  List of flags to run exporter with, as string or list
          default: null
          type: raw

- smokeping_prober_github_checksum_filename  Filename for the exporter package checksums file on github
          default: null
          type: str

- smokeping_prober_github_org  Name of organisation for exporter github repository
          default: SuperQ
          type: str

- smokeping_prober_github_repo  Name of exporter github repository
          default: null
          type: str

- smokeping_prober_group  Name of the exporter unix group
          default: null
          type: str

- smokeping_prober_groups  Unix groups added to exporter unix user
          default: null
          elements: str
          type: list

- smokeping_prober_handler  Name of the exporter handler to notify
          default: null
          type: str

- smokeping_prober_install  If true, install exporter
          default: true
          type: bool

- smokeping_prober_labels  Labels added to exporter metrics, overrides prometheus_labels
          default: null
          type: dict

- smokeping_prober_listen_addresses  List of addresses and ports to listen on
          default: ['localhost:9374']
          elements: str
          type: list

- smokeping_prober_log_level  Only log messages with the given severity or above
          choices: [debug, info, warn, error]
          default: warn
          type: str

- smokeping_prober_manage_user  If true, add exporter unix user and group
          default: true
          type: bool

- smokeping_prober_port  Listen port
          default: 9374
          type: int

- smokeping_prober_privileged  If true, run in privileged ICMP mode
          default: true
          type: bool

- smokeping_prober_register  If true, register the exporter with the scrape servers
          default: false
          type: bool

- smokeping_prober_scrape_servers  List of servers that scrape exporter metrics from the host,
                                    overrides
                                    prometheus_scrape_servers
          default: null
          elements: str
          type: list

- smokeping_prober_service  Name of the exporter systemd service
          default: null
          type: str

- smokeping_prober_service_unit_file  Contents of the systemd unit file for the exporter
          default: null
          type: str

- smokeping_prober_src_dir  Directory for the downloaded exporter src archive
          default: null
          type: str

- smokeping_prober_strip_components  Strip NUMBER leading components from file names on extraction
          default: 1
          type: int

- smokeping_prober_target  Scrape target hostname and port
          default: null
          type: str

- smokeping_prober_targets  List of prober configuration for smokeping prober to target
                             Each item may be given as a string or
                             dictionary
                             See here for details about the target
                             configuration format
                             https://github.com/SuperQ/smokeping_prober#configuration
          default: null
          elements: raw
          type: list

- smokeping_prober_user  Name of the exporter unix user
          default: null
          type: str

- smokeping_prober_version  Version to install (use "latest" for the latest version)
          default: latest
          type: str
```

Installation
------------

This role can either be installed manually with the ansible-galaxy CLI tool:

    ansible-galaxy install git+https://github.com/wandansible/prometheus_exporter,main,wandansible.prometheus_exporter
    ansible-galaxy install git+https://github.com/wandansible/prometheus_exporter.smokeping_prober,main,wandansible.prometheus_exporter.smokeping_prober
     
Or, by adding the following to `requirements.yml`:

    - name: wandansible.prometheus_exporter
      src: https://github.com/wandansible/prometheus_exporter
    - name: wandansible.prometheus_exporter.smokeping_prober
      src: https://github.com/wandansible/prometheus_exporter.smokeping_prober

Roles listed in `requirements.yml` can be installed with the following ansible-galaxy command:

    ansible-galaxy install -r requirements.yml

Example Playbook
----------------

    - hosts: all
      roles:
         - role: wandansible.prometheus_exporter.smokeping_prober
           become: true
