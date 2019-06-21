# Superset-BI-Platform-based-on-Linux

### 1. Background info

The aim of me to start the project is that I am handling tuns of daily-reports, and those reports even made me could not breathed.
Now I am sharing you my steps of building `Superset` on a Linux Server. 


### 2. The Structure of my Superset-BI-Platform
![](https://github.com/loktarjason/Superset-BI-Platform-based-on-Linux/blob/master/images/supersetBIstructure.png)
The Structure is sample, my superset is builded on a Server and the Server connect to the Database, then users use their accounts visit the Superset-BI-Platform through a http link and see the visualized datas.

### 3. Steps of building the Superset on Server(based on CentOS 7.x)
The following list is what you need before you `pip` Superset:
* database installation
* sqlite3 package
* python3.6<br>

Before you start to install superset, you should check your linux systerm, make sure it is allready installed Database clients_installation, because superset needs the database installation to connect the database. 
In my case I use Oracle Database, so I installed the Oracle database through `rpm` with a `oracle install.rpm`, `wget`from oracle official website. Then check your systerm to see if you installed `sqlite3 package`(it's a python package),
`superset` will need it for `init` after that you need a `python3.6`（superset official doc claims that they test the py3.6 environment） in your systerm to `pip` the superset.
