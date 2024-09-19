# SIEM-Implementation and Fleet Server Project


## Objective

In this project, I have set up a Security Information and Event Management (SIEM) system in my home lab. I have configured Elasticsearch, Logstash, and Kibana (ELK). I have also configured it as a fleet server and deployed multiple agents to simulate a real-world security monitoring environment.


### Skills Learned



### Tools Used

- Oracle VM Virtual Box Manager
- Ubuntu 24 Operating system
- Windows Server 2022
- Lucidchart
- Elasticsearch, Logstash, Kibana
  

![topology](https://github.com/user-attachments/assets/f86f499c-57d2-4f9e-96fa-636e4b90a328)

  

## Steps


1. First I will download and install the public signing key, along with the apt-transport-https package and save the repository definition to /etc/apt/sources.list.d/elastic-8.x.list. Next, I will run an update command and pair it with installing Elasticsearch.

![ELK1](https://github.com/user-attachments/assets/d70f997b-da17-4cb6-864a-ac32af26a165)

2. Here I am installing Logstash and Kibana

![ELK2](https://github.com/user-attachments/assets/5e8d5cfe-e2d5-49c5-8d7b-24c8d1b07a71)

3. Some modifications have to be done to these yml files, here I will uncomment the server.port: 5601 and server.host "0.0.0.0"

![ELK3](https://github.com/user-attachments/assets/793c21fe-b7f7-4fc5-8abe-58a191722069)

4. The
 
![ELK4 elasticsearch 2](https://github.com/user-attachments/assets/58d25cd0-b40b-40b8-ab3c-a5189716452d)

![ELK4 elasticsearch](https://github.com/user-attachments/assets/4f5326b7-6d6b-4ed0-924f-d93411cea191)

5.

![ELK5 Start up service](https://github.com/user-attachments/assets/ee29d478-89d9-469e-894c-a4e586bddd2a)

6. The

![ELK6 Start Services](https://github.com/user-attachments/assets/5aa60147-94b0-4df3-89e5-ccfc422b10d1)

7. The

![ELK7Kibana Status](https://github.com/user-attachments/assets/558c738c-2ec4-4ad8-a153-7d82a6750a9e)

8. The

![ELK8 Elastic Status](https://github.com/user-attachments/assets/d820c69b-b3d5-4bc9-b889-cb4255003637)

9.

![ELK9 Enrollment Token](https://github.com/user-attachments/assets/ce92778b-4e3c-40de-9cef-caca9f7c3cdf)

10. The

![ELK10 Token and Verification Code](https://github.com/user-attachments/assets/fae05c30-d702-4568-bd40-e193483bd2df)

11. The

![ELK11 Verification COde](https://github.com/user-attachments/assets/874dc5ce-0035-40cb-8fe8-b2dde9ea6050)

12. The

![ELK12 Finished](https://github.com/user-attachments/assets/7769c149-ea82-4984-83ab-be92a6608807)

13. The

![Fleet 1](https://github.com/user-attachments/assets/df118712-651f-4ef9-9216-336b56309669)

14. The

![Fleet 2](https://github.com/user-attachments/assets/eb60fdd1-1b61-4b7c-b813-1de6385cbe2f)

15. The

![Fleet add windows agent](https://github.com/user-attachments/assets/c081c10d-8307-4bc6-a8d4-7efe72b743d2)

16. The

![Fleet pwershell](https://github.com/user-attachments/assets/bee9897f-edf7-44cf-979c-b81bb253893a)

17. The

![Fleet joined agent windows](https://github.com/user-attachments/assets/bee15812-e194-42bc-9ebf-dcae6dec9b72)

18. The

![fleet windows logs](https://github.com/user-attachments/assets/8114ed13-66e7-4dbe-b1ae-018f6c6ed64a)

19. The

![Fleet Sysmon](https://github.com/user-attachments/assets/5fae8aa5-0acb-4456-b4b0-bdbf7a511388)

![Fleet Windows Defender](https://github.com/user-attachments/assets/00c0e927-9ee8-449b-b919-27698660b92c)

20. The
    
![FLEET LOGS](https://github.com/user-attachments/assets/c9910228-31de-40a5-b021-9da2db47cded)


21. The
![Fleet sysmon agent connected](https://github.com/user-attachments/assets/3d3fa7cc-46bc-4d7c-a3d1-4b0f0aa5fc9e)


22. The

![FLEET WINLOG](https://github.com/user-attachments/assets/9dd49188-c5c7-4181-b842-ea31900496ee)

23. The

![Fleet agent machine](https://github.com/user-attachments/assets/661a142f-c2ff-4292-9edc-961ad846c262)

24. The

![Fleet 2 agents](https://github.com/user-attachments/assets/0f4a6e76-a561-4dc7-b18b-773e8a80fc8d)






















