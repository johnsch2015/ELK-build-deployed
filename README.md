The files in this repository were used to configure the network depicted below.

Diagrams/Complete Network Diagram Including ELK.png)

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
- Which machine did you allow to access your ELK VM? What was its IP address? Jump Box provisioner VM only has access to ELK VM with local ip via docker attach.

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
      
- Ansible/Install-elk.yml.txt. https://github.com/johnsch2015/project1/blob/57261510895db8956d383120b1dfc95eb85b88a9/Ansible/Install-elk.yml.txt

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

snips/sudo docker ps.PNG

https://github.com/johnsch2015/project1/raw/main/snips/sudo%20docker%20ps.PNG


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- List the IP addresses of the machines you are monitoring_
10.0.0.8, 10.0.0.6
We have installed the following Beats on these machines:
- Filebeat-7.4.0-amd64.deb, Metricbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____ file.
- Update the configuration file to include ELK machine IP address.
- Run the playbook, and navigate to docker container list to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- Which file is the playbook? Where do you copy it?_Copy to /etc/ansible folder
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?
