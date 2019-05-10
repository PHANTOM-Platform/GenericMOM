# Description

The Multi-Objective Mapper (MOM) is responsible for optimising the mapping of components and shared data communications throughout the target architecture, towards user-defined non-functional requirements, while maintaining Quality of Service. MOM considers evolutionary/bio-inspired multi-objective optimization approaches in order to optimize the placement of components against multiple objectives such as power, performance (execution time, energy consumption, memory utilization but also data security), considering requirements/policies from application developers’ side, as well as the status and capabilities of computing resources.

MOM addresses the idea of multi-dimensional optimization in terms of optimizing against multiple objectives and targeting systems with increased heterogeneity (CPU, CPU-GPU, CPU-FPGA) across the computing continuum (from embedded to compute clusters) in full consistency with the PHANTOM Component-based Programming Model. MOM has been developed using Java Programming language and Eclipse platform as Integrated Development Environment, using appropriate XML libraries to be able to parse its input and produce its output. MOM is inspired by multi-objective optimization and bio-inspired paradigms.

# Deployment Guide

The uploaded version is a simplified version of the Multi-Objective Mapper. This version only supports the deployment of parallel applications on the CPU-based distributed hardware platforms.
If you are interested in the full version of this tool, please contact us as at info@wings-ict-solutions.eu

## System requirements
No specific operating system is required and nor any hardware requirements are specified.

#Configuration Guide

Along with the executable jar file, a configuration file (“configuration.xml”) is available for the user to change the following fields:
- configuration name="GenericMOM"
- login value="LOGIN"
- password value="MYPASSWORD"
- ipAddress value="IPADDRESS"
- targetPort target="Repository" value="PORTNUMBER1"
- targetPort target="ApplicationManager" value=" PORTNUMBER2"
- targetPort target="ExecutionManager" value=" PORTNUMBER3"
- subscription type="project" value="MYPROJECT1"
- filepath value = "description"
- source value = "PT"
- target value = "MOM"
- componentNetworkFileName value = "cpn.xml"
- hardwarePlatformFileName value = "hw.xml"
- mfserveraddress value = " IPADDRESS "

# Usage Guide

## Execution steps

**Run at terminal:**
1. cd path/to/jarfile/
2. java –jar MOM.jar -app “MOM_jar_file” -hw “component_network_XML file” -NMAP 10 -iMAP init_deployment.xml --online

**Arguments:**
-jar “MOM_jar_file”: indicating the name of MOM’s executable jar file. Mandatory argument.
-app “component_network_XML file”: indicating the name of the component network XML file. Mandatory argument when MOM does not access the remote repository.
-hw “hardware_platform_XML file”: indicating the name of the hardware platform XML file. Mandatory argument when MOM does not access the remote repository.
-NMAP “number”: indicating the number of the generated deployment plan population per MOM’s genetic algorithm’s iteration. Optional argument.
-iMAP “deployment_plan_XML file”: indicating the name of the initial deployment plan XML file. Optional argument.
--manualData: flag which indicates MOM to use metrics provided by the user and not by the Monitoring Server or the MBT. Optional argument.
--online: flag which indicates MOM to access the remote repository as it is configured in the configuration file (see Prerequisite files below). Optional argument.
-project “project_name”: indicating the specific target project name, overriding the projects subscribed in the configuration file. Optional argument.

## Results
The generated mappings are uploaded to the Repository for the Deployment Manager to use them.

## Coordination with other components (online mode)
The integration between the PHANTOM components is being coordinated by the Application Manager, Execution Manager and the Repository servers. Thus, any integration aspects refer to the communication of the components via the use of the functionalities provided by these servers.

### Multi-Objective Mapper
In specific, the MOM expects the Code Analysis part of the PT to be completed before it continues with its execution. So, the PT is responsible to inform the Application Manager about the end of its execution so that MOM can be initiated. Similarly, the Technique Selection expects a notification from the MOM (through the Application Manager) in order to continue with its execution.

### Repository
During execution (online mode), there are a lot of interactions with the Repository, for downloading and uploading files.






