<h1>SIEM - Azure Sentinel</h1>


<h2>Description</h2>

- To implement this project, a custom Powershell script was used to extract metadata from Windows Event Viewer and forward the data to third party API to derive geolocation data.<br />
- Thereafter, Log Analytics Workspace was created in Azure to ingest the custom logs containing some of the extracted information (Latitude, Longitude, State/Province and Country)<br />
- Next,the geo data in Log Analytic Workspace was mapped with Azure Sentinel.<br />
- Finally, Azure Sentinel (Microsoft's Cloud SIEM) workbook to display global attack data (RDP brute force) on world map, indicating the physical location and magnitude of attack was generated.<br />
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>ipgeolocation API</b>

<h2>Environments Used </h2>

- <b>Windows 11</b> 
- <b>Azure Portal<b>


<h2>Program walk-through:</h2>

<p align="center">
Create a Virtual Machine to serve a honeyPot for attackers: <br/>
<img src="https://i.imgur.com/6DGFSLL.png" height="60%" width="60%" alt="VM Creation"/>
<br />
<br />
Create the Log Analytic Workspace to store extracted logs:  <br/>
<img src="https://i.imgur.com/SGoIjyP.png" height="60%" width="60%" alt="Create Log Analytic"/>
<br />
<br />
From Microsoft Defender for Cloud, enable the ability for the Log Analytic to access logs from the HoneyPot VM : <br/>
<img src="https://i.imgur.com/wR08d4G.png" height="60%" width="60%" alt="Microsoft Defender for Cloud"/>
<br />
<br />
Connect the VM to Log Analytics:  <br/>
<img src="https://i.imgur.com/3RqwNv4.png" height="60%" width="60%" alt="Connect the VM to Log Analytics"/>
<br />
<br />
RDP into the HoneyPot VM to capture Event Log (I intentionally used a wrong password initailly to view the log):  <br/>
<img src="https://i.imgur.com/r9cnUQ7.png" height="60%" width="60%" alt="Event Viewer"/>
<br />
<br />
Powershell script that loops through thr event viewr to capture some data from failed logins. API key was generated from the (https://ipgeolocation.io) :  <br/>
<img src="https://i.imgur.com/tRA1ncM.png="60%" width="60%" alt="PowerShell Script"/>
<br />
<br />
Created Custom Log in Log Analytic and after few minutes, the custom log got populated on Azure portal:  <br/>
<img src="https://i.imgur.com/LSiY1LC.png" height="60%" width="60%" alt="Custom Log in Log Analytic"/> 
<br />
<br />
Extract the geo data of interest form the custom log and create custom fields :  <br/>
<img src="https://i.imgur.com/OzLkP5n.png" height="60%" width="60%" alt="Extract the geo data"/>
<br />
<br />
Setup map in Sentinel with Longitude and Latitude :  <br/>
<img src="https://i.imgur.com/Ze3hD1m.png" height="60%" width="60%" alt="Setup map in Sentinel"/>
<br />
<br />
View of Captured attacks after few minutes of exposure of the oneyPot VM :  <br/>
<img src="https://i.imgur.com/qHG3vgK.png" height="60%" width="60%" alt="Connect the VM to Log Analytics"/>
<br />
<br />                                                                                                        
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
