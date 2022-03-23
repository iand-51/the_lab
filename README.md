# the_lab
A place to experiment and tinker
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![alt text](https://github.com/iand-51/the_lab/blob/52275bf45c6b0b0943c95468d51040087aef984d/Diagrams/Azure%20diagram%201.drawio.png?raw=true)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML/playbook file may be used to install only certain pieces of it, such as Filebeat.

install-elk.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file system and system logs.

The configuration details of each machine may be found below.

| Name     | Function        | IP Address | Operating System |
|----------|-----------------|------------|------------------|
| Jump Box | Gateway         | 10.0.0.4   | Ubuntu 18.04     |
| Web-1    | Virtual Machine | 10.0.0.5   | Ubuntu 18.04     |
| Web-2    | Virtual Machine | 10.0.0.6   | Ubuntu 18.04     |
| Web-3    | Virtual Machine | 10.0.0.7   | Ubuntu 18.04     |
| ELK2     | ELK Server      | 10.1.0.5   | Ubuntu 18.04     |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the "Jump-Box-Provisioner" can accept connections from the Internet. Access to this machine is only allowed from whitelisted IP addresses with a registered public SSH key. 


Machines within the network can only be accessed by SSH connections originating from the docker container running on the "Jump-Box-Provisioner" machine. 

A summary of the access policies in place can be found in the table below.

| Name     | Function        | IP Address | Operating System |
|----------|-----------------|------------|------------------|
| Jump Box | Gateway         | 10.0.0.4   | Ubuntu 18.04     |
| Web-1    | Virtual Machine | 10.0.0.5   | Ubuntu 18.04     |
| Web-2    | Virtual Machine | 10.0.0.6   | Ubuntu 18.04     |
| Web-3    | Virtual Machine | 10.0.0.7   | Ubuntu 18.04     |
| ELK2     | ELK Server      | 10.1.0.5   | Ubuntu 18.04     |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which increases efficency by implementing a repeatable "one to many" solution, and reduces errors once the configuration has been tested and proven to execute as intended.  

The playbook implements the following tasks:
In order for the ELK stack to run correctly, we first need to tell the virtual machine to allocate enough RAM in order to be able to generate and send the logs in question to the ELK server. After that, a docker container is downloaded and launched from the docker website/repository 
and configured to start everytime the container is initialized. The necessary complementing packages and plugins are also installed so that the machine has the proper resources for reporting in play. 

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
10.0.0.5,10.0.0.6,10.0.0.7

We have installed the following Beats on these machines:
Metricbeat, Filebeat

These Beats allow us to collect the following information from each machine:
Filebeat tracks deltas in the file system, such as if a user tries to elevate or escalate user privileges. Metricbeat collects telemetry data from the machine in question.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node configured: 

SSH into the control node and follow the steps below:
- Copy the playbook file to the /etc/ansible directory on the docker container.
- Update the configuration and playbook files to include the relevant IP addresses where the playbook should apply to/ where the logs will be generated from and delivered to 
- Run the playbook, and navigate to the Kibana dashboard/portal in a web browser to check that the installation worked as expected.

