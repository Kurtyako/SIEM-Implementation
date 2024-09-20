# SIEM-Implementation and Fleet Server Project


## Objective

In this project, I have set up a Security Information and Event Management (SIEM) system in my home lab. I have configured Elasticsearch, Logstash, and Kibana (ELK). I have also configured it as a Fleet Server and deployed multiple agents to simulate a real-world security monitoring environment.


### Skills Learned
- SIEM Knowledge: Familiarity with SIEM log management and security monitoring
- Fleet Server Knowledge: Understanding of how to deploy and manage a Fleet Server for endpoint management
- Integration Skills: Knowledge of integrating various data sources and security tools with the SIEM solution.

### Tools Used

- Oracle VM Virtual Box Manager
- Ubuntu 24 Operating system
- Windows Server 2022
- Lucidchart
- Elasticsearch, Logstash, Kibana
- Fleet
  

![topology](https://github.com/user-attachments/assets/f86f499c-57d2-4f9e-96fa-636e4b90a328)

  

## Steps


1. First I will download and install the public signing key, along with the apt-transport-https package and save the repository definition to /etc/apt/sources.list.d/elastic-8.x.list. Next, I will run an update command and pair it with installing Elasticsearch.

![ELK1](https://github.com/user-attachments/assets/d70f997b-da17-4cb6-864a-ac32af26a165)


2. Here I am installing Logstash and Kibana

![ELK2](https://github.com/user-attachments/assets/5e8d5cfe-e2d5-49c5-8d7b-24c8d1b07a71)


3. Some modifications have to be done to these yml files, here I will uncomment the server.port: 5601 and server.host "0.0.0.0"

![ELK3](https://github.com/user-attachments/assets/793c21fe-b7f7-4fc5-8abe-58a191722069)


4. Here I am uncommenting out the cluster.name and giving it a name. I am also uncommenting out the network.host "0.0.0.0" and the http.port 9200
 
![ELK4 elasticsearch 2](https://github.com/user-attachments/assets/58d25cd0-b40b-40b8-ab3c-a5189716452d)

![ELK4 elasticsearch](https://github.com/user-attachments/assets/4f5326b7-6d6b-4ed0-924f-d93411cea191)


5. Now I will be configuring Elasticsearch to start automatically when the system boots up

![ELK5 Start up service](https://github.com/user-attachments/assets/ee29d478-89d9-469e-894c-a4e586bddd2a)


6. I am starting Elasticsearch and Kibana

![ELK6 Start Services](https://github.com/user-attachments/assets/5aa60147-94b0-4df3-89e5-ccfc422b10d1)


7. Checking the status for Kibana

![ELK7Kibana Status](https://github.com/user-attachments/assets/558c738c-2ec4-4ad8-a153-7d82a6750a9e)


8. Checking the status for Elasticsearch

![ELK8 Elastic Status](https://github.com/user-attachments/assets/d820c69b-b3d5-4bc9-b889-cb4255003637)


9. On Firefox I searched for HTTP://0.0.0.0:5601 to reach the Elasticsearch dashboard and now an enrollment token is required along with a verification code

![ELK9 Enrollment Token](https://github.com/user-attachments/assets/ce92778b-4e3c-40de-9cef-caca9f7c3cdf)


10. Here are the commands i used to retrieve the enrollment token and verification code

![ELK10 Token and Verification Code](https://github.com/user-attachments/assets/fae05c30-d702-4568-bd40-e193483bd2df)


11. This is what the verification code page looks like

![ELK11 Verification COde](https://github.com/user-attachments/assets/874dc5ce-0035-40cb-8fe8-b2dde9ea6050)


12. Now we are logged into the Elastic dashboard

![ELK12 Finished](https://github.com/user-attachments/assets/7769c149-ea82-4984-83ab-be92a6608807)


13. I am also going to make this server a Fleet Server. Using these commands I will enroll this server to become a Fleet Server

![Fleet 1](https://github.com/user-attachments/assets/df118712-651f-4ef9-9216-336b56309669)


14. Near the bottom you can see that it says Fleet Server Connected

![Fleet 2](https://github.com/user-attachments/assets/eb60fdd1-1b61-4b7c-b813-1de6385cbe2f)


15. I will now be adding an agent to this Fleet server which will be a Windows 2022 Server

![Fleet add windows agent](https://github.com/user-attachments/assets/c081c10d-8307-4bc6-a8d4-7efe72b743d2)


16. Using this command it will connect this Windows 2022 Server to my Fleet management server

![Fleet pwershell](https://github.com/user-attachments/assets/bee9897f-edf7-44cf-979c-b81bb253893a)


17. As you can see the Windows machine is now an active agent part of the fleet server

![Fleet joined agent windows](https://github.com/user-attachments/assets/bee15812-e194-42bc-9ebf-dcae6dec9b72)


18. I now have data ingested into the Elastic dashboard from the windows machine

![fleet windows logs](https://github.com/user-attachments/assets/8114ed13-66e7-4dbe-b1ae-018f6c6ed64a)


19. Now let's say I want to be more specific with the type of logs I want it to monitor. I am going to add a custom integration for Sysmon and Windows Defender logs into the SIEM.

![Fleet Sysmon](https://github.com/user-attachments/assets/5fae8aa5-0acb-4456-b4b0-bdbf7a511388)

![Fleet Windows Defender](https://github.com/user-attachments/assets/00c0e927-9ee8-449b-b919-27698660b92c)


20. Here you can see my two custom integrations. For Windows Defender I am going to add a filter for specific event IDs including 1116, 1117, 5001
#
    -ID 1116 The antimalware platform detected malware or other potentially unwanted software
    -ID 1117 The antimalware platform performed an action to protect your system from malware or other potentially unwanted software
    -ID 5001 Microsoft Defender Antivirus real-time protection scanning for malware and other potentially unwanted software was disabled
    
![FLEET LOGS](https://github.com/user-attachments/assets/c9910228-31de-40a5-b021-9da2db47cded)


21. We can now see that my custom integration seems to be working as we are receiving Sysmon logs into the SIEM
    
![Fleet sysmon agent connected](https://github.com/user-attachments/assets/3d3fa7cc-46bc-4d7c-a3d1-4b0f0aa5fc9e)


22. As a test I disabled Real-time protection on the Windows 2022 Server and look we have an event in our SIEM with the event ID as 5001 by Windows Defender


![FLEET WINLOG](https://github.com/user-attachments/assets/9dd49188-c5c7-4181-b842-ea31900496ee)


23. I will also be adding another agent, this one will be a Linux server (Ubuntu 24)

![Fleet agent machine](https://github.com/user-attachments/assets/661a142f-c2ff-4292-9edc-961ad846c262)


24. As you can see we now have two agents, one Windows agent and one Linux agent

![Fleet 2 agents](https://github.com/user-attachments/assets/0f4a6e76-a561-4dc7-b18b-773e8a80fc8d)






















