Galera SELinux Policy
=====================

## Testbed
* Cent OS 6.6
* selinux-policy-3.7.19-260.el6_6.2.noarch
* selinux-policy-targeted-3.7.19-260.el6_6.2.noarch
* MariaDB-Galera 10.0.16 x86_64 or latest

## Usage
``` shell
 [root@linux ~]# semanage port -m -t mysqld_port_t -p tcp 4444
 [root@linux ~]# semanage port -a -t mysqld_port_t -p tcp 4567
 [root@linux ~]# semanage port -a -t mysqld_port_t -p tcp 4568
 [root@linux ~]# checkmodule -Mmo mariadb-galera-cluster.mod mariadb-galera-cluster.te
 [root@linux ~]# semodule_package -m mariadb-galera-cluster.mod -o mariadb-galera-cluster.pp
 [root@linux ~]# semodule -i mariadb-galera-cluster.pp
```
