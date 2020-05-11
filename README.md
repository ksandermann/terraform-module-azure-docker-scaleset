# Terraform module azure-docker-scaleset
Terraform module to deploy a highly available linux scaleset running stateless docker images using docker-compose,
placed behind an Azure Loadbalancer.
Input parameters are the docker-compose file which should be used as well as, optionally, configuration files to mount 
into the containers.

The highly-available setup includes:
1. A zone-redudant scaleset behind a zone-redudant loadbalancer
1. Healthchecks of the containers
1. Automatic OS-upgrades
1. Automatic instance repair
1. Autoscaling based on CPU metric

# Prerequisites
1. Resource Groups for the loadbalancer and the scaleset. Can be the same.
1. A VNET to place both the loadbalancer and the scaleset.
1. Subnets for the loadbalancer and the scaleset. Can be the same.
1. Connectivity on the configured routes between the used subnets. Both NSGs and routes have to be configured, if applicable.
1. A Public SSH key for the scaleset admin user.
1. *Optional*: If you choose to opt-in for boot diagnostics for the scaleset, an appropriate storage account is needed.

# Example usage
An exemplary workspace calling this module can be found [here](https://github.com/ksandermann/terraform-workspace-examples/tree/master/azure-docker-scaleset)
