## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible file may be used to install only certain pieces of it, such as Filebeat.

  - [Install ELK Ansible](install-elk.yml)
  - [Ansible Playbook Filebeat](filebeat-playbook.yml)
  - [Ansible Playbook Metricbeat](metricbeat-playbook.yml)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Damn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting unauthorized access to the network.
- _What aspect of security do load balancers protect? What is the advantage of a jump box?
	* Load balancers distribute traffic across multiple servers, whether it is network or application traffic. This traffic distribution defends against DDoS attacks.
	* A jump box is the hardened internet-facing server, which prevents virtual machines within its network from exposure to the public. This becomes the remote entry point to the rest of the virtual machines on the network, meaning all admins must connect through this machine prior to performing other network tasks. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system system traffic.
- Filebeat watches for log files and their location, and sends this information to Logstash or Elasticsearch to be indexed.
- Metricbeat monitors machine/service metrics.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway/Ansible  | 10.0.0.4   | Linux (ubuntu 18.04)           |
| Web-1    | Docker-DVMA  | 10.0.0.5   | Linux (ubuntu 18.04)           |
| Web-2    | Docker-DVMA | 10.0.0.6   | Linux   (ubuntu 18.04)         |
| Web-3    | Docker-DVMA  | 10.0.0.7   | Linux   (ubuntu 18.04)         |
| ELK      |ELK Server    | 10.2.0.4   | Linux   (ubuntu 18.04)         |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 75.168.90.239 (Personal IP Address) 

Machines within the network can only be accessed by the Jump Box, IP 10.0.0.4.
- Which machine did you allow to access your ELK VM? What was its IP address?
	* Only the Jump Box (IP 10.0.0.4) can access the ELK VM. However, the security is configured to allow TCP traffic to the ELK Server from Personal IP


A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | Personal IP          |
| Web-1    | No                  | 10.0.0.4             |
| Web-2    | No                  | 10.0.0.4             |
| Web-3    | No                  | 10.0.0.4             |
| Elk      | No                  | Personal IP, 10.0.0.4|

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- you are able to manage configuration and deploy to several servers at once, all from the command line after initial playbook configuration. This makes the task of configuration not only extremely efficient, but also greatly reduces human error induced configuration variability between servers. 

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Installs these services:
	* docker.io
	* python3-pip
	* docker (python pip module)
- Increases memory via systemctl, setting the value to '262144'
- Downloads and launches elk container and maps to these ports: 5601, 9200, 5044 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![docker ps output](Images/docker_ps_output.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._