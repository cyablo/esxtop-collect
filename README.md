# esxtop-collect
Daemon has to be deployed on every vSphere server. It collects esxtop's statistics to influxdb for further use, for example, in grafana

# Preparing for first use
1. Enable remote SSH console on vSphere hosts
2. Place daemon and init scripts in /bin and /etc/init.d directories
3. Edit influxdb_server and influxdb_dbname in /bin/esxtop-collect
4. chmod 755 /bin/esxtop-collect /etc/init.d/esxtop-collect
5. chkconfig esxtop-collect on
6. /etc/init.d/esxtop-collect start

# Making installation easier on other hosts in a cluster

Prepare

1. Login to remote SSH console on vSphere host
2. cd / ; rm /esxtop-collect.tgz ; tar -cz -f /esxtop-collect.tgz /bin/esxtop-collect /etc/init.d/esxtop-collect
3. Place esxtop-collect.tgz on a web server

Install

1. wget -O - http://.../esxtop-collect.tgz | tar - xz -C /
2. chkconfig esxtop-collect on
3. /etc/init.d/esxtop-collect start

