# Osquery in a Box

This repository is a collection of resources useful for setting up a test environment with [osquery](https://github.com/osquery/osquery), [Fleet](https://github.com/kolide/fleet), and an [ELK stack](https://github.com/elastic).

## Requirements

The only requirement for running this test environment is a working installation of [Docker](https://www.docker.com/products/docker-desktop).

## Usage

The provided `docker-compose.yml` file will start Fleet and its dependencies, along with the ELK stack:

``` shell
docker-compose up
```

### Configure Fleet

Open [https://localhost:8412](https://localhost:8412) to set up the Fleet server (note, the server is using a self-signed certificate and will generate a warning in your browser).

### Configure ELK

Logstash is configured to send osquery logs from the Fleet server into an Elasticsearch index named `osquery-result`.

Open [http://localhost:5601/app/kibana#/management](http://localhost:5601/app/kibana#/management) to manage the Kibana and Elasticsearch configurations.

### Run osquery

The [`osquery`](./osquery) directory contains a `docker-compose.yml` and additional configuration files to start containerized osquery agents. To start osquery, first retrieve the "Enroll Secret" from Fleet (by clicking the "Add New Host") button in the Fleet dashboard, or with `fleetctl get enroll-secret`).

``` shell
cd osquery
ENROLL_SECRET=<copy from fleet> docker-compose up
```

## Can I run this in production?

This depends on what "production" means to you. There are a number of tradeoffs
made to simplify this configuration that would not fit the needs for a typical
production deployment. A partial list:

- The configuration uses a self-signed TLS certificate with a well-known private
  key (that key is in this repo).
- The database credentials are well-known (in this repo).
- Only a single instance of each service is run. There is no failover.
- All services are run on a single physical/virtual host machine.

Depending on your use-case, this repository may work as an effective starting
point for a production deployment.
