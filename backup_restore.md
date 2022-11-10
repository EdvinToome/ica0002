Install and configure infrastructure with Ansible:

    ansible-playbook infra.yaml

Restore MySQL data from the backup:
Enter these commands after configuring infrastructure with ansible:

    sudo -u backup duplicity --no-encryption restore rsync://EdvinToome@backup.larsenbiscuits.io/mysql /home/backup/restore/mysql
    mysql agama < /home/backup/restore/mysql/agama.sql

To enter root user: 'sudo su -'

You can verify by entering 'mysql'(type 'mysql' command) as root user and typing 'show databases;'

Restore InfluxDB data from the backup:

    sudo -u backup duplicity --no-encryption restore rsync://EdvinToome@backup.larsenbiscuits.io/influxdb /home/backup/restore/influxdb
    sudo -u backup influxd restore -portable /home/backup/restore/influxdb/

Check it by entering 'influx' as root user(type 'influx' command) and typing 'show databases;'