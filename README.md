## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Elk Project Final Diagram
https://drive.google.com/file/d/1nImKqEzhM9E_SyKCG1VZJ5_EdtAxVdnc/view?usp=sharing
These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

The playbook file._ ![Pentest YML Screenshot](https://user-images.githubusercontent.com/95048384/159387220-616413d1-c0f8-4f13-989f-8d89b4bd8826.png)
  
This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
- Beats in Use
- Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network.
- Load balancers protect networking systems by defending against distributed denial-of-service (DDoS) attacks.
- The advantage of a jump box is it allows for all admins to connect to the jump box before performing any administrative tasks. It also allows an original point of connection to other servers or untrusted environments.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
- Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
- Metricbeat is a lightweight shipper that you can install on your servers to periodically collect metrics from the operating system and from services running on the server. Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify.

The configuration details of each machine may be found below.


| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Elk      | Server   | 10.1.0.4   | Linux            |
| Web-1    | Server   | 10.0.0.5   | Linux            |
| Web-2    | Server   | 10.0.0.6   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 73.178.126.28

Machines within the network can only be accessed by Jump Box.
- The Jump Box machine had access to the ELK VM. The public IP address is 20.228.226.85. The private IP address is 10.0.0.4.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |    No               |    73.178.126.28     |
| Elk      |    No               |    20.228.226.85     |
| Web-1    |    No               |    20.228.226.85     |
| Web-2    |    No               |    20.228.226.85     |

### Elk Configuration

Ansible was used to automate the configuration of the ELK machine. No configuration was performed manually, which is advantageous because there are no special coding skills are required to run the Ansible playbooks. Ansible lets you model complex IT workflows.


The playbook implements the following tasks:
- Install docker.io
- Install python3-pip
- Install Docker module
- Increase virtual memory
- Increase virtual memory on restart
- Download and launch a docker elk container
- Enable service docker on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Docker PS ![Docker PS](https://user-images.githubusercontent.com/95048384/159387324-3889c98b-4ea9-408b-9f34-9296b92a909a.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1: IP Address (10.0.0.5)
- Web-2: IP Address (10.0.0.6)

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat collects audit logs, GC logs, server logs, and slow logs. Metricbeat helps monitor servers by collecting metrics from the system and services running on the server.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the SSH key from the ansible container to the Jumpbox.
- Update the ELK configuration file to include the elk server, 
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

- Filebeat-configuration.yml is the playbook file and it is copied to the elk machine.
- The ansible file is the playbook that is needed to be updated to run the playbook. Replacing the IP address with the IP address of the ELK machine in the filebeat config file allows us to run the file on the elk machine.
-  HTTP://[your.VM.IP]:5601/app/kibana is the url used to make sure the elk machine is working.
