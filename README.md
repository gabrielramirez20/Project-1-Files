# Project-1-Files
Files that review skills from previous units
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Network Diagram](https://raw.githubusercontent.com/gabrielramirez20/Project-1-Files/Diagrams/Network%20Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yml and config file may be used to install only certain pieces of it, such as Filebeat.

  - Enter the playbook file._

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly functional and available, in addition to restricting traffic to the network.
-  What aspect of security do load balancers protect? Load balancers add resiliency by routing live traffic from one server to another if a server falls prey to a DDoS attack or otherwise become unavailable.  What is the advantage of a jump box? The advantage of a jump box is that it prevents Aazure vm's from being exposed from a public IP address. This allows us to monitor and log on a sinlge box.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system logs.
-  What does Filebeat watch for? Filebeat monitors the log files or locations that you specify, collects log events and
 forwards them to Elasticsearch
 -  What does Metricbeat record? Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| Web-1    | Ubuntu   | 10.0.0.5   | Linux            |
| Web-2    | Ubuntu   | 10.0.0.6   | Linux            |
| Elk      | Ubuntu   | 10.0.0.4   | Limux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

Machines within the network can only be accessed by jump box provisioner through SSH jump box.
-  Which machine did you allow to access your ELK VM? The jump box via ssh
-  What was its IP address? It was my desktop IP address

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | Personal             |  
| LB       | Yes                 | Open                 |
| Web-1    | No                  | 10.0.0.5             |
| Web-2    | No                  | 10.0.0.6             | 

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
-  What is the main advantage of automating configuration with Ansible? There are multiple advantages, Ansible lets you quickly and easily deploy multi tier applications through a yaml playbook. You don't need to write custom code to automate your systems.

The playbook implements the following tasks:
-  In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- First task was to resize the virtual memory.
- Second install Docker by using the APT module to install Docker.io
- Third install PIP using APT.
- Fourth install python3 using PIP
- Fifth downloads and launches the ELK Container.
- Sixth enable docker services.
- Seventh start docker services with systemd

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-  List the IP addresses of the machines you are monitoring
- Web-1: 10.1.0.5
- Web-2: 10.1.0.6

We have installed the following Beats on these machines:
-  Specify which Beats you successfully installed
- Filebeaat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat will be used to collect log files from very specific files such as Apache, Microsft Azure tools and web servers, MySQL databases.
- Metericbeat will be used to monitor vm stats, per cpu core stats, per filesystem stats, memory stats and network stats.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the configuration file to ansible folder.
- Update the /etc/ansible/hosts file to include IP address of the Elk server vm and webservers.


- Run the playbook, and navigate to Kibana ((Your IP Address):5601) to check that the installation worked as expected.

- _Which file do you update to make Ansible run the playbook on a specific machine? The Host file How do I specify which machine to install the ELK server on versus which to install Filebeat on? Update filebeat-config.yml -- specify which machine to install by updating the host files with ip addresses of web/elk servers and selecting which group to run on in ansible
- _Which URL do you navigate to in order to check that the ELK server is running? http://[your.ELK-VM.External.IP]:5601/app/kibana.

