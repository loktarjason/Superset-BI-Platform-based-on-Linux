#Server Environment(Linux CentOS 7.x)<br>
##oracle-instantclient -do not forget rename your downloaded file.<br>

##download oracle-instantclient<br><br>
```
wget --http-user=you@domain.com --ask-password "http://download.oracle.com/otn/linux/instantclient/122010/oracle-instantclient12.2-precomp-12.2.0.1.0-1.i386.rpm" -O oracle-instantclient12.2-precomp-12.2.0.1.0-1.i386.rpm
```

##install oracle-instantclient as root<br><br>
```
rpm -ivh oracle-instantclient12.2-precomp-12.2.0.1.0-1.i386.rpm
```

##configure profile<br>
```
su - oracle
vi ~/.bash_profile 
```

##insert into bash_profile<br>
```
export LD_LIBRARY_PATH=/usr/lib/oracle/12.2/client64/lib
export TNS_ADMIN=/usr/lib/oracle/12.2/client64/
export PATH=/usr/lib/oracle/12.2/client64/bin:$PATH
--type'esc' then':''w''q' --save the config<br>
```

##Prepare the environment for python3.6 and superset<br>
```
yum install gcc gcc-c++ libffi-devel python-devel python-pip python-wheel openssl-devel libsasl2-devel openldap-devel
```

##install python3.6 (with sqlite3)<br>
```
wget https://www.python.org/ftp/python/3.6.5/Python-3.6.5.tgz
tar -xzvf Python-3.6.5.tgz -C  /tmp
cd  /tmp/Python-3.6.5/
./configure --prefix=/usr/local
make
make install
```

##pip install virtualenv --for making a virtualenv environment for superset<br>
```
pip install virtualenv
```

##create and active the venv environment<br>
```
python3 -m venv
source venv/bin/activate
--you could shut it down by 'deactivate'
```

##unser the venv what you have done stay in venv<br>
###before pip superset you need a lower version pandas and SQLAlchemy<br>
```
pip install pandas==0.23.4
pip install SQLAlchemy==1.2.18
```

##pip superset<br>
```
pip install superset
```

##steps need to be finished besfore you start superset<br>

###set up an admin account<br>
```
fabmanager create-admin --app superset 
```

###initialize db<br>
```
superset db upgrade
```

```
--import some examples data sets in cause you need it.(I do not recommed you do this process, cause the esample data may infect your data.)
--superset load_examples
```

###initialize user account roles<br>
```
superset init
```

###start superset server with a specified port(make sure the port is already open)<br>
```
superset runserver -d -p 8081
```

###keep superset running in the background<br>
```
nohup superset runserver -p 8081&
```

###kill superset server<br>
```
ps -ef | grep superset
kill pid
```


