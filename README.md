🛡️ ##Splunk SIEM Dashboard for Apache Logs (Haxcamp Project)

📌 ## Project Overview

This repository contains a step-by-step hands-on implementation of an Apache Log Monitoring & Threat Hunting Dashboard in Splunk Enterprise, 
based on the Haxcamp SOC Analyst Lab framework.

STEP 1: Start Splunk in Kali Linux Terminal

Open your Kali Linux terminal.

Navigate to the Splunk executable directory:

Type the command  udo /opt/splunk/bin/splunk start --run-as-root

Then after starting the server open browser in the host machine

Type- Kali ip:8000 ( e.g 192.168.190.135:8000)

STEP 2: Add Apache Log File (GUI Method)

In the Splunk home dashboard, click on Settings in the top navigation bar.

Select Add Data from the drop-down menu.

Click on the Upload button.

Click Select File and browse to your Apache log file location (e.g., /var/log/apache2/access.log or your downloaded .log file).

Click Next.

<img width="1299" height="481" alt="image" src="https://github.com/user-attachments/assets/5b9eef31-9443-4359-99cb-f281fac3c1ee" />

<img width="1600" height="860" alt="image" src="https://github.com/user-attachments/assets/298be55d-f1db-41d2-a1cc-2b9bd1e48db8" />

<img width="1600" height="860" alt="image" src="https://github.com/user-attachments/assets/f8bb41f4-7f79-4b4e-8b95-bed45764942b" />

## Setting up Time Range

 Add Time Range Button

 Click om Add Input

 Select Time and click on pencil icon

 Set Label to Time Range and Token time_range

 Again Add Input

Select Submit

<img width="1216" height="615" alt="image" src="https://github.com/user-attachments/assets/4590cee5-3f3d-410c-b5bc-ef7c6618920e" />

## Web Activities

Goal: Give a quick summary of Web activity.

Total Web Requests

Click on Add Panel

Under New, choose Single Value

Use Shared Time Picker time_range

Set Content Title to "Total Web Requests"

Enter the Search String as below

 source="apache_mixed_access_full (1).json" host="webserver" sourcetype="_json" 
| stats count AS "Total Web Requests"

<img width="1298" height="626" alt="image" src="https://github.com/user-attachments/assets/c2e5c076-0546-475d-b60d-3f8dade1d2bc" />


<img width="1273" height="634" alt="image" src="https://github.com/user-attachments/assets/19efb5c6-1ddf-4c17-85c4-462ad31588f2" />


# Successful Response

Click on Add Panel

Under New, choose Single Value

Use Shared Time Picker time_range

Set Content Title to "Successful Response"

Enter the Search String as below

 source="apache_mixed_access_full (1).json" host="webserver" sourcetype="_json" method=GET status=200 
| stats count AS "Successful Responses"	

<img width="1480" height="602" alt="image" src="https://github.com/user-attachments/assets/87f1d4c8-532f-409c-8c77-bfa6b72447ef" />

# Client Errors (4xx)

Click on Add Panel

Under New, choose Single Value

Use Shared Time Picker time_range

Set Content Title to "Client Errors"

Enter the Search String as below:

source="apache_mixed_access_full (1).json" host="webserver" sourcetype="_json" | where status>=400 and status<500 | stats count AS "Client Errors"

<img width="979" height="478" alt="image" src="https://github.com/user-attachments/assets/412595b5-d690-42d9-b8f1-496a49ae34a9" />

<img width="973" height="495" alt="image" src="https://github.com/user-attachments/assets/e1501e67-119d-4852-bccc-0cf0a907c1f0" />

# Server Errors (5xx)

Click on Add Panel

Under New, choose Single Value

Use Shared Time Picker time_range

Set Content Title to "Server Errors (5xx)"

Enter the Search String as below:

source="apache_mixed_access_full (1).json" host="webserver" sourcetype="_json" 
| where status>=400 and status<500 
| stats count AS "Client Errors"

<img width="970" height="499" alt="image" src="https://github.com/user-attachments/assets/5c94353b-a077-43e7-a18b-4caf01748f28" />

# Web Stats

Goal: Give a quick summary of Web Statstics.

Top Requested URIs

Click on Add Panel

Under New, choose Bar Chart

Use Shared Time Picker time_range

Set Content Title to "Top Requested URIs"

Enter the Search String as below

<img width="965" height="495" alt="image" src="https://github.com/user-attachments/assets/4a6be06b-34ef-4ddf-bfb8-85ab6fe3d247" />

# Top Users by IP Address

Click on Add Panel

Under New, choose Bar Chart

Use Shared Time Picker time_range

Set Content Title to "Top Users by IP Address"

Enter the Search String as below


<img width="965" height="527" alt="image" src="https://github.com/user-attachments/assets/4506a263-9763-4cde-a8b2-ed94bfcd4b3a" />


# Web Traffic by Client IP Addresses

Click on Add Panel

Under New, choose Choropleth Map

Use Shared Time Picker time_range

Set Content Title to Web Traffic by Client IP Addresses

Enter the Search String as below:

  source="apache_mixed_access_full (1).json" host="webserver" sourcetype="_json"     method=GET
| table ip
| iplocation ip
| stats count by Country
| geom geo_countries featureIdField="Country"

<img width="1038" height="526" alt="image" src="https://github.com/user-attachments/assets/c1a84768-613b-4838-ac72-86b54f1a0bf0" />

# Conclusion

plunk provides a robust, real-time Security Information and Event Management (SIEM) solution for collecting, parsing, and visualizing server telemetry. By ingesting raw Apache web server access logs, transforming raw data into structured fields, and building targeted SPL (Search Processing Language) queries, security operations teams gain end-to-end operational visibility.

Through custom dashboard panels, time-series charts, and geo-location mapping, Splunk transforms unorganized log entries into actionable security intelligence. It allows SOC analysts to quickly detect abnormal traffic patterns, flag status code errors, trace client IP behavior, and identify brute-force or scanner attacks in real time, making it an essential platform for modern threat hunting, incident response, and web infrastructure monitoring.







