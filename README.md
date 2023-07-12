# mariabackup

Ansible role for creating full and incremental backups of MariaDB and rotating backups.

## Role Variables

| Variable      | Default Value     | Description                                                                                                                                                      |
| ------------- | ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| scripts_dir   | /opt              | Where to store the scripts.                                                                                                                                      |
| backup_root   | /mnt/backup       | Where to store the MariaDB backups.                                                                                                                              |
| keep_backup   | 5                 | How many backups to keep.                                                                                                                                        |
| cron          | \*-\*-\* 18:00:00 | When to run the backup. Default value: every day at 18:00:00. [Format explained here](<https://silentlad.com/systemd-timers-oncalendar-(cron)-format-explained>) |
| extra_options |                   | Extra switches for the mariabackup command.                                                                                                                      |

## Example Playbook

```yaml
- hosts: mariadb
  roles:
    - role: davey2.mariabackup
      vars:
        extra_options: "--user=root --no-lock --binlog-info=OFF"
        keep_backup: 2
```
