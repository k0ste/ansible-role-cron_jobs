# ansible-cron-jobs

Role for deploy cron jobs.

## Requirements

* Ansible 2.4;

## Example configuration

```yaml
---
# Enable service.
cron_jobs_enable: 'false'
# Restart cron service. This is not nessesary if kernel have inotify support.
cron_jobs_restart: 'false'
# Install cron daemon package.
cron_jobs_install_package: 'false'

cron_jobs:
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
