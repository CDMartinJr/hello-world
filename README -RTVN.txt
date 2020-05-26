## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/CDMartinJr/hello-world/blob/master/RedTeamDiagram.png (Red Team Network)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  -https://github.com/CDMartinJr/hello-world/blob/master/install-elk.yml.txt 

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting unwanted access to the network.
- By using load balancers, networks can more evenly distribute traffic between different servers, thus helping to prevent any single
  server from becoming overwhelmed.  The jump box, on the other hand, allows for remote access into the network, but itself remains 
  secure with very limited internet access.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system logs.
- Filebeat monitors and compiles log events
- Metricbeat records metrics and statistics from the OS and other services running on a network

The configuration details of each machine may be found below.
_Note: Use the Markdown Table Generator (http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.1.4   | Linux            |
| DVWA-VM1 | Docker   | 10.0.1.5   | Linux            |
| DVWA-VM2 |Redundancy| 10.0.1.6   | Linux            |
| DVWA-VM3 |Redundancy| 10.0.1.8   | Linux            |
| DVWA-VM4 |Redundancy| 10.0.1.9   | Linux            |
| ELK-STACK|ELK/Docker| 10.0.1.10  | Linux            |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Dynamic IPV4 Address

Machines within the network can only be accessed by the ansible within the Jump Box.
- Jump Box runs off of a dynamic public address, but its private address is 10.0.1.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |    Yes              |    Local Machine     |
| VM1      |    No               |      10.0.1.4        |
| VM2      |    No               |      10.0.1.4        |
| VM3      |    No               |      10.0.1.4        |
| VM4      |    No               |      10.0.1.4        |
| ELK      |    No               |      10.0.1.4        |  



### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because
as the network needs grow, rather than individually configure each machine, the machines can all be configured/reconfigured within 
minutes.

The playbook implements the following tasks:
- installs Docker and Python
- downloads Docker container sebp/elk
- configures necessary ports
- starts the container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/CDMartinJr/hello-world/blob/master/Screenshot%20(17).png (Docker ps output)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.1.5 
- 10.0.1.6
- 10.0.1.8 
- 10.0.1.9

We have installed the following Beats on these machines:
- filebeats
- metricbeats

These Beats allow us to collect the following information from each machine:
- Metricbeats collects metrics and statistics from a wide variety of services, includinf Nginx and 
  MySQL. Filebeats examines log files - such as Apache log files - for pre-specified data types.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming 
you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to /etc/ansible/.
- Update the /etc/ansible/hosts file to include the ELK-Stack server in the [elkservers] group (this group must be added).
- Run the playbook, and navigate to <private-elk ip address>:5601 to check that the installation worked as expected.

##Filebeat
Below you will find the filebeat-playbook as well.

-https://github.com/CDMartinJr/hello-world/blob/master/filebeat_playbook.txt
