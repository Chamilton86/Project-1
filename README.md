## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Network diagram](https://github.com/Chamilton86/Project-1/blob/f5fa373b9e119f96c1ac9d53f151bcb47aa18b43/Diagrams/UNIT%2012%20HW.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  [elk-playbook](https://github.com/Chamilton86/Project-1/blob/6965f22f3031d4a82b214701772e5dd04ca2b818/Ansible/install-elk.yml)

[filebeat-playbook](https://github.com/Chamilton86/Project-1/blob/fb7afcfdabba40ed6090d01fbd3b1a00ecd738d9/Ansible/filebeat-playbook.yml)

[hosts](https://github.com/Chamilton86/Project-1/blob/6965f22f3031d4a82b214701772e5dd04ca2b818/Ansible/hosts.yml)

[metric-playbook](https://github.com/Chamilton86/Project-1/blob/6965f22f3031d4a82b214701772e5dd04ca2b818/Ansible/metricbeat-playbook.yml)

[pentest](https://github.com/Chamilton86/Project-1/blob/65f9e08eda8b513021af2712f9be11d0c2c80523/Ansible/pentest.yml)





This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- What aspect of security do load balancers protect? 
- Load balancers protect the system from DDoS attacks by shiftinf traffic
- 
- What is the advantage of a jump box?_
- The advantage of a jump box is to give secure access to such resources via SSH and Private Pre Shared key

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs
- What does Filebeat watch for?
- -Filebeat forwards and centralizes log data.  Filebeat monitors the log files or locations that you specify collects log events and forwards them either to Elasticsearch or Logstash for indexing
- 
- What does Metricbeat record?
- -Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch of Logstash.  Metricbeat helps you monitor your servers by collecting metrics from the systme and services running on the server, such as Apache

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  10.1.0.4     | Linux            |
| Elk      | Gateway  | 40.78.3.115| Linux            |
| Web-1    | LBalancer| FTE-IP     | Linux            |
| Web-2    | LBalancer| FTE-IP     | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Elk machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 45.23.180.71

Machines within the network can only be accessed by Jumpbox via SSH & Private Pre-Shared key
- Which machine did you allow to access your ELK VM?
- Jumpbox
- 
-  What was its IP address?_
-  40.113.205.32 (public) 10.1.0.4 (private)

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 45.23.180.71         |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_

The playbook implements the following tasks:
- In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Check for presence of docker (Installation/Update)
- Check for presence of python3-pip (Install/Update)
- Install Docker module
- Increase virtual memory
- Download and launch docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Docker ps](https://github.com/shonham/Shontae-s-Cybersecurity-Project-1/blob/8573356a371266d9c31bd00b2386bedb29c34ddd/diagrams/Docker%20ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 10.1.0.5 
- Web-2 10.1.0.6

We have installed the following Beats on these machines:
-Webservers

These Beats allow us to collect the following information from each machine:
-Machine health, performance, system logs and events

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat file to file-config.yml
- Update the filebeat.yml file to include...
- Run the playbook, and navigate to check that the installation worked as expected.
![kibanaserver](https://github.com/Chamilton86/Project-1/blob/e319cb422f90df56d9665f319ecd7c5b7ee3b172/Diagrams/kibana.png)

Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Ansible-playbook files
- Where do you copy it? Root of ansible
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? hosts configuration file

Which URL do you navigate to in order to check that the ELK server is running? 
-ssh azureuser@10.1.0.5
-http://40.78.3.115:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
