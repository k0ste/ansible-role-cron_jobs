# cron_jobs

Role for deploy cron jobs.

## Requirements

* Ansible 3.0.0+;

## Example configuration

```yaml
---
cron_jobs:
# Enable crond service or not
- enable: 'false'
# Restart cron service. This is not necessary if kernel have inotify support
  restart: 'false'
# Install cron daemon package or not
  install_package: 'false'
  settings:
# Set env for bob jobs
    MAILTO:
      file: 'bob'
      user: 'bob'
      job: 'bob@allsafe.com'
      env: 'true'
# Define 'foo' job for bob
    bob_cron:
      file: 'bob'
      user: 'bob'
      minute: '01'
      hour: '01'
      day: '*'
      weekday: '*'
      month: '*'
      job: 'foo'
      state: 'present'
# Define alice's 'bar' job
    alice_cron:
      file: 'alice'
      user: 'root'
      minute: '03'
      hour: '04'
      day: '*'
      weekday: '*'
      month: '*'
      job: 'bar'
      state: 'present'
```
