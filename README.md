# Azure-Ansible-ELKStack-Project-1
Project 1 README 
The files in this repository were used to configure the network depicted below.

https://drive.google.com/file/d/1_c_89ebYV7noHcIhEfzs9yT36h-YDa7G/view?usp=sharing

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the README file may be used to install only certain pieces of it, such as Filebeat.

### Link to Elk Playbook
https://github.com/Rutroh87/Azure-Ansible-Project-1/blob/main/install-elk.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
- Beats in Use
- Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly Available, in addition to restricting access to the network.

 What is the advantage of a jump box?
 
A jump box is a secure computer that all admins first connect to before launching any administrative task or use as an origination point to connect to other servers or untrusted environments

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system configurations.

File beat - is a lightweight shipper for forwarding and centralizing log data. Installed as an agent on your servers, File beat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash.

Metric beat - is a lightweight shipper that you can install on the servers to periodically collect metrics from the operating system and from services running on the server. Metricbeat takes the metrics and statistics that it collects and sends them to the output that you specify, such as Elasticsearch or Logstash.

(NOTE) 
MetricBeat - Custom magnifying glass to your standards -- Circumstantial-- You must ask yourself, what is a normal Baseline in my enviroment?

The configuration details of each machine may be found below.

| Name     | Function          |IP Address |        Operating System        |
|----------|-------------------|-----------|--------------------------------|
| Jump Box / Ansible | Gateway |10.0.0.10 / Public IP| Linux Ubuntu 18.04   |
| Web 1    | Website DVWA      |10.0.0.6   |       Linux Ubuntu  18.04      |
| Web 2    | Website DVWA      |10.0.0.8   |       Linux Ubuntu  18.04      |                  
| Web 3    | Website DVWA      |10.0.0.12  |       Linux Ubuntu  18.04      |         
| ELKSTACK | Kibana / Elastic  |10.1.0.4   |       Linux Ubuntu  18.04      |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 
Only the jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

- 10.0.0.10 (EX) JumpstartProvisoner Private IP
- 51.143.119.53 (EX) Load Balancer 

Machines within the network can only be accessed by JumpBox - Internal IP ADDRESS 10.0.0.10 

- JumpBox Provisioner / Ansible 

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses       |
|----------|---------------------|----------------------------|
| Jump Box |   YES/NO            | 45.49.0.78 \ 10.0.0.10     |
| Web 1    |   NO                | 10.0.0.10  \               |
| Web 2    |   NO                | 10.0.0.10  \               |
| Web 3    |   NO                | 10.0.0.10  \               | 
| ELKStack |   YES/NO            | 10.0.0.10  \ Public IP     |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

- Playbooks...these little YAML books allow anyone to run a list of important commands to install tools and containers. A pro is the ability to configure and manage such containers with playbooks...the downside however is that you must double check YAML configurations files to make sure there are NO SYNTAX ERRORS and all must be formatted correctly...if one thing is off, the whole playbook will NOT WORK PROPERLY.  

The playbook implements the following tasks:

- Install Apache httpd
- Configure memory
- Install docker.io 
- Install python3-pip
- Install docker using pip
- Install ELK

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/Rutroh87/Azure-Ansible-Project-1/blob/main/docker_ps_output.png.png


### Target Machines & Beats
This ELK server is configured to monitor the following machines:

- Web 1
- Web 2
- Web 3
- JumpBox

We have installed the following Beats on these machines:

- Web 1 
- Web 2
- Web 3

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:

- Copy the Metricbeat and Filebeat configuration files to the Ansible Container.

- Update and allow the files to include your IP addresses and other recommended settings given by Kibana 

- Run the playbook, and navigate to the Elk Stack Virtual Machine to check that the installation worked as expected.

- Navigate to this site with your virtual machine's ip address to check that the ELK Server is running.

- http:/<your ip>/app/kibana 

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
