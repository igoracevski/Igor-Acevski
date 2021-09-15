# Igor-Acevski
Home Work Elk Stack Project Homework
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://drive.google.com/file/d/1Z9iwv_a3-cZ2UoDFMgv04-DwDfXO54dK/view?usp=sharing

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the __yaml___ file may be used to install only certain pieces of it, such as Filebeat.

https://drive.google.com/file/d/1RS5l7dxLAAI-NCtczjixezo1LiZyfFoN/view?usp=sharing

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _redundancy_, in addition to restricting __traffic___ to the network.

--The load balancer is here to redirect the traffic on through web servers. In addition to avoid DDOs attack.

--The advantage of Jump Box that you are creating a vMachine so you can manage the systems and the security to your network or systems.


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the __Logs___ and system __Traffic___.
-What does Filebeat watch for? Monitors the log files or a specific location.
-What does Metricbeat record? Monitors the performance of the systems. 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.







| Name       | Function | IP Address | Operating System |
|------------|----------|------------|------------------|
| Jump Box   | Gateway  | 10.0.0.8   | Linux            |
| Web1       |Webserver1| 10.0.0.5   | Linux            |
| Web2       |Webserver2| 10.0.0.7   | Linux            |
|Elk Server  | Elk Stack| 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _Jump Box_ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- My Personal Public IP

Machines within the network can only be accessed by Ansible Jump Box Machine.
-Which machine did you allow to access your ELK VM? What was its IP address? Only the Jump Box can access to the Elk VM with the IP 10.0.0.8

A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible | Allowed IP Addresses |
|------------|---------------------|----------------------|
| Jump Box   | No                  |My personal IP        |
| Web1       | No                  | 10.0.0.8             |
| Web2       | No                  | 10.0.0.8             |
|Elk Server  | Yes                 |My per.IP and 10.0.0.8|



### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
-What is the main advantage of automating configuration with Ansible? To save time by automating all machines at ones. Setup all machines with one ansible playbook that loads ips of the machines. 						

The playbook implements the following tasks:
-In 3-5 bullets, explain the steps of the ELK installation play. 
E.g., install Docker; download image; etc._

- Installing the docker.
- Installing the Phyton3.
- Install docker module.
- Increase virtual memory.
- Download and lunch docker elk.


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://drive.google.com/file/d/1ZsXvhw6junCW95mgeonYC0iudkwFBJlN/view?usp=sharing



### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web1 10.0.0.5
- Web2 10.0.0.7

We have installed the following Beats on these machines:
- File beat
- Metri cbeats 

These Beats allow us to collect the following information from each machine:
- Filebeat monitors the files or locations that we specify, what changes and messages the files, 
- Metricbeat record and metric statistics from systems and services on servers.
 
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _ansible.cfg_ file to _/etc/ansible_.
- Update the _host_ file to include...
- Run the playbook, and navigate to _Kibana web site_ to check that the installation worked as expected.

- Answer the following questions to fill in the blanks:
- Which file is the playbook? Where do you copy it?
   -The files that have .yml extension. And is copied to the Virtual machines that are installed by the ansible.

- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
 -This is the host file. And you need to separate machines by ips and groups. 
Example: 
[webservers]
10.0.0.5 ansible_python_interpreter=/usr/bin/python3
10.0.0.7 ansible_python_interpreter=/usr/bin/python3

[elk]
10.1.0.4 ansible_python_interpreter=/usr/bin/python3 


- _Which URL do you navigate to in order to check that the ELK server is running?
  -You will need to navigate to the public IP from the Elk server through the specified port
 Example:
http://40.71.62.248:5601/app/kibana# 

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

To download: curl -L -O
To install:  dpkg -i
To setup:    filebeat setup
To enable module: filebeat modules enable system
To start service: service filebeat start
