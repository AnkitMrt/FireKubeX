# Kubernetes Resource Generator

This Python application dynamically generates Kubernetes resource files (Deployment, ConfigMap, etc.) based on the configuration provided in a YAML file. It utilizes Jinja templates to streamline the resource creation process.

## Table of Contents

- [Overview](#overview)
- [Requirements](#requirements)
- [Usage](#usage)
- [Configuration](#configuration)
- [Examples](#examples)

## Overview

The `start.py` script reads the configuration from the `config.yaml` file and generates Kubernetes resource files for each specified service. With this script, developers can deploy their applications without requiring in-depth knowledge of Kubernetes.

## Requirements

- [X] **Python 3.X**
- [X] **kubectl installed and configured for the target Kubernetes cluster**
- [X] **Dockerfiles** (for the applications you want to deploy)


## Usage

1. **Clone the repository:**

   ```bash
   git clone https://github.com/mindfiredigital/FireKubeX.git
   cd FireKubeX


## Configuration

### `config.yaml`

The `config.yaml` file is the main configuration file for the script. You should provide the following information for each application you want to deploy:

- `version`: The script version (currently 3.2).

- `service`: A dictionary containing information about each application. You can configure multiple applications in this section. For each application, provide the following details:

  - `image`: The Docker image address for the application.
  
  - `name`: The name of the application, which will be used as the namespace in Kubernetes.

  - `port`: The port on which the application should listen.

  - `ContainerPath`: The path within the container where the application files are stored.

  - `ServiceLocalPath`: The local path on the host machine where the application files are stored.

  - `ReplicaSet`: The number of replicas you want for the application (optional).

  - `configmaps`: Configuration settings for the application. You can specify environment variables and their values here.

  - `tags`: Tags or labels for the application (optional).

### `core.yaml`

For core services, you can use a separate `core.yaml` file with the same structure as `config.yaml`. This allows you to configure core services separately.

## Usage

The script provides several command-line options:

- `--start <name>`: Start a specific service by providing its name. You can also use `--start all` to start all services.

- `--stop <name>`: Stop a specific service by providing its name.

- `--core`: Use this option to parse and apply services from `core.yaml`.

## How to Run

Running this script is pretty straight forward.

**For starting a specific service**

```shell
python3 start.py --start <service_name>
```

**For starting all services**

```shell
python3 start.py --start all
```
**For Deleting a specific service and components**

```shell
python3 start.py --stop <service_name>
```

**For Deleting all service and components**

```shell
python3 start.py --stop all
```

**For setting up Harbor image repository and components**

```shell
python3 start.py --harbor
```


## Notes
- The Dockerfile for each application must be present in the source code repository.

- This script is designed to work with various Kubernetes setups, including both cloud and on-premises clusters.

## Conclusion

This script simplifies the deployment process for developers by abstracting the complexities of Kubernetes. By providing the necessary configuration in the config.yaml file, developers can quickly deploy their applications to a Kubernetes cluster with ease.
Enjoy deploying your applications without the need for in-depth Kubernetes knowledge!
