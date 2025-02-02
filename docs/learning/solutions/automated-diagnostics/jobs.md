## Automated Diagnostics
### Prebuilt Jobs

Jobs are arranged in Job Groups (folders) based on their purpose or related technology.

:::tip Note
Many of these Jobs depend on a method of sending of commands to remote-nodes (such as EC2's). 
Follow the SSM Tour outlined in the [Tours section](/learning/solutions/automated-diagnostics/tours) to use Systems Manager, or install an [Enterprise Runner](/administration/runner/) for SSH so that Runbook Automation can send commands to the remote-nodes.  
:::

**AWS**: Gather diagnostic data from your own AWS environment, including EC2, ECS, ELB, RDS and VPCs. These Jobs do _not_ require an [Enterprise Runner](/administration/runner/)  or an integration with Systems Manager.

**Kubernetes**:  Describe your Kubernetes objects, run commands against Pods and gather logs.

**Linux**: Retrieve Syslog messages and service statuses as well as top processes large files.

**Nginx**: Test your Nginx configuration, retrieve logs and curl an endpoint.

**PostgreSQL**: Test your PostgreSQL server and tail its logs.

**Redis**: Check listening port, test latency, retrieve memory stats and return slow log entries.

**Validate Integrations** Checks whether the credentials provided for the specified integration (such as AWS or PagerDuty) successfully connect and authenticate.

### How to Use the Node Filter Job Option
All Jobs that send commands to a remote-node have a predefined Node Filter set to `{$option.node_filter}`:

![Node Filter](@assets/img/solutions-auto-diag-node-filter.png)<br>

This is so that target-nodes can be specified in the Job invocations from [**PagerDuty Automation Actions**](https://www.pagerduty.com/platform/automation/actions/) - as described in the next section of this Solution Guide.

#### Target Specific Nodes
To target specific Nodes for the prebuilt Jobs within the Runbook Automation Interface:

1. Select **`Change the Target Nodes`**
2. Click the dropdown to the left of **`${option.node_filter}`**
3. Click on **Show all nodes**
![Change Nodes](@assets/img/solutions-auto-diag-change-nodes.png)<br><br>
4. Click on an individual Node, and click the small **Arrow** to the right of the Node Name:
![Select Node](@assets/img/solutions-auto-diag-select-node.png)<br>

This will allow you to target the _individual_ node selected.  If you want to target multiple Nodes, see the [Node Filter Documentation](/manual/11-node-filters).

### **With the Prebuilt Jobs, you can [<span style="color:green"><ins>integrate with Automation Actions!</ins></span>](/learning/solutions/automated-diagnostics/automation-actions.html)**