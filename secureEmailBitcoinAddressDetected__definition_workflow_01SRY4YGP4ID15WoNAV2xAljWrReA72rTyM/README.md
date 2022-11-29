# Cisco Secure Email Bitcoin Address Detected

This workflow monitors a SecureX mailbox for incoming email with Bitcoin Address detected by Cisco Secure Email. When an email is received, the workflow get report from Bitcoinabuse for Bitcoin Address reputation. URL will be parse from the email body and send to Cisco Malware Analytics. A suspicious judgment will be set for Observables from the email. SecureX Casebook will be create with all details.

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
    * IMAP inbox
    * The targets and account keys listed at the bottom of the page
