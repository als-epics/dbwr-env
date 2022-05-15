# Tomcat without any package managers

## Predefine variables

```bash
$ make vars FILTER=TOMCAT_

------------------------------------------------------------
>>>>          Current Environment Variables             <<<<
------------------------------------------------------------

TOMCAT_DEFAULT_PORT = 8083
TOMCAT_DEFAULT_SERVER_XML = server.xml
TOMCAT_HOME = /opt/tomcat9
TOMCAT_INSTALL_LOCATION = /opt/tomcat9
TOMCAT_MAJOR_VER = 9
TOMCAT_MINOR_VER = 0.58
TOMCAT_SRC = apache-tomcat-9.0.58.tar.gz
TOMCAT_URL = "https://archive.apache.org/dist/tomcat/tomcat-9/v9.0.58/bin/apache-tomcat-9.0.58.tar.gz"
TOMCAT_VER = 9.0.58
```

## Setup

```bash
make tomcat.get
make tomcat.install
make tomcat.exist
```

### Tomcat service
The Tomcat service itself isn't necessary for this application. However if one wants to have the tomcat service itself, please follow the below steps:

```
make tomcat.sd_install
make tomcat.sd_start
make tomcat.sd_status
```
There are several rules, which may be interested.

```bash
make tomcat.sd_conf.show
make tomcat.sd_stop
make tomcat.sd_disable
make tomcat.sd_enable
make tomcat.sd_clean
make 
```

## Tomcat Generic Service

The generic tomcat uses 8080, which has the conflict with our another services sometimes, so we would like to change it 8083.

Debian 10, the generic `server.xml` is located in `/etc/tomcat9`, and replace `8080` with `8083`.

```xml
    <Connector port="8083" protocol="HTTP/1.1"
               connectionTimeout="20000"
               redirectPort="8443" />
```
