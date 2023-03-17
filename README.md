# Group Project: System For Predicting And Determining Where Harmful Substance Emissions Into The Air Come From

Web application allows you to forecast and identify the source of emissions of harmful substances into the air.

## Server Installation

Clone the repository to your computer:
```bash
git clone https://github.com/VictorKostinOfficial/groupProject.git
```

### Requirements:

Install the appropriate software:

1. [Docker Desktop](https://www.docker.com).
2. [Git](https://github.com/git-guides/install-git).
3. [PyCharm](https://www.jetbrains.com/ru-ru/pycharm/download) (optional).

### Usage:

1. To configure the application copy `.env.sample` into `.env` file:
    ```shell
    cp .env.sample .env
    ```
    This file contains environment variables that will share their values across the application. 
    The sample file (`.env.sample`) contains a set of variables with default values. 
    So it can be configured depending on the environment.
    
    Set influxdb environment variable values (in `.env` file):
    - `DOCKER_INFLUXDB_INIT_USERNAME` - for influxdb user username
    - `DOCKER_INFLUXDB_INIT_PASSWORD` - for influxdb user password
    - `DOCKER_INFLUXDB_INIT_ORG` - for influxdb initial organisation name
    - `DOCKER_INFLUXDB_INIT_BUCKET` - for influxdb initial bucket name
    - `DOCKER_INFLUXDB_INIT_ADMIN_TOKEN` - for influxdb initial admin token
    
    Set postgres environment variable values (in `.env` file):
    - `POSTGRES_USER` - for postgres user username
    - `POSTGRES_PASSWORD` - for postgres user password
    - `POSTGRES_DB` - for postgres initial database name
    
    Set postgres environment variable values for cron (in `.env` file):
    - `CRON_POSTGRES_USER` - for postgres cron username
    - `CRON_POSTGRES_VALUE` - for postgres cron password
    
2. Build the container using Docker Compose:
    ```shell
    docker compose build
    ```
    This command should be run from the root directory where `Dockerfile` is located.
    You also need to build the docker container again in case if you have updated `requirements.txt`.
    
 3. To start the application run:
    ```shell
    docker compose up -d
    ```
   
    This command should be run from the root directory where docker-compose is located.
   
    A background program will start that will collect information about wheather from `https://open-meteo.com` API and save
    it to `influxdb`. The data collection process runs once per hour.
