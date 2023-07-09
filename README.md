# mariabackup

Ansible role for creating full and incremental backups of MariaDB and rotating backups.

## Role Variables

| Variable           | Default Value     | Description                                                                                                                                                      |
| ------------------ | ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| scripts_dir        | /opt              | Where to store the scripts.                                                                                                                                      |
| backup_root        | /mnt/backup       | Where to store the MariaDB backups.                                                                                                                              |
| old_backup         | 1296000           | Delete old backups. The number is expressed in seconds. Default value: 15 day.                                                                                   |
| cron               | \*-\*-\* 18:00:00 | When to run the backup. Default value: every day at 18:00:00. [Format explained here](<https://silentlad.com/systemd-timers-oncalendar-(cron)-format-explained>) |
| weekly_full_backup | true              | Whether to perform a full backup weekly or monthly. If you have a large database, it is recommended to leave this option enabled.                                |

## Example Playbook

```yaml
- hosts: mariadb
  roles:
    - role: davey2.mariabackup
```
