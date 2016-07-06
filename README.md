# TOSCA Based Deployment and Monitoring of Clearwater vIMS
This repository contains a [Cloudify](http://getcloudify.org) blueprint for deploying MetaSwitch Clearwater vIMS Cloudify, a TOSCA based VNF Orchestrator and policy engine.
[This video](https://youtu.be/ZsT78d1BR5s) shows how the bluerint is used for deployment, configuration, monitoring and healing/scalingof Clearwater. 

## Repository Contents
This repository includes the following:

1. A TOSCA blueprints to deploy Clearwater on OpenStack (`clearwater51.yaml`) and VMWare vCloud Director (`clearwater-vcloud.yaml`) including relationships and dependencies between the various Clearwater componentsare
2. A DNS plugin to point each node (Bono, Ellis, Homer, Homestead, Sprout and Ralf) to the deployed DNS
3. Scripts to install the application stack on each node


The blueprint supports healing, e.g you can kill Bono and as a result a new VM would be instantiated and the Bono application stack will be installed on it. The relationships to other nodes will make sure that these nodes are also wired properly with the newly created Bono VM. 

## Using the Blueprint
#### Step 0 
[Install the Cloudify CLI](http://docs.getcloudify.org/3.4.0/intro/installation/) and [bootstrap a Cloudify manager](http://docs.getcloudify.org/3.4.0/manager/bootstrapping/).

#### Step 1
Upload the blueprint to the manager, create a deployment and invoke `install` workflow using the following command:
```
cfy install -p clearwater51.yaml
```

#### Uninstalling
To uninstall and delete the running deployment and delete created blueprint, invoke the `uninstall` workflow:
```
cfy uninstall -d deployment_name
```


The following picture shows a running deployment example as it appears in the GUI
![alt text](https://github.com/cloudify-examples/clearwater-scripts-plugin-blueprint/blob/master/yaml/images/Clearwater.jpg "ClearWater Deployment")

