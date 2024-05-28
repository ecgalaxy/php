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
* `php_remove_al2_extras_packages`: should amazon-linux-extras PHP packages be removed or not

See `defaults` and `vars` for the default values.

Dependencies
------------

* optional: ecgalaxy.bootstrap
* optional: ecgalaxy.common_packages
* optional: ecgalaxy.oracle_instantclient

On Amazon Linux 2 and Ubuntu, the `ecgalaxy.oracle_instantclient` role should be executed first
if `php_install_oci8_extension` is set to `true` (which is the default value).

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

Using multiple PHP versions
---------------------------

Installing and using multiple PHP versions is supported by executing the role multiple times with different values of `php_version`.

To switch to another version, use the `sudo update-alternatives` (Ubuntu) or `module load php<version>` (Amazon Linux, RedHat) command.

For instance, to switch to PHP 8.2:

On Ubuntu:

    sudo update-alternatives --set php /usr/bin/php8.2

On Amazon Linux, RedHat:

    . /etc/profile.d/modules.sh
    module load php82

License
-------

Copyright the European Union 2022.

Licensed under the EUPL-1.2 or later.

Author Information
------------------

ECGALAXY team.
