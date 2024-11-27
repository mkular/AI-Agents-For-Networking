# AI-Agents-For-Networking
AI agents for network deployment, configuration and monitoring

## Description
Overall agentic worflow consisted of 4 agents. First one was tasked to get the installation steps from https://learn.srlinux.dev/get-started/lab/ website. 
Second agent executed those steps. Third agent came up with relevant node configs based on network topology and finally the last agent executed those and verified end to end connectivity.

<img width="1665" alt="Agentic Workflow" src="https://github.com/user-attachments/assets/4860d142-8d74-4c79-85e6-880b8a7205b4">

For this use-case, entire topology was deployed on a pre-built Debian 12 UTM VM (as a sandbox environment). This was deliberatly chosen as it comes with all relevant packages like containerlab and docker packages pre-installed. Containerlab helps spin up various container based networking topologies with ease. Following topology was chosen which consisted of linux containers and Nokia's SR Linux containers:
Client1 - - Leaf1 - - Spine1 - - Leaf2 - - Client2
Where Client1 and Client2 are linux containers and Leaf1 and Leaf2 are IXR-D2L and Spine1 is IXR-D5 types of SR Linux containers.

## Basic workflow
1. Document Specialist Agent goes to and extracts following steps from the containerlab quickstart guide (https://learn.srlinux.dev/get-started/lab/):
					"1. Extract installation steps"
					"2. Identify topology deployment steps"
					"3. Find node connection instructions"
	        "Present in a clear, sequential format"

2. Linux Configuration Agent executes the steps given by Document Specialist Agent and deploys containerlab
   and topology: Client1 - - Leaf1 - - Spine1 - - Leaf2 - - Client2.

3. Network Configuration Specialist agent the understand the topology and comes up with the right ip
   allocation scheme, interface and routing configs.

4. Senior Network Administrator agent then executes these configs and verifies end to end connectivity.

## Instructions to run[^1]
1. Create a conda env in order to run and install all dependencies.
   <pre>conda create ai-agents python=3.12
   conda activate ai-agents
2. Install following requirements:
```
   pip install crewai
   pip install requests
   pip install paramiko
   pip install netmiko
```
4. Enter the right api key for open ai and anthropic in the relevant code cells.
6. Run all the cells in the notebook.
   
  [^1]: __**NOTE**__ : Be patient while running this code book it takes a little over 10 mins to complete. One challenge is that run times varies with every run and sometimes it can take even longer. Also claude-3-5-sonnet usage can get expensive real quick, so be careful :).
