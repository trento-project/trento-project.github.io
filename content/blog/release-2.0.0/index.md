---
title: "Announcing Trento Version 2.0.0"
date: 2023-05-04T16:21:00+02:00
hideLastModified: false
showInMenu: false
summary: "Available beginning of May’23, Trento 2.0.0 brings major changes to the architecture of the solution..."
summaryImage: "trento-2-0-0-thumbnail@2x.png"
author: "Alberto Bravo"
---
![Trento Release Version 2.0.0](trento-release-2-0-0-hero@2x.png)

Available beginning of May’23, Trento 2.0.0 brings major changes to the architecture of the solution and therefore it will be **necessary an update on both the server** and the agents for those customers that are already using Trento. 

The main change in the new version is a brand-new SSH-less checks engine, but it also adds VMware to the list of known platforms and provides versioned external APIs for both the web and engine components.

# SSH-less Checks Engine

![Trento Checks Engine](trento-checks-engine@2x.png)

The old engine required an SSH connection from the server to the cluster nodes to execute the checks, which were nothing but Ansible playbooks. With the new Checks Engine, the SSH connection is no longer necessary, which **massively improves the security and performance** of the entire system. Moving forward there will be only one secured, outbound communication channel from the agent host to the server and there will be no need to maintain an SSH key specific for Trento, nor an SSH user with elevated access to execute the Ansible playbooks.

In the new Checks Engine, internally nicknamed _Wanda_, the execution of a check is split in two stages. On the client side, the Trento Agent is responsible for collecting the required data: we call this _fact gathering_. The _facts_ are sent by the Agent to the _Wanda_ server component, which in turn performs the evaluation of the _expectations_ about these facts. This division of responsibilities translates in a reduced footprint on SAP hosts and a much better performance.

The new checks engine comes with a new Domain Specific Language where checks are represented by YAML files with a human readable structure, specifically tailored around the needs of SAP architects and experts, to provide them with a framework to add new configuration validation logic with ease and extend our existing catalog of checks at will.

```yaml
## Check YAML (Domain Specific Language) Example
id: "156F64"
name: Check Corosync token_timeout value
group: Corosync
description: |
  Corosync `token` timeout is set to expected value
remediation: |
  ## Abstract
  The value of the Corosync `token` timeout is not set as recommended.

  ## Remediation
  Adjust the corosync `token` timeout as recommended on the best practices, and reload the corosync configuration...

  ## References...

facts:
  - name: corosync_token_timeout
    gatherer: corosync.conf
    argument: totem.token

values:
  - name: expected_token_timeout
    default: 5000
    conditions:
      - value: 30000
        when: env.provider == "azure" || env.provider == "aws"
      - value: 20000
        when: env.provider == "gcp"

expectations:
  - name: token_timeout
    expect: facts.corosync_token_timeout == values.expected_token_timeout
```

You can read the full specification of this DSL in our [guides](https://github.com/trento-project/wanda/blob/main/guides/specification.md).

In addition to these immediate improvements, the new Checks Engine is also the gateway to the following **up-coming features**:
* Configuration checks for other HA scenarios (ASCS/ERS, Cost Optimized, Scale-Out).
* Configuration checks for other targets (hosts, HANA databases and NetWeaver instances).
* Checks customization overriding values from best practices with custom values proven to work better in the customer particular setup.
* Addition of custom checks by customers and partners to cover areas of the SAP environment beyond Trento scope.

# VMware Discovery

Trento 2.0.0 adds VMware to the list of known platforms, along with Azure, AWS, GCP and on-premise bare metal. With this addition, most customers running SAP systems on SUSE Linux Enterprise Server for SAP are represented in Trento.

![Trento VMware Discovery](trento-vmware-discovery@2x.png)

# Versioned APIs

Last but not least, both the web and the engine components are now available with a set of versioned public APIs which ultimate goal is to facilitate the integration of Trento with other monitoring tools. With these APIs you can essentially retrieve any information currently displayed in the console, like a list of the registered SAP systems or the status of the node exporter in any given host, and perform any available actions, like selecting and executing checks or setting and removing tags.

For the browseable OpenAPI specification ouf our APIs, please refer to:
* https://www.trento-project.io/web/swaggerui/
* https://www.trento-project.io/wanda/swaggerui/

![Trento External APIs](trento-external-api@2x.png)

# Are you wanting to upgrade or try out Trento?
Follow the [instructions in our documentation](https://documentation.suse.com/sles-sap/trento/single-html/SLES-SAP-trento/index.html "Getting started with Trento Premium") to get started.
