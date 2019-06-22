# Server Environment(Linux CentOS 7.x)<br>

## Download and install oracle-instantclient as root<br>
```
wget --http-user=you@domain.com --ask-password "http://download.oracle.com/otn/linux/instantclient/122010/oracle-instantclient12.2-precomp-12.2.0.1.0-1.i386.rpm" -O oracle-instantclient12.2-precomp-12.2.0.1.0-1.i386.rpm
rpm -ivh oracle-instantclient12.2-precomp-12.2.0.1.0-1.i386.rpm
```


## Configure profile<br>
```
su - oracle
vi ~/.bash_profile 
```


## Insert into bash_profile<br>
```
export LD_LIBRARY_PATH=/usr/lib/oracle/12.2/client64/lib
export TNS_ADMIN=/usr/lib/oracle/12.2/client64/
export PATH=/usr/lib/oracle/12.2/client64/bin:$PATH
--type'esc' then':''w''q' --save the config<br>
```


## Prepare the environment for python3.6 and superset<br>
```
yum install gcc gcc-c++ libffi-devel python-devel python-pip python-wheel openssl-devel libsasl2-devel openldap-devel
```


## Install python3.6 (with sqlite3)<br>
```
wget https://www.python.org/ftp/python/3.6.5/Python-3.6.5.tgz
tar -xzvf Python-3.6.5.tgz -C  /tmp
cd  /tmp/Python-3.6.5/
./configure --prefix=/usr/local
make
make install
```


## Pip install virtualenv --for making a virtualenv environment for superset<br>
```
pip install virtualenv
```


## Create and active the venv environment<br>
```
python3 -m venv
source venv/bin/activate
--you could shut it down by 'deactivate'
```


## Before pip superset you need a lower version pandas and SQLAlchemy<br>
```
pip install pandas==0.23.4
pip install SQLAlchemy==1.2.18

#In my case I use Oracle DB so I install Oracle DB py driver.
pip install cx_Oracle
```


## Pip superset<br>
```
pip install superset
```


## Steps need to be finished besfore you start superset<br>


### Set up Superset<br>
```
# Set up an admin account
fabmanager create-admin --app superset 

#Initialize db
superset db upgrade

#import Example data(do not recommed you to do this process, cause the example data may infect your own data.)
superset load_examples

#initialize user account roles
superset init

#start superset server with a specified port(make sure the port is already open)
superset runserver -d -p 8081

```

 
### Keep superset running in the Linux background<br>
```
nohup superset runserver -p 8081&
```
 
 
### Kill superset server<br>
```
ps -ef | grep superset
kill pid
```


