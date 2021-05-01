# *Project 1 Repository* *Azure Elk Deployment*



The files in this repository were used to configure the network depicted below.

Diagrams/Complete Network Diagram Including ELK.png
https://github.com/johnsch2015/project1/blob/main/Diagrams/Complete%20Network%20Diagram%20Including%20ELK.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ansible file may be used to install only certain pieces of it, such as Filebeat.


This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting vulnerabilities to the network.
- Load balancers protect server data and a jump box helps to shield the other VMs. It also may serve as a docker point of entry.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the traffic and system logs.
- Filebeat watches out for and collects log events.
- Metricbeat takes metrics and statistics and collects them for output.

The configuration details of each machine may be found below.

| Name     | Function  | IP Address | Operating System |
|----------|-----------|------------|------------------|
|Jump Box  | Gateway   |13.64.244.94| Linux            |
| Web-3    |web server |10.0.0.8    | Linux            |
| Web-4    |web server |10.0.0.6    | Linux            |
|Elk-to-Red|ELK server |10.1.1.4    | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- My personal IP

Machines within the network can only be accessed by other machines on the network
- Jump Box provisioner VM only has access to ELK VM with local ip via docker attach.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | Personal IP          |
|    Web-3 | No                  | Local VM IPs         |
|    Web-4 | No                  | Local VM IPs         |                      

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it decreases the chance of human error and is efficient.

The playbook implements the following tasks:
- Install docker.io
- Install python3.pip
- Install Docker module
- Increase virtual memory
- Use more memory
- download and launch a docker elk container
- Enable service docker on boot
  
Ansible/Install-elk.yml.txt. https://github.com/johnsch2015/project1/blob/57261510895db8956d383120b1dfc95eb85b88a9/Ansible/Install-elk.yml.txt

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

snips/sudo docker ps.PNG

https://github.com/johnsch2015/project1/raw/main/snips/sudo%20docker%20ps.PNG


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- List of monitored IPs
10.0.0.8, 10.0.0.6
We have installed the following Beats on these machines:
- Filebeat-7.4.0-amd64.deb, Metricbeat
These Beats allow us to collect the following information from each machine: Filebeat collects the log files, locations specified regarding traffic. Metricbeat collects metric and statistical information. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the appropriate configuration file (originally modified from pentest.yml) to local ansible container. For example, ELK, filebeat, metricbeat locations.
- Update the hosts and config files to include the internal webserver IP addresses.
- Run the playbook, and navigate to docker container list to check that the installation worked as expected.

- For ELK, the Install-elk is the playbook and the filebeat and metricbeat both are clearly labeled. Copy to /etc/ansible folder in the ansible container and on each web vm.
- Update the ansible config file to make ansible run the playbook on a specific machine (i.e. filebeat-playbook.yml). ELK will install from the provisioner attach to the container created. There are two configuration files to edit and one will say Intall-elk, filebeat, and metricbeat. Each will have to be edited, run on each vm with the appropriate IP addresses and configuration.
- Make sure the ELK server is running by going to http://[your.VM.IP]:5601/app/kibana. This would be the IP address that was added to the config file.
