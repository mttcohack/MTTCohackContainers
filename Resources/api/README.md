# API Container

## Usage

Here you can find the source files to build this container. The container is a web API that returns JSON payload. It offers the following endpoints:

* `/api/healthcheck`: returns a basic JSON code to verify if the application is running, it can be used for liveliness probes
* `/api/sqlversion`: returns the results of a SQL query (`SELECT @@VERSION` for SQL Server or `SELECT VERSION();` for MySQL/Postgres) against a SQL database. You can override the value of the `SQL_SERVER_FQDN` via a query parameter
* `/api/sqlsrcip`: returns the results of a SQL query (`SELECT CONNECTIONPROPERTY("client_net_address")` for SQL Server, `SELECT host FROM information_schema.processlist WHERE ID=connection_id();` for MySQL or `SELECT inet_client_addr ();` for Postgres) against a SQL database. You can override the value of the `SQL_SERVER_FQDN`, `SQL_SERVER_USERNAME`, `SQL_SERVER_PASSWORD` and `SQL_SERVER_ENGINE` via a query parameter
* `/api/ip`: returns information about the IP configuration of the container, such as private IP address, egress public IP address, default gateway, DNS servers, etc
* `/api/dns`: returns the IP address resolved from the FQDN supplied in the parameter `fqdn`
* `/api/printenv`: returns the environment variables for the container
* `/api/curl`: returns the output of a curl request, you can specify the argument with the parameter `url`
* `/api/pi`: calculates the decimals of the number pi, you can specify how many decimals with the parameter `digits`. 1,000 digits should be quick, but as you keep increasing the number of digits, more CPU will be required. You can use this endpoint to force the container to consume more CPU
* `/api/sqlsrcipinit`: the previous endpoints do not modify the database. If you want to modify the database, you need first to create a table with this endpoint
* `/api/sqlsrciplog`: this endpoint will create a new record in the table created with the previous endpoint (`sqlsrcipinit`) with a timestamp and the source IP address as seen by the database.

The container requires these environment variables :

* `SQL_SERVER_FQDN`: FQDN of the SQL server
* `SQL_SERVER_DB` (optional): FQDN of the SQL server
* `SQL_SERVER_USERNAME`: username for the SQL server
* `SQL_SERVER_PASSWORD`: password for the SQL server
* `SQL_ENGINE`: can be either `sqlserver`, `mysql` or `postgres`
* `PORT` (optional): TCP port where the web server will be listening (8080 per default)
* `USE_SSL` (optional): Connect to the database using SSL. Can be either `yes` or `no`. Default `yes`.


## Build

You can build the image locally with:

docker build -t cohack/sqlapi:1.0 .

## Deploy

### Test this against an Azure SQL Database

You need an Azure Sql Database. This was installed during the "before CoHack" deployment:
Please go to you Azure Portal to find the SQL details


### Run this image locally

docker run -d -p 8080:8080 -e "SQL_SERVER_FQDN=yourdatabase.com" -e "SQL_SERVER_USERNAME=your_db_admin_user" -e "SQL_SERVER_PASSWORD=your_db_admin_password" --name api cohack/sqlapi:1.0
