# <div align="center">CDC Confluent Platform</div>

## Step-by-Step CDC Confluent Platform Postgres to Oracle

## **Step**
1. [Build Confluent Platform and Database on top of Docker](#step-1)
2. [Create table and data on PostgreSQL](#step-2)
3. [Create Source Postgres CDC to Confluent Platform](#step-3)
4. [Create Sink Oracle (JDBC) Connection to Confluent Platform](#step-4)
5. [Exercise](#step-5)

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


