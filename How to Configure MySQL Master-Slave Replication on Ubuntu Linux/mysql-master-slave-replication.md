Replication in MySQL means copying data automatically from one database server (Master) to another (Slave). This is used for backup, high availability, and load balancing.

🔹 1. Prerequisites

2 Ubuntu servers (or VMs/containers):

Master DB Server → 192.168.1.100

Slave DB Server → 192.168.1.101

MySQL installed on both servers.

Root or sudo access.

🔹 2. Configure the Master Server
Step 1: Edit MySQL Configuration

Open MySQL config file on Master:

sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf


Find these lines and update:

server-id = 1
log_bin = /var/log/mysql/mysql-bin.log
binlog_do_db = mydatabase   # replace with the DB you want to replicate


Save and restart MySQL:

sudo systemctl restart mysql

Step 2: Create Replication User

Log into MySQL on the Master:

mysql -u root -p


Run:

CREATE USER 'replica'@'%' IDENTIFIED BY 'StrongPassword';
GRANT REPLICATION SLAVE ON *.* TO 'replica'@'%';
FLUSH PRIVILEGES;

Step 3: Lock the Database and Get Coordinates
USE mydatabase;
FLUSH TABLES WITH READ LOCK;
SHOW MASTER STATUS;


📌 Note the File and Position values (e.g., mysql-bin.000001, position 120).
Keep this window open (don’t exit yet).

🔹 3. Configure the Slave Server
Step 1: Edit MySQL Config on Slave
sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf


Add:

server-id = 2
relay_log = /var/log/mysql/mysql-relay-bin.log


Restart MySQL:

sudo systemctl restart mysql

Step 2: Connect Slave to Master

Log into Slave MySQL:

mysql -u root -p


Run:

CHANGE MASTER TO
MASTER_HOST='192.168.1.100',
MASTER_USER='replica',
MASTER_PASSWORD='StrongPassword',
MASTER_LOG_FILE='mysql-bin.000001',   -- from Master status
MASTER_LOG_POS=120;                   -- from Master status

START SLAVE;

🔹 4. Verify Replication

On Slave:

SHOW SLAVE STATUS\G


Look for:

Slave_IO_Running: Yes

Slave_SQL_Running: Yes

If both are Yes, replication is working 🎉

🔹 5. Test Replication

On Master:

USE mydatabase;
CREATE TABLE test (id INT PRIMARY KEY, name VARCHAR(50));
INSERT INTO test VALUES (1, 'Hello Replication');


On Slave, check:

SELECT * FROM mydatabase.test;


You should see the same data ✅

📌 Summary

Master stores database changes in binary logs.

Slave reads those logs and applies them.

Used for backup, scaling read queries, and fault tolerance.
