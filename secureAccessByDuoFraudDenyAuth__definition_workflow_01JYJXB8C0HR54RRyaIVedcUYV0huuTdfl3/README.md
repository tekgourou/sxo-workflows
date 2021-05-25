[![published](https://static.production.devnetcloud.com/codeexchange/assets/images/devnet-published.svg)](https://developer.cisco.com/codeexchange/github/repo/tekgourou/SecureX-Workflows-Duo-Casebook-Sigthings)

# Cisco Secure Access by Duo - SecureX Orchestration workflows

Create SecureX Casebook and Sigthings based on Cisco Secure Access by Duo Auth DENIED or FRAUD logs.

Use cases : 
  - Track compromised Duo accounts
  - Track Access Device and Auth Device IP and or country mismatch
  - Track the potential source IP of guessing password scan
  - Block Duo user in CTR
  - Link cybercriminals IP(s) from a NGIPS event to a Duo denied authentication log during an investigation

For any questions or comments/bugs please reach out to me at alexandre@argeris.net or aargeris@cisco.com

![image](./img/Screen_Shot_Duo_fraud_casebook.png)
<br/>
![image](./img/Screen_Shot_Duo_CTR.png)
<br/>
![image](./img/Screen_Shot_Duo_Sigthings.png)
<br/>

# Main workflows:

- Events - Cisco Secure Access Fraud _ Deny auth.json  

This workflow will fetch Duo FRAUD logs detail from a Duo Fraud Email alert and Deny logs every 1hour. Detail will be parse to create a casebook and sigthings in SecureX platform. 
  
![image](./img/workflow2.png)
<br/>  

# Prerequisites:
Refence for best practice and documentation https://ciscosecurity.github.io/sxo-05-security-workflows/

- Create an Admin API application in Duo and save the credentials.
    https://duo.com/docs/adminapi
    
- Copy these credentials into Cisco SecureX Orchestration variable section:

  - Admin Integration Key (iKey), Host as a string variables [duo_admin_ikey], [duo_host]
  - Admin Secret Key (sKey) as a Secure string variable [duo_admin_skey]

- From the Duo Admin portal, configure Fraud Email Alert to be send to your IMAP account
![image](./img/Screen_Shot_duo_email_fraud_alert.png)


- Create the Duo Target based on the hostname in the Cisco SecureX Orchestration. 

  - Give a name, like "Duo"
  - No account keys: True
  - HTTPS protocol, host/IP address: API hostname
  - Proxy: Ignore Proxy
  
- Create a IMAP target and event

![image](./img/Screen_Shot_email_event.png)

# Import these workflows into SecureX Orchestration as atomic workflows:
  
- Threat Response v2 - Generate Access Token.json from https://github.com/CiscoSecurity/sxo-05-security-workflows/tree/Main/Atomics
  
  This Atomic workflow action will get CTR access token.

- Threat Response v2 - Create Casebook.json from https://github.com/CiscoSecurity/sxo-05-security-workflows/tree/Main/Atomics
  
  This Atomic workflow actions will create Casebook.  
  
- Duo Admin - Get DENIED or FRAUD Auth Logs.json from https://github.com/tekgourou/sxo-atomics/tree/main/duoAdminGetDeniedOrFraudAuthLogs__definition_workflow_01JYONCDVQVZ62K7SkNWdQCuAPUgfdRcFAF
  
  This Atomic workflow action will fetch Duo auth denied and fraud logs.

# Response

- End user can be notify in case a fraudulent authentification request. 

![image](./img/email2.jpeg)

# Remediation workflows

- Duo Admin - Block User By Username.json  

  This Atomics action block a Duo user based on username. (Work only if the Duo user is local - not sync with Azure AD or Win AD)
  credit to https://github.com/Gyuri1/duo-sxo
  
- Quarantine Duo User.json
  This workflow give you access to quarantine user in Duo from the SecureX AO contextuel menu.
  
