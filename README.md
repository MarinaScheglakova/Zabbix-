# Zabbix-server
1. apt install postgresq
2. wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-4+debian11_all.deb
3. dpkg -i zabbix-release_6.0-4+debian11_all.deb
4. apt update
5. apt install zabbix-server-mysql zabbix-frontend-php zabbix-apache-conf zabbix-sql-scripts
6. su - postgres -c 'psql --command "CREATE USER zabbix WITH PASSWORD'\'123456789\'';"'
7. su - postgres -c 'psql --command "CREATE DATABASE zabbix OWNER zabbix;"'
8. zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix
9. sed -i 's/# DBPassword=/DBPassword=123456789/g' /etc/zabbix/zabbix_server.conf 
10. systemctl restart zabbix-server apache2
11. systemctl enable zabbix-server apache2
12. systemctl status zabbix-server.service
![image](https://github.com/MarinaScheglakova/Zabbix-/assets/173897293/436a136a-9b59-47c4-b254-8fa6752ce97f)

# Zabbix-agent 
1. dpkg -i zabbix-release_6.0-4+debian11_all.deb
2. apt install zabbix-agent
3. systemctl restart zabbix-agent
4. systemctl enable zabbix-agent
5. systemctl status zabbix-agent.service
![image](https://github.com/MarinaScheglakova/Zabbix-/assets/173897293/e7f07aef-dcd5-4c54-bdf6-3d36813caa24)
