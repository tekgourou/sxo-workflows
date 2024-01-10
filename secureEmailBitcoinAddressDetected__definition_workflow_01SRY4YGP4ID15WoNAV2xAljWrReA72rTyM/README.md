# Cisco Secure Email Bitcoin Address Detected

This workflow monitors a Cisco XDR mailbox for incoming email with Bitcoin Address detected by Cisco Secure Email. When an email is received, the workflow get report from chainabuse for Bitcoin Address reputation. URL will be parse from the email body and send to Cisco Malware Analytics. A suspicious judgment will be set for Observables from the email. Cisco XDR Casebook will be create with all details.

![](img/email.png)

![](img/final.png)

## Extra information
	Cisco Live DevNet-2107 https://www.ciscolive.com/on-demand/on-demand-library.html?search=2107#/session/1655424246651001Q9zx
  
  ## Requirements
    * The following system atomics are used by this workflow:
    * Threat Response - Generated Access Token
    * Threat Response - Inspect for Observables
    * Secure Malware Analytics - Submit URL
    * Threat Response - Create Casebook
    * O365 inbox
    * Chainabuse API key.
    * The targets and account keys listed at the bottom of the page

## Workflow Steps

This workflow is designed to be triggered by an email arriving in a SecureX CES notification mailbox.

1.  Get Threat Response Access Token and Timestamp
2. For each email attach to the notification email:
	- Create a table with email headers.
3. For each headers:
	- Update variables with observable from the email headers.
4. If email matchl with Bitcoin Address regex
 	- Get Chainabuse report.
5. If email match with URL regex 
	- Submit URL to Cisco Secure Malware Analytics
6. Create observables json output.
7. Create Cisco XDR judgment for observables
8. Casebook is created. 

## Configuration

Variable/Account Keys/Targets
* Set local variable "Secure_Malware_Analytics" to "true" if you have a Cisco Secure Malware Analytics API subscription.
* Edit local variable "Secure_Malware_Analytics_API_key" to add your own api key.
* You must create an account key with your mailbox’s credentials and then update the SecureX CES notification Mailbox target with that account key. While you’re editing the target, be sure to add your email server’s information

## Targets
Target Group: `Default TargetGroup`

By default, the `Default TargetGroup` may not include `SMTP Endpoint` targets. If this is the case, you will need to update the target group and add `SMTP Endpoint` to the target types included.

| Target Name | Type | Details | Account Keys | Notes |
|:------------|:-----|:--------|:-------------|:------|
| CTR_API | HTTP Endpoint | _Protocol:_ `HTTPS`<br />_Host:_ `visibility.amp.cisco.com`<br />_Path:_ `/iroh` | CTR_Credentials | Created by default |
| SecureX Trigger IMAP Mailbox | IMAP Endpoint | Configured for your IMAP server |SecureX Trigger IMAP Mailbox Credentials | |
| Private_CTIA_Target | HTTP Endpoint | _Protocol:_ `HTTPS`<br />_Host:_ `private.intel.amp.cisco.com`<br />_Path:_ None | CTR_Credentials | Created by default |

## Account Keys

| Account Key Name | Type | Details | Notes |
|:-----------------|:-----|:--------|:------|
| SecureX Trigger IMAP Mailbox Credentials | Email Credentials | _Username:_ Mailbox Username<br />_Password:_ Mailbox Password | |
