# Install MySQL Ubuntu 14.04

## Install the Server

```bash
sudo apt-get update
```

```bash
sudo apt-get install mysql-server
```

```bash
sudo mysql_secure_installation
```

```bash
sudo mysql_install_db
```

- Open /etc/mysql/my.cnf
- Change bind address to 0.0.0.0
- Log in to MySQL console

```sql
CREATE USER 'user'@'%' IDENTIFIED BY 'password';
```

```sql
GRANT ALL PRIVILEGES ON *.* TO 'user'@'%' WITH GRANT OPTION;
```

```sql
FLUSH PRIVILEGES;
```