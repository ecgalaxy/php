ECGALAXY php role
=================

This Ansible role installs PHP and extensions.

Requirements
------------

None.

Role Variables
--------------

* `php_version`: the PHP version to install
* `php_enabled_apt_repos`: additional APT repositories to enable
* `php_enabled_yum_repos`: additional Yum repositories to enable
* `php_installed_packages`: the list of packages to install
* `php_installed_packages_extra`: additional packages to install
* `php_install_xdebug`: should Xdebug be installed or not
* `php_install_oci8_extension`: should the OCI8 extension be installed or not
* `php_oci8_extension_ini_path`: where to store the OCI8 ini file (Ubuntu)
* `php_oracle_instantclient_path`: Oracle Instant Client path

See `defaults` and `vars` for the default values.

Dependencies
------------

* ecgalaxy.bootstrap
* ecgalaxy.common_packages
* optional: ecgalaxy.oracle_instantclient

On Ubuntu, the `ecgalaxy.oracle_instantclient` role should be executed first if `php_install_oci8_extension` is set to `true`.

Example Playbook
----------------

    - hosts: all
      roles:
        - ecgalaxy.oracle_instantclient
        - ecgalaxy.php

License
-------

Copyright the European Union 2022.

Licensed under the EUPL-1.2 or later.

Author Information
------------------

ECGALAXY team.
