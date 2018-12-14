# Ansible Role: Moodle
Installs and configures Moodle.

## Requirements
Make sure the [minimum requirements for Moodle](https://docs.moodle.org/en/Installing_Moodle) are meet before using this role.

## Role Variables
Available variables are listed below, see `defaults/main.yml` for the default values.

```yaml
moodle_root_path: /var/www/moodle
```
The path where Moodle will be installed.

```yaml
moodle_dataroot_path: /var/www/moodledata
```
The path for the 'moodledata' data folder. This will be created if it doesn't exist.

```yaml
moodle_version: '3.3'
```
By default, the latest version of Moodle will be installed. You can specify which version to install by setting the `moodle_version` variable.

```yaml
moodle_root_user: root
moodle_root_group: root
moodle_root_permissions: '0755'
```
By default, the owner and group of the 'moodle' root folder will be `root`. This can be changed by setting the `moodle_root_user` and `moodle_root_group` variables. The permissions mode for this folder is `0755` by default, use the `moodle_root_permissions` variable to change this.

```yaml
moodle_dataroot_user: www-data
moodle_dataroot_group: www-data
moodle_dataroot_permissions: '0777'
```
By default, the owner and group of the 'moodledata' folder will be `www-data`. This can be changed by setting the `moodle_dataroot_user` and `moodle_dataroot_group` variables. The permissions mode for this folder is `0777` by default, use the `moodle_dataroot_permissions` variable to change this.

```yaml
moodle_fullname: My Moodle website
moodle_shortname: mymoodle
```
Set the `moodle_fullname` variable to the fullname of the site. The `moodle_shortname` variable should contain the shortname of the site.

```yaml
moodle_wwwroot: https://example.com
```
The `moodle_wwwroot` variable should contain the web address for the Moodle site.

```yaml
moodle_database_type: pgsql
```
By default, Moodle uses MySQL for it's database. To use a different type of database, set the `moodle_database_type` variable. Supported database types are `pgsql, mariadb, mysqli, mssql, sqlsrv` and `oci`.

```yaml
moodle_database_name: example_database
moodle_database_user: example_user
moodle_database_password: secret
```
Configure the database that Moodle will use.

```yaml
moodle_database_host: '192.168.2.18'
moodle_database_port: '33060'
moodle_database_prefix: app_
```
The default database host used by Moodle is `localhost`, use the `moodle_database_host` variable to set this to something different. The default port used by the database is `3306` for MySQL, use the `moodle_database_port` variable to set a different port. The `mdl_` prefix is added to the name of all the database tables created by Moodle. To change this prefix set the `moodle_database_prefix` variable.

```yaml
moodle_admin_username: admin
moodle_admin_password: P@ssw0rd
moodle_admin_email: admin@example.com
```
Configure the default admin account.

```yaml
moodle_enable_debug: true
```
By default, debug mode is off for Moodle. To enable debug mode use the set the `moodle_enable_debug` variable to `true`.

## Dependencies
None.

## Example Playbook
```yaml
- hosts: server
  become: yes

  tasks:
  - import_role:
      name: damianlewis.moodle
```
