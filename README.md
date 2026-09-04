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

<img width="1600" height="860" alt="image" src="https://github.com/user-attachments/assets/8b9ee0ee-0ff2-4f23-9f8f-335bb049763a" />


# Successful Response

Click on Add Panel

Under New, choose Single Value

Use Shared Time Picker time_range

Set Content Title to "Successful Response"

Enter the Search String as below

 source="apache_mixed_access_full (1).json" host="webserver" sourcetype="_json" method=GET status=200 
| stats count AS "Successful Responses"	

<img width="1480" height="602" alt="image" src="https://github.com/user-attachments/assets/87f1d4c8-532f-409c-8c77-bfa6b72447ef" />




