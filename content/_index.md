---
title: "Home"
hideLastModified: true
featuredTitle: "Why Use Trento"
featuredContent:
    1:
        image: "user-friendly@2x.png"
        title: "User Friendly"
        caption: "Trento is built with cutting-edge technology to be intuitive and easy to use. It provides just the right amount of information that is really needed at a glance."
    2:
        image: "discover-system-issues@2x.png"
        title: "Discover System Issues"
        caption: "It automatically discovers how an SAP system is structured and configured, and gives users a comprehensive overview of their entire SAP landscape."
    3:
        image: "prevent-downtime@2x.png"
        title: "Prevent Downtime"
        caption: "It is designed to help enterprise and integrator system administrators avoid common infrastructure problems that can result in delayed service implementations or unplanned downtime."
subFeatTitle: "Features"
subFeatContent:
    1:
        image: "monitoring@2x.png"
        title: "Monitoring"
        caption: "Trento integrates with a Prometheus backend and ad-hoc exporters to provide real-time metrics on business-critical SAP infrastructure. Unlike generic observability solutions, Trento provides contextual information that are peculiar to how SAP systems are structured."
    2:
        image: "continous-system-checks@2x.png"
        title: "System Configuration Checks"
        caption: "Trento features a bespoke configuration validation engine designed to promptly flag any non-compliant system configurations, aligning with SUSE's industry-leading best practices. SAP Architects can extend this engine by building additional system checks with a YAML-based Domain Specific Language."
    3:
        image: "flexible-apis@2x.png"
        title: "Flexible APIs"
        caption: "Powered by an API-driven design, all the data consumed via the web UI can also be leveraged by third-party systems via transparent, explicitly specified and documented integration interfaces."
    4:
        image: ""
        title: "And more..."
        caption: "Trento is still under active development and will be releasing more features in the upcoming months."
---

## How it Works
Trento is composed by two main parts, the Trento Server and Trento Agents. The Trento Server is further composed by a multi-tier web application and a background service, the Trento Checks Engine, codenamed _Wanda_.

You can run the Trento Server anywhere you want: we support Kubernetes-based container platforms via an Helm Chart, and provide also classic RPM packages that can be installed in traditional SUSE Linux Enterprise environments.

The Trento Agents are shipped with SUSE Linux Enterprise Server for SAP Applications, so they run within the workload that needs to be monitored. These needs to connect outbound to the Server.

![Trento Checks Engine](trento-checks-engine@2x.png)

## Get Started with Trento
Use Trento with you SAP Application server and improve the overall visibility and discovery of faults which are aligned to the SUSE SAP Best Practice Guidelines.

{{< button class="is-primary" link="/docs" alt="Start Reading the Trento Documentation" >}}Read Documentation{{< /button >}}
