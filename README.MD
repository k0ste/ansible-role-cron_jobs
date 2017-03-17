ansible-cron-jobs
====================

Role for deploy cron jobs.

Ansible versions
--------------------

Role is adapted for Ansible 2.0, should work on 1.9.


Example configuration
-------------------------

```yaml
---
cron_jobs_enable: 'true' # enable service
cron_jobs_restart: 'false' # restart cron service. This is not nessesary if kernel have inotify support

cron_jobs:
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
