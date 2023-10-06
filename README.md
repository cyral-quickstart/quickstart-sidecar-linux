# Sidecar - Linux

A quick start to deploy a sidecar to a Linux machine.

This repo provides a script that help install the Cyral Sidecar via linux packages.

Please review the [sidecar deployment](https://cyral.com/docs/sidecars/deployment)
for more information.

These instructions have been fully tested on the following operating systems:
- Ubuntu 20.04.2 LTS
- RHEL 8.3.0
- CentOS Linux release 8.3.2011
- Oracle Linux 8

> **NOTE:** This script assumes that you have superuser privileges on the target machine.

## Install

### Requirements

* A Linux machine with at least 1 CPU, 4GB of RAM and 5GB of available disk space.
* You will either need to be root or have sudo permissions on the target machine in order to run the install script.
* Make sure [curl](https://curl.se/download.html) and [jq](https://stedolan.github.io/jq/download/) are 
installed on the target machine.

> **IMPORTANT:** You must run the script as **superuser**!

### Examples

#### Quick Start

* Open a terminal window in the location where you will install the sidecar.
* Export the environment variables `CYRAL_SIDECAR_ID`, `CYRAL_CONTROL_PLANE`, 
`CYRAL_SIDECAR_CLIENT_ID` and `CYRAL_SIDECAR_CLIENT_SECRET` with the information 
from the `Cyral Templates` option in the `Deployment` tab of your sidecar details.
* Export the environment variable `CYRAL_SIDECAR_VERSION` with the desired sidecar
version.
* Run [install-linux.sh](https://github.com/cyral-quickstart/quickstart-sidecar-linux/blob/v0.1.0/install-linux.sh) as a super user.

Use the command below as an example:

```bash
sudo CYRAL_CONTROL_PLANE='<control plane url>' \
CYRAL_SIDECAR_ID='<sidecar id>' \
CYRAL_SIDECAR_CLIENT_ID='<client id>' \
CYRAL_SIDECAR_CLIENT_SECRET="<client secret>" \
CYRAL_SIDECAR_VERSION='<sidecar version>' \
bash -c "$(curl -fsSL https://raw.githubusercontent.com/cyral-quickstart/quickstart-sidecar-linux/main/install-linux.sh)"
```

Otherwise you can do a git clone and execute the install:

```bash
git clone https://github.com/cyral-quickstart/quickstart-sidecar-linux.git
sudo CYRAL_CONTROL_PLANE='<control plane url>' \
CYRAL_SIDECAR_ID='<sidecar id>' \
CYRAL_SIDECAR_CLIENT_ID='<client id>' \
CYRAL_SIDECAR_CLIENT_SECRET="<client secret>" \
CYRAL_SIDECAR_VERSION='<sidecar version>' \
./install-linux.sh
```

#### Production Starting Point

* Download the sidecar binaries and store it on a preferred location (run the quick start installation
procedure to download it).
* Export the environment variables `CYRAL_SIDECAR_ID`, `CYRAL_CONTROL_PLANE`, 
`CYRAL_SIDECAR_CLIENT_ID` and `CYRAL_SIDECAR_CLIENT_SECRET` with the information 
from the `Cyral Templates` option in the `Deployment` tab of your sidecar details.
* Download the [install-linux.sh](https://github.com/cyral-quickstart/quickstart-sidecar-linux/blob/v0.1.0/install-linux.sh)
to the target machine.
* Make the `install-linux.sh` executable:
   ```
   chmod +x install-linux.sh
   ```
* Use the `--local_package` argument to provide the location of the downloaded binaries.


```bash
sudo CYRAL_CONTROL_PLANE='<control plane url>' \
CYRAL_SIDECAR_ID='<sidecar id>' \
CYRAL_SIDECAR_CLIENT_ID='<client id>' \
CYRAL_SIDECAR_CLIENT_SECRET="<client secret>" \
CYRAL_SIDECAR_VERSION='<sidecar version>' \
./install-linux.sh --local_package=<binary_path>
```

A note on running multiple nodes of one sidecar, or multiple sidecars:

The installation steps on this page should be performed on any host
that will be running a sidecar. Take care to note the difference
between multiple instances of a sidecar vs. multiple sidecars:

- If multiple hosts will be configured as instances of the same
  sidecar, then repeat the installation procedure using the settings
  you got in the steps above.

- If you are planning to have each host operate as an individual
  sidecar (each with its own configuration in the Cyral control
  plane), then you will also need to repeat the steps above to get a
  unique Sidecar ID, Client ID, and Client Secret for each host.

## Parameters

**--local_package**: specify path to an already-downloaded Cyral sidecar RPM/DEB package, and prevent the script from downloading a new one.

## Advanced

Instructions for advanced deployment configurations are available for the following topics:

* [Configure the sidecar for SSO](./docs/sso.md)
* [Sidecar certificates](./docs/certificates.md)
* [Sidecar instance metrics](./docs/metrics.md)
* [Sidecar process monitoring](./docs/process-monitoring.md)
