# <div align="center">CDC Confluent Platform Demo</div>

## Step-by-Step CDC Confluent Platform Postgres to Oracle

## **Step**
1. [Build Confluent Platform and Database on top of Docker](#step-1)
2. [Create table and data on PostgreSQL](#step-2)
3. [Create Source Postgres CDC to Confluent Platform](#step-3)
4. [Create Sink Oracle (JDBC) Connection to Confluent Platform](#step-4)
5. [Insert, Update, Delete changes](#step-5)
6. [Single Message Transform](#step-6)
7. [Exercise](#step-7)

***

## **Prerequisites**
<br>

1. Installed docker and docker-compose
2. DBeaver (optional)

## <a name="step-1"></a>Build Confluent Platform and Database on top of Docker

1. Make sure you already clone the git from the repo to your local environment.
```git
git clone https://github.com/ihengki17/cdc-confluent-platform.git
```
2. Bring up all of the component on the docker-compose to your local environment.
```docker
docker-compose up -d
```
3. Wait until all of the component is up and running, you could also check the component status using Control Center.
```C3
http://localhost:9021
or
http://<hostname>:9021
```
## <a name="step-2"></a>Create table and data on PostgreSQL

1. Create table and data through the DBeaver or inside the docker as you would like to create
2. The user and password could be found in docker-compose.yml **User: docker, Password: docker**
3. If you doesn't have any data refference you could use the postgres.sql to create and fill the data to the table

## <a name="step-3"></a>Build Confluent Platform and Database on top of Docker

1. Access Control Center and click connect tab on the left side
2. Click the connect-cluster
3. Now import the **connector_CDC_Postgres_config.json** to the Kafka Connect to deploy the task
4. You could change or modified the config as you seen fit to your demo
5. If all set, click next and launch the connector
6. You'll see red or failed the connector, but give a couple seconds and it will be running well
7. If the Connector is running well you'll get a new topic with the message inside the Cluster
   * Click Topics on the left side
   * Click the topics name (by using the json that has been provide it will be **CDC.public.customers**)
   * Click **Messages** tab
   * Click the offset bar on the right middle page, type 0 and enter
   * You'll see the message that starting from offset 0 up to now

You could use API to deploy the connector as you see fit and easier to deploy the connector.

## <a name="step-4"></a>Create Sink Oracle (JDBC) Connection to Confluent Platform

1. Access Control Center and click connect tab on the left side
2. Click the connect-cluster
3. Now import the **connector_Oracle_Sink_config.json** to the Kafka Connect to deploy the task
4. You could change or modified the config as you seen fit to your demo
5. If all set, click next and launch the connector
6. Now check the Oracle DB and you'll find that will be new table with 

## <a name="step-5"></a>Insert, Update, Delete changes

1. Let's do the fun part where we could see how the data could be append into the table, updated or delete the data.
2. Insert, let's insert one of the data using this query
3. Check the Oracle DB how the data append on the table
4. Update, let's update the new data using this query
5. Check the Oracle DB how the data updated on Oracle DB
6. Delete, let's delete the data using this query
7. Check the Oracle DB how the data deleted from your table

## <a name="step-6"></a>Single Message Transform

1. Let's try to run one more connect CDC using SMT for masking the field
2. We could also deploy the connector using API
```bash
curl -i -X PUT -H  "Content-Type:application/json" http://localhost:8083/connectors/CDC_postgres_masking/config -d @connector_cdc_postgres_masking_config.json
```

3. Now check the topic CDC_Masking.public.customers and see inside the message 


## <a name="step-7"></a>Exercise

1. Now let's do more through our environment
2. Let's filter and transform your data using ksqlDB
3. Create Oracle CDC Source Connector on the existing table
4. Create Sink Connection to another external system on your environment

