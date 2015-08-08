In case of broken databases (InnoDB engine) try:

Either delete the whole db and restart ``rm /var/lib/mysql/ibdata1``

#OR

``mysql --innodb_force_recovery=1 `` /*+1 if it fails ... wird in 5.5.44 nicht erkannt #http://dev.mysql.com/doc/refman/5.6/en/forcing-innodb-recovery.html#

``mysqlcheck --all-databases``

``mysqldump --force --compress --triggers --routines --create-options -uroot -p --all-databases > /home/pi/alldb-recovery.sql``

``mysqladmin -uUSERNAME -pPASSWORD shutdown``

``rm -fdr /var/lib/mysql``

``mkdir /var/lib/mysql \
chown -R mysql:mysql /var/lib/mysql \
/usr/local/bin/mysql_install_db \
chown -R mysql:mysql /var/lib/mysql``

``mysql -uroot --compress < /home/pi/alldb-recovery.sql``

``/usr/local/bin/mysqladmin -uroot flush-privileges ``

#OR

``sudo /etc/init.d/mysql status`

``sudo /etc/init.d/mysql stop`

``sudo cp -r /var/lib/mysql /home/pi/sicherung/mysql``

``sudo rm -r /var/lib/mysql/klima_growbox``

``sudo rm  /var/lib/mysql/ibdata``

``sudo rm  /var/lib/mysql/ib_logfile0``

``sudo rm  /var/lib/mysql/ib_logfile1``

``sudo /etc/init.d/mysql start`

http://www.tecmint.com/mysqladmin-commands-for-database-administration-in-linux/
