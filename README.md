logrotate Role
=========

Logrotate is installed by default on Ubuntu 16.04, and is set up to handle the log rotation needs of all installed packages.
This role will easily allow default configuration changes and individual log rotation file creation.

Role Variables
--------------
```
log_conf_location: /etc/logrotate.d
log_rotate: weekly
log_group: "su root syslog"
log_keep: 4
log_create: create
log_compress: compress
logs: []

# Sample log configuration
logs:
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