# Ansible Role: Backup Cisco Switch

[![Build Status](https://travis-ci.org/dsgnr/ansible-role-backup-cisco-switch.svg?branch=master)](https://travis-ci.org/dsgnr/ansible-role-backup-cisco-switch)

This saves the running config for Cisco devices to a backup location specified and posts to Slack.

## Requirements

- A Cisco Switch configured within your Ansible hosts
- A Slack API key

## Role Variables

    backup_dir: /backups/{{ inventory_hostname }}
    slack_channel: "{{ slack_api_key }}

## Example Playbook

    ---

    - hosts: cisco
    
      vars_files:
        - vault/cisco_pass.yml
        - vault/slack_api.yml
    
      vars:
        datetime: "{{lookup('pipe','date \"+%Y-%m-%d\"')}}"
        slack_channel: #channel_name
        slack_api_key: "{{ vault_slack_api_backup_key }}"
    
      roles:
        - cisco-backup

## License

GNUv3

## Author Information

This role was created by [Dan Hand](https://danielhand.io).
