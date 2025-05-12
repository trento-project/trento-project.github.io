---
title: "Announcing Trento Version 2.5"
date: 2025-04-25T10:30:00+02:00
hideLastModified: false
showInMenu: false
summary: "Trento 2.5 closes a first development cycle focused on observability and compliance."
summaryImage: "trento-2-5-thumbnail@2x.png"
author: "Alberto Bravo"
aliases: [ "release-2.5.0" ]
---

Trento 2.5 closes a first development cycle focused on observability and compliance. Stay tuned for a new major version of Trento with the first operation use cases! Coming soon.

# Discovery of Hana Scale-up Cost Optimized Clusters
With the discovery of HANA scale-up cost optimized clusters, along with the corresponding configuration checks, Trento delivers on coverage of the most important HA pacemaker-based scenarios for SAP workloads on SLES for SAP. 

![Cluster Detail for Hana Cost Optimized Scenario](discovery-of-hana-cost-optimized-clusters@2x.png)

# Checks Customization
The new version of Trento provides a more flexible Checks Catalog by allowing customers to customize checks in situations where there is a justified reason to depart from our Best Practices.

![Check Settings with Checks Customization](checks-customization@2x.png)

# Enhanced Activity Log
The activity log, which is the central point where users can review past actions and events, gets reinforced with the introduction of important enhancements such as search by metadata, auto refresh capabilities, severity information and permission-based access level.

![Activity Log with Enhancements](enhanced-activity-log@2x.png)

# More Flexible Prometheus Integration
In this new version, the IP address and the port that the node exporter is listening to can be specified in the corresponding agent configuration file, hence ensuring that the communication from Prometheus server to the node exporter works fine.

![Terminal with Prometheus Integration Message](more-flexible-prometheus-intergration@2x.png)

# Discovery Optimization in Edge-Case Scenarios
Based on direct customer feedback, the new Trento version improves the discovery behavior in not supported or not recommended scenarios. For example, pacemaker clusters combining HANA and ASCS/ERS resources or not managed instances running on cluster nodes.

# Are you wanting to upgrade or try out Trento?
Follow the [instructions in our documentation](https://documentation.suse.com/sles-sap/trento/single-html/SLES-SAP-trento/index.html "Getting started with Trento Premium") to get started.
