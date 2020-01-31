# Osquery in a Box

This repository is a collection of resources useful for setting up a test environment with osquery, Fleet, and an ELK stack.

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
