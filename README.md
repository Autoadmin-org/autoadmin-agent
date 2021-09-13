# Autoadmin-agent

There are two options for installing Autoadmin-agent: using Docker Desktop (for MacOS and Windows) or using Docker Engine (for Linux).


## Installing autoadmin using docker

Open Terminal app and run following commands:

```bash

docker pull autoadminorg/autoadmin-agent
docker run -e CONNECTION_TOKEN=connection_token -e CONNECTION_TYPE=mysql -e CONNECTION_USERNAME=your_username \
    -e CONNECTION_PASSWORD=your_password -e CONNECTION_HOST=example.com autoadminorg/autoadmin-agent
```

## Install via Docker Compose

First step is installing [Docker Engine](https://docker.com).
On Linux, please install [Docker Compose](https://docs.docker.com/compose/install/) as well.
> Note: Docker Desktop on Windows and MacOS already include Docker Compose.

Second step – create **docker-compose.yml** file. 
Copy and paste configuration from [(source file)](https://github.com/Autoadmin-org/autoadmin-agent/blob/master/docker-compose.yml) or download this file.

Third step – create **.config.env** file in the same directory. 
Copy and paste the contents of [(source file)](https://github.com/Autoadmin-org/autoadmin-agent/blob/master/.config.env) or download this file.

Fourth step – open **.config.env** file and specify all required credentials:

|Variable|Description|
|---|---|
|CONNECTION_TOKEN|Unique connection token you received when created connection on main page. **Example:** IqqGdSLbB-F-ozinkrtegADNaukDbIlyDcZjz-PxjHqGJr1HNxjNLW7dwG8I7a4q|
|CONNECTION_TYPE|Type of your database. **Values:** oracledb, mysql, postgres, mssql   |
|CONNECTION_HOST|IP or URL where your database is located. **Example:** mysql-157d19f-project-a403.aivencloud.com  |
|CONNECTION_PORT|Server port where database is located. **Example:** 16144   |
|CONNECTION_USERNAME|Your database username. **Example:** admin |
|CONNECTION_PASSWORD|Your database password. **Example:** 6K4vT@w2qKJ{A^ |
|CONNECTION_DATABASE|Your database name. **Example:** defaultdb |
|CONNECTION_SCHEMA|Your database schema, if exists. **Example:** testsch |
|CONNECTION_SID|Your database SID (it's instance id for **oracle** database only)   |
|CONNECTION_SSL|SSL option. **Values:** 1 – SSL on, 0 – SSL off|
|CONNECTION_SSL_SERTIFICATE|SSL sertificate is required if you want use SSL connection to your database. Replace line breakes with spaecial characters \n and quote a line. You can also write the key to a file /storage/ssl-cert.txt and leave this field blank   |
|APP_PORT|Port on you computer, where agent application will be runned. **By default:** 7007|
|LOGS_TO_TEXT_FILE|Writing logs to a text file (/storage/stored-logs/logs.txt. **Values:** 1 – save logs in text file; 0 – don't save|

Open Terminal app and run:

```sh
docker-compose up --build
```
After sucessfull execution, new connection will appear in Autoadmin Connections List.

