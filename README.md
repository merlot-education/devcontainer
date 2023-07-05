# VSCode DevContainer based development environment

## Description

This repository defines a development container to be used together with VSCode containing the necessary tools to develop infrastructure and platform services.
<br>
It can be used independent from th OS you are working in and could be Linux, MacOS, Windows and WSL2 as well.

## Installation

### Precondition

- Working Docker installation on the host you plan to use for running the devcontainer
- Working VSCode installation on the host. In case you use WSL2. VSCode is expected to be installed on Windows
- Working Git installation on the devcontainer host

### Configuration

The current devcontainer implementation expect several environment variables set on the host to work properly. The same apply for some directories which must be present as they are mounted into the devcontainer.

#### Environment Variables

The following variables are used to access various accounts at our infrastructure hoster and described in our project documentation.

- MERLOT_IONOS_USERNAME
- MERLOT_IONOS_PASSWORD
- MERLOT_WORKSPACE points to a directory where all modifications made inside the devcontainer are persisted. Repository checkouts inside the devcontainer should be stored here. See also the use of mounted directories below.
  **Please regard that the path of this environment variable must be absolute.**
  <br>
- HOSTNAME environment variable must be set with the hostname of the host, otherwise the devcontainer host cannot be set, eg. <code>export HOSTNAME=`hostname`</code>

#### Directories

Some directory mount sources will be directly take from the container host, others are recommended to be set specific for a project. Therefor a project specific directory containing the mount sources seems to be a best practice. This ensure that modifications inside the devcontainer are persisted in the host. The environment variable MERLOT_WORKSPACE points to this directory.

- The HOME directory of the host will be mounted at "/localhome" of the devcontainer. Just for convenience. Not used directly otherwise.
- .kube of HOME directory of the host will be mounted in the HOME directory of the devcontainer
- .ssh of HOME directory of the host will be mounted in the HOME directory of the devcontainer
- .history of MERLOT_WORKSPACE will be mounted in the HOME directory of the devcontainer to allow persistence of the command history between container rebuilds/restarts
- .ansible of MERLOT_WORKSPACE will be mounted in the HOME directory of the devcontainer to allow persistence Ansible collections from galaxy
- .config of MERLOT_WORKSPACE will be mounted in the HOME directory of the devcontainer to allow persistence of various installation artifacts
- .local of MERLOT_WORKSPACE will be mounted in the HOME directory of the devcontainer to allow persistence of various installation artifacts

## Usage

- Checkout the [devcontainer](git@github.com:merlot/devcontainer.git) repository in a directory separate from the MERLOT_WORKSPACE
- Change into that directory
- Open the folder with <code>code .</code>
- Accept reopen as devcontainer if asked

## Useful links

### Devcontainer

- [List of available Features][features]
- [Developing inside a Container][containerdevelopment]
- [Advanced container configuration][advancedcontainer]
- [Team specific Features][teamfeatures]

### WSL

- [Developing in WSL](https://code.visualstudio.com/docs/remote/wsl)

## Credits

Thanks to [dBildungscloud SRE Team](https://github.com/hpi-schul-cloud) for providing new features for the devcontainers.

[features]: https://containers.dev/features
[containerdevelopment]: https://code.visualstudio.com/docs/devcontainers/containers
[advancedcontainer]: https://code.visualstudio.com/remote/advancedcontainers/overview
[teamfeatures]: https://github.com/dBildungsplattform/infra-dcfeatures
