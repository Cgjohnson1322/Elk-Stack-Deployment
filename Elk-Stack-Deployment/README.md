## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

[TODO: /Elk_Stack_Project/Images/Elk_Server_Deployment_Setup.png]

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Playbook/YAML file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Elk_Stack_Project/Playbooks/Install-ElkServer.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build

### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly accessible, in addition to restricting access/traffic to the network.
- _TODO:
 What aspect of security do load balancers protect?
 
 Load balancers protect the data aspect of security like servers by working on the transport layer, on way is off-loading which they an use to help mitigate a denial of service attack.
 
What is the advantage of a jump box?_

	The advantage of the jump box is that it allows you to configure and monitor all access to your VM’s , servers, etc. in a secure manner then you can add access to the jump box as needed to only those who require it and creates an almost one way in control point.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the server and system logs.
- _TODO: What does Filebeat watch for?
	Filebeat monitors, collects, and forwards log files you specify to Elastiseach or logstash.
- _TODO: What does Metricbeat record?_
	Metricbeat collects metric data like CPU usage and memory usage and logs them while being able to identify unusual or suspicious spikes in metrics parameters you set.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name       | Function      | IP Address    | Operating System |
|------------|---------------|---------------|------------------|
| Jump-Box   | Gateway       | 10.0.0.4      | Linux            |
| Elk Server | Server        | 10.2.0.4      | Linux            |
| RedTeam LB | Load Balancer | 23.100.33.134 |                  |
| Web 1      | Web Server    | 10.0.0.5      | Linux            |
| Web 2      | Web Server    | 10.0.0.6      | Linux            |
| Web 3      | Web Server    | 10.0.0.7      | Linux            |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO:
 Host #1 IP: 69.136.83.22:5601
	Host #2 IP: 71.225.240.101:5601

Machines within the network can only be accessed by ssh using an internal IP address.
- _TODO: 
Which machine did you allow to access your ELK VM? What was its IP address?
	The ELK VM was allowed access from the Host Machine of port 5601 TCP connection.
	 Host #1 IP: 69.136.83.22:5601
	Host #2 IP: 71.225.240.101:5601
	






A summary of the access policies in place can be found in the table below.

|  Name         | Publicly Accessible | Allowed IP Addresses                   |
|---------------|---------------------|----------------------------------------|
| Jump Box      | Yes                 | 69.136.83.22, 71.225.240.101           |
| Elk Server    | Yes                 | 69.136.83.22:5601, 71.225.240.101:5601 |
| Load Balancer | Yes                 | 69.136.83.22, 71.225.240.101           |
| Web 1         | No                  | 10.0.0.4                               |
| Web 2         | No                  | 10.0.0.4                               |
| Web 3         | No                  | 10.0.0.4                               |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?
	The biggest advantage of automating configuration allows you to deploy on one, hundreds, or thousands of machines in a quicker and more efficient manner.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install Docker.io
- Install Python3
- Install Docker
- Increase Virtual Memory
- Download docker container
- Ensure Service is running

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

[TODO: /Elk_Stack_Project/Images/ElkDocker.png 

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring
	- Web Server 1: 10.0.0.5
	- Web Server 2: 10.0.0.6
	- Web Server 3: 10.0.0.7



We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed
	- Filebeat
	- Metricbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc.
	
	Filebeat collects log files that you specify like system logs and so forth. So I would expect to see successful and failed ssh login attempts to the Webservers. Metricbeat collects and forwards computer metrics such as CPU usage and so forth. I would expect to see information on high usage of CPUs on one of the web servers which would mean either an issue with the load balancer out in place or other suspicious activity.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Elk Server playbook .yml file to /etc/ansible/.
- Update the hosts file to include the internal ip address of the machine under your created [Elk] header line.
- Run the playbook, and navigate to the elk server cmd line via ssh and run docker ps to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:

- _Which file is the playbook? Where do you copy it?
	The .yml file is the playbook and you copy it to the /etc/ansible folder
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
 - You update the /etc/ansible/host file to specify which specific machine you want the playbook run on by putting the internal ip of the machine under a specific header line ex: [Webserver], [Elk Server]

- _Which URL do you navigate to in order to check that the ELK server is running?

 	https:// [Public ip of Elk Server]:5601/app/kibana



_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._


Download playbook:

Ssh username@[IP of ansible node]

cd /etc/ansible

Curl https:// [website].com/Location/of/ Playbook/ Download/ File > install-elkl.yml

nano ./ansible.cfg (to update the credentials log in) ctrl+X , Y for yes then ENTER

nano ./hosts (to add internal ip of elk server under its on file header [Elk])

Ex: [Elk Internal IP] includeansible_python_interpreter=/usr/bin/python3  

Run: ansible-playbook install-elk.yml

Ssh into elk server:

Ssh username@[public IP of elk server]

Cmd: sudo docker ps (to check if elk server is up and running)
