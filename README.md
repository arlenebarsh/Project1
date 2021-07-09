### ELK-Stack Project

The files in this repository were used to configure the network depicted below.

![Diagram](https://github.com/arlenebarsh/Project1/blob/main/Diagrams/Network_Topology.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

(Ansible/install_elk_yml)

This document contains the following details:

Description of the Topologu
Access Policies
ELK Configuration
Beats in Use
Machines Being Monitored
How to Use the Ansible Build
Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting unauthorized accesss to the network. Load balancers are an important security tool because they can severly help mitigate a DDos attack. Jump boxes are usefull because they provide an all in one access point for administrative tasks. JumpBoxes can be considered a SAW, Secure Admin Worstation, which would require an administrator to access the JumpBox before accesssing the servers.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.

Filebeat watches for log files/locations and collects events related to those files and locations.
Metricbeat records metrics and statistical data from the operating system and services that are running on the server.
The configuration details of each machine may be found below.

Name	Function	IP Address	Operating System
Jump Box	Gateway	10.0.0.4	Linux
Web-1	Web Server	10.0.0.6	Linux
Web-2	Web Server	10.0.0.5	Linux
ELK Stack	ELK Stack	10.1.0.4	Linux
Access Policies
The machines on the internal network are not exposed to the public Internet.

Only the JumpBox Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 1. My personal IP Address.

Machines within the network can only be accessed by SSH. 1. The ELK Server is only accessible by SSH from the JumpBox.

A summary of the access policies in place can be found in the table below.

Name	Publicly Accessible	Allowed IP Addresses
Jump Box	Yes/No	My personal IP Address
Web-1	No	10.0.0.4
Web-2	No	10.0.0.4
ELK-Server	No	10.0.0.4
Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

The main advantage of automating the installation process is that you can deploy multiple servers quickly and easily without having to manually configure each server.
The playbook implements the following tasks:

Configures the machine with Docker.
Installs Docker.io and pip3.
Downloads and configures ELK docker container.
Activates ports 5601, 9200, and 5044.
The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.

Target Machines & Beats
This ELK server is configured to monitor the following machines:

Web-1 10.0.0.6
Web-2 10.0.0.5
We have installed the following Beats on these machines:

Filebeat
Metricbeat
These Beats allow us to collect the following information from each machine:

Filebeat watches for log files/locations and collects events related to those files and locations.
Metricbeat records metrics and statistical data from the operating system and services that are running on the server.
Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:

Copy the install_elk_yml file to your /etc/ansible directory.
Update the host file to include the IP Addresses of your Web-1, Web-2, and ELK server as well as assign python3 as the interpreter.
Run the playbook, and navigate to your ELK server to check that the installation worked as expected.
Navigate to http://publicip(elkserver):5601 to check that the installation worked as expected.
