In case of broken databases (InnoDB engine) try:

Either delete the whole db and restart ``rm /var/lib/mysql/ibdata1``

#OR

``mysql --innodb_force_recovery=1 `` /*+1 if it fails #http://dev.mysql.com/doc/refman/5.6/en/forcing-innodb-recovery.html#

``mysqlcheck --all-databases``

``mysqldump --force --compress --triggers --routines --create-options -uroot -p --all-databases > /home/pi/alldb-recovery.sql``

``mysqladmin -uUSERNAME -pPASSWORD shutdown``

``rm -fdr /var/lib/mysql``

``mkdir /var/lib/mysql \
chown -R mysql:mysql /usr/local/var \
/usr/local/bin/mysql_install_db \
chown -R mysql:mysql /usr/local/var``

``mysql -uroot --compress < /home/pi/alldb-recovery.sql``

``/usr/local/bin/mysqladmin -uroot flush-privileges ``
