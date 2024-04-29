ECGALAXY php role
=================

This Ansible role installs PHP and extensions.

Supported PHP versions: 8.1, 8.2 and 8.3 (default).

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

* optional: ecgalaxy.bootstrap
* optional: ecgalaxy.common_packages
* optional: ecgalaxy.oracle_instantclient

On Amazon Linux 2 and Ubuntu, the `ecgalaxy.oracle_instantclient` role should be executed first
if `php_install_oci8_extension` is set to `true`.

Example Playbook
----------------

    - hosts: all
      roles:
        - ecgalaxy.bootstrap
        - ecgalaxy.common_packages
        - ecgalaxy.oracle_instantclient
        - ecgalaxy.php

One-liner
---------

To globally install the default PHP version:

    bash <(curl -s https://code.europa.eu/-/snippets/1/raw/main/ansible-role.sh) ecgalaxy.php

To globally install PHP 8.2:

    bash <(curl -s https://code.europa.eu/-/snippets/1/raw/main/ansible-role.sh) ecgalaxy.php --extra-vars '{"php_version":"8.2"}'

You may need to execute the `ecgalaxy.oracle_instantclient` first (Amazon Linux 2, Ubuntu):

    bash <(curl -s https://code.europa.eu/-/snippets/1/raw/main/ansible-role.sh) ecgalaxy.oracle_instantclient

See [ansible-role](https://code.europa.eu/-/snippets/1) for instructions.

Please verify the script integrity first.

License
-------

Copyright the European Union 2022.

Licensed under the EUPL-1.2 or later.

Author Information
------------------

ECGALAXY team.
