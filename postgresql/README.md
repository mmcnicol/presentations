# postgresql


## install

// switch to root
su - 

apt-get update

apt-get install postgresql

postgresql-setup initdb

systemctl start postgresql

// so that postgresql starts automatically after reboot
systemctl enable postgresql

### set password to connect to postgresql via command line (linux user)

// verify that user "postgres" was added without a password, by installer
more /etc/passwd

// add a password to user "postgres"
passwd postgres
> enter password when prompted
> confirm password when prompted

### set password to connect to postgresql remotely

su - postgres

psql -d template1 -c "ALTER USER postgres WITH PASSWORD 'password1';"


## connect to postgresql database postgres

psql postgres


## create a new database

createdb newtestdb


## connect to postgresql database newtestdb

psql newtestdb


## list postgresql databases (when connected via psql)

\l


## quit postgresql (when connected via psql)

\q


## monitoring considerations

open firewall port, if applicable

default port 5432

### allow remote connection to postgresql, if applicable

cd /var/lib/pgsql/data

more pg_hba.conf

// towards end of file, find section & add:
host all all <server ip address> md5

### check which ip address(es) postgress should listen on

cd /var/lib/pgsql/data

more postgresql.conf

// section "connections and authentication"; listen_address...should be 'localhost', or '*', etc., as appropriate

// restart postgresql to pick up configuration changes
systemctl restart postgresql



---


PostgreSQL - A Crash Course
https://youtu.be/AtIopyyumvk












