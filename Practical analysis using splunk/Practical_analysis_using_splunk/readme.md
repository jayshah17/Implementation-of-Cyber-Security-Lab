# Intro to Splunk

1. What is splunk ?
   Splunk's software can be used to examine, monitor, and search for machine-generated big data through a browser-like interface.

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/0122f712-93bc-4b71-bb0e-3d410185e5b6)

2. Using splunk web

   Splunk web is pre configured environment, there are three pre defined roles in splunk enterprise a. Admin - Full access b. Power - It will perform real time          searches. c. User - user can access own knowleadge object.

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/0fe56146-bb42-49f7-8285-80b99aa2c21c)

  Splunk default lauch environment

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/fbd95e35-84ac-476e-8a07-94c5509b4af1)

3. Using search

    Search option is used to search the incident log with time span.

    Limiting a search by time is a key to faster result and is a best pratice.
    Eg. Installing cmatrix in remote VM (Kali) and we can see the installation logs in splunk enterprises.

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/8f22fd55-53b4-40f0-ab6e-7ed42b5b65e5)

  Commands that create statics and visualisation are called transforming commands.
  We can share the share job log with other user it will remian active for 7 days, and every 10 min we need to refresh the log search.
  We can dowload the report in csv,xml,json.

4. Exploring Events

   If we search the objects in filters by default the event will turn the list, filtered keyword would be highlighted and we can examine the logs with timespan.

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/fec8b2f3-51ee-472e-8a83-a5e1249b9c61)
  Many events actions filter will be available.

5. Using search term
  In filters we can use terms of keywords.
  Eg. fail*, failed, FAILURE
  ![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/b6f003d7-a826-4eb5-8257-e6343062ef8b)

   search terms are not case senstive and booleans also we can use
   Boolean operations have an order of evaluation a. NOT b. OR c. AND Note: parenthesis () should be used
  ![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/7b614f56-d9e3-47e1-8090-e11bbbc4ea61)
  ![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/b6de5b51-be37-42a4-a410-615fc119b4c8)
  User can customize the filter as per the requirements.

6. What are commands ?
  Search splunk language contain 5 component’s
  a. search term - Fiundation of search query. b. commands - Commands is used to customize the log as per the need like charts, statistics and formatting. c.         functions - How we need to display the charts and evaluate the results. d. arguments - It is the variables which we want to apply in the functions. e. clauses -    It will group the result as per the requirement.

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/8db05333-1cc2-42c7-b46d-628dd87728f1)

7. What are knowledge objects?
   It is tools that help you discover and analyse the data, will be grouped in 5 categories .
    a.Data Interpretation b.Data classifications c.Data Enrichment d.Data Normalisation e.Data Model
   Knowleage object is use full for several reasons it can be create by one user and share with other user with permission granted. It is powerful tool for your       deployment
   Data Interpretation - Fields
   ![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/1dde8ded-0435-4701-8714-f405228a0ace)
   ![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/9a4457b2-6466-4da9-b9d0-e4ebb418fd07)

8. Creating Reports
    Customize the report using visualization trick and statistics charts
   ![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/a6990905-1590-4d38-84f5-9e6fc0d4731a)

9. Creating Dashboards
    Creating new dashboard for User
![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/97db5393-8e6f-4a15-b53c-dd21d8eadade)
![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/6265d46e-77f6-4f27-ba53-51c0eb7ab7c5)
    As per the requirement of the report and analyses we can customize the dashboard accordingly.

10. Dashboard Studio
    Classic Dashboard
![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/25cd9991-68b6-48c5-97e9-c4a95028702f)
Cloning exisitng dashboard into studio dashboard
![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/edcac258-9966-44e4-aef1-e237ba0fc612)
Multiple customisation available to update the classic dahsboard
![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/67867ff1-2913-44b3-9350-ceff3b6709ea)
