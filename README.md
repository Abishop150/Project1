## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://drive.google.com/file/d/1hEdn_DRiJQMiIwX66eWW1IYPgYvxjAQI/view?usp=sharing

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  	playbook-filebeat.yml
	playbook-metricbeat.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly robust, in addition to restricting access to the network.
What aspect of security do load balancers protect? What is the advantage of a jump box? 
The load balancer protects the network from attackers that are trying to overload it, it spreads the traffic out to different areas to balance the load, hence the name. The advantage of having a jumpbox is that it is a single unit that has outside access that is easily monitored.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
What does Filebeat watch for? 
Filebeat is to watch system logs and send the logs to a host to record
What does Metricbeat record? 
Metricbeat records the metrics and stats from webservers to help monitor the traffic

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| EKL	   | Server   | 10.1.0.4   | Linux	      |
| WEB1 	   | Webserver| 10.0.0.9   | Linux            |
| WEB2     | Webserver| 10.0.0.10  | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
My personal IP

Machines within the network can only be accessed by the Jumpbox by running the ansible container.
Which machine did you allow to access your ELK VM? What was its IP address? 
Jumpbox using ansible, 10.0.0.4 private IP, 40.121.56.40 public IP

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible| Allowed IP Addresses  |
|----------|--------------------|-----------------------|
| Jump Box |Yes			|My personal IP		|
| Web 1	   |No			|Private IP 10.0.0.4	|
| Web 2	   |No			|Private IP 10.0.0.4	|
| ELK	   |Yes/No		|Private IP 10.0.0.4/Kibana|	   


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
What is the main advantage of automating configuration with Ansible? 
Automating the configuration of ansible is easy and allows you to customize everything, making sure it is exactly what you need

The playbook implements the following tasks:
In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ... Install Docker.io
- ... Install Pip3
- ... Install ansible docker
- ... increase the cirtual memory
- ... download and install the final docker

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
README\Images\DockerPS_SC

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
List the IP addresses of the machines you are monitoring: 
Web1 private IP 10.0.0.9, Web2 private IP 10.0.0.10

We have installed the following Beats on these machines:
Specify which Beats you successfully installed: 
We installed filebeats and metricbeats

These Beats allow us to collect the following information from each machine:
In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc.: 
Filebeat is used as a monitoring system that logs files and sends the data to a processing software
Metricbeat collects metrics and stats and sends them to be viewed, it helps monitor connections to the network and the running systems

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat config file to /etc/ansible/roles.
- Update the hosts file to include the private IP of the webservers and ELK server
- Run the playbook, and navigate to http://52.183.101.12:5601/app/kibana to check that the installation worked as expected.

Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_ 
It is called filename-playbook.yml and it is in the /etc/ansible directory
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ 
Within the ELK yml file you code in the hosts you want it installed on.

- _Which URL do you navigate to in order to check that the ELK server is running? 
http://52.183.101.12:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
