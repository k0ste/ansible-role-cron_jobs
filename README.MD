# cron_jobs

Role for deploy crond & cron jobs

## Requirements

* Ansible 3.0.0+

## Example configuration

```yaml
---
cron_jobs:
# Enable crond service or not
- enable: 'true'
# Restart cron service. This is not necessary if kernel have inotify support
  restart: 'true'
# Install cron daemon package or not
  install_package: 'true'
# Drop exists jobs (exclude distro-specific files) or not
  drop_exists: 'true'
# Setup cron daemon options. Only for RedHat & Archlinux, Debian uses own
# version of crond
  settings:
# Disables inotify support
    - inotify: 'false'
# This option allows you to specify a shell command to use for sending Cron mail
# output instead of using sendmail This command must accept a fully formatted
# mail message (with headers) on standard input and send it as a mail message
# to the recipients specified in the mail headers. Specifying the string 'off'
# will disable the sending of mail
      mail: 'off'
# Don't set PATH. PATH is instead inherited from the environment
      path: 'false'
# This option enables clustering support, as described below
      clustering: 'false'
# This option will direct Cron to send the job output to the system log using
# syslog. This is useful if your system does not have sendmail installed or if
# mail is disabled
      system_log: 'true'
  jobs:
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
