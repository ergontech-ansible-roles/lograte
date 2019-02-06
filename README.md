logrotate Role
=========

Logrotate is installed by default on Ubuntu 16.04, and is set up to handle the log rotation needs of all installed packages.
This role will easily allow default configuration changes and individual log rotation file creation.

Role Variables
--------------
```
logrotate_conf_location: /etc/logrotate.d
logrotate_rotate: weekly
logrotate_group: "su root syslog"
logrotate_keep: 4
logrotate_create: create
logrotate_compress: compress

# Sample log configuration
logrotate_files:
  - filename: application
    path: /var/www/magento/shared/var/log
    rotate_options:
      - monthly
  - filename: message-cleanup
    path: /var/log/messages
    rotate_options:
      - "rotate 5"
      - weekly
    post_rotate:
      - "/usr/bin/killall -HUP syslogd"
```


----------------

```
#   requirements.yml
#
#   Example
# - src: https://github.com/ergontech-ansible-roles/logrotate
#   version: master
#   name: logrotate
```

License
-------

[MIT](LICENSE)
