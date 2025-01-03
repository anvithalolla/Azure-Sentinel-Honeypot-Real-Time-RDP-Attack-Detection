# **AZURE SENTINEL HONEYPOT REAL-TIME RDP ATTACK DETECTION**

### **Project Description:**

This project involves the creation of an RDP honeypot using a virtual machine exposed to the internet, attracting brute force attacks. The integration with Azure Sentinel provides a comprehensive security information and event management (SIEM) solution. A custom PowerShell script extracts failed RDP log events, and the ipgeolocation.io API is utilized to gather geolocation information about attackers

### **Tools Used:** 
- Microsoft Sentinel (SIEM)
- Log Analytic Workbooks
- Microsoft Defender for Cloud
- Virtual Machines
- Remote Desktop
- PowerShell
- API's
- Event Viewer
- Firewall

### **Environments Used:**
- Microsoft Azure
- Windows 10 (21H2)

### **Links:**
Microsoft Azure Free Trial: https://azure.microsoft.com/en-us/free/

IPGeolocation: https://ipgeolocation.io/

### **Microsoft Azure Resources for HoneyPot Lab:**

![image](https://github.com/anvithalolla/Azure-Sentinel-Honeypot-Real-Time-RDP-Attack-Detection/assets/55392153/3cbc4fc8-eddb-44fb-af2a-33d5a638e2b1)

### Concept of Creating Vulnerable VM
![image](https://github.com/anvithalolla/Azure-Sentinel-Honeypot-Real-Time-RDP-Attack-Detection/assets/55392153/10fd5485-b0eb-4db8-b35f-b36f79b48b93)

_(Ref: Youtube)_

- The first step in this project is to create a Microsoft Azure trial account. This gives you the ability to set up the VM, Sentinel, and logs within Azure.
After setting up the virtual machine named InfoExtraction and log analysis workspace named Logginginformation. Next step is to connect the virtual machine with workspace.
In the VM we were provided with IP address, copy that and open Remote Desktop connection and access the VM, make sure to turn off the firewall.

- Create a IPGeolocation API account. This is the API we will use to gather the IP address of the RDP attempts.
<img width="287" alt="image" src="https://github.com/anvithalolla/Azure-Sentinel-Honeypot-Real-Time-RDP-Attack-Detection/assets/55392153/442408fe-1efd-4728-9bfa-f714521f9dbc">

- Open PowerShell ISE and run the following script after replacing the API key with the key you receive from the IPGeolocation API.

### **Sample Log with Powershell Script**

<img width="633" alt="291138765-c841a82f-0666-47c5-88c4-5ba8b7f25353" src="https://github.com/user-attachments/assets/10d9082d-3e51-4fb8-9993-4b1aa03b15f2" />


- You can see above, that the script is working. You are already able to see RDP attempts being logged. The data is being saved locally in the c/programdata/failed_rdp as .log file.

### **Failed RDP JSON File:**
<img width="951" alt="image" src="https://github.com/anvithalolla/Azure-Sentinel-Honeypot-Real-Time-RDP-Attack-Detection/assets/55392153/4d268269-099c-4a9a-8cd0-eb5066807d7a">

- Now you will put this data into Azure. Copy the .log file onto your personal machine. Create a custom log and insert the .log data into a sample. Then you will upload the actual file path on the VM for the data to be pulled from.

- Go to logs and add a new query by entering "FAILED_RDP_WITH_GEO_CL" and the log data will be displayed . That will be displayed as follows:

<img width="507" alt="image" src="https://github.com/anvithalolla/Azure-Sentinel-Honeypot-Real-Time-RDP-Attack-Detection/assets/55392153/04e25a4b-14eb-4d4a-929d-bfe288b71050">

<br/><br/>
**Create a Azure Sentinal workbook named *"Azure- SENTINAL"* and enter KQL (Kusto Querly Language) and run the code by selecting **"Map"** under visualisation .It will look something like this after 4hrs**

![image](https://github.com/anvithalolla/Azure-Sentinel-Honeypot-Real-Time-RDP-Attack-Detection/assets/55392153/102973a9-26e0-4a15-b7ae-7ee8307a0321)
**World map of incoming attacks after 20 hours:**

![image](https://github.com/anvithalolla/Azure-Sentinel-Honeypot-Real-Time-RDP-Attack-Detection/assets/55392153/f1154767-1138-4a86-bd92-177cd7babb7b)

