# Cisco Secure Email Bitcoin Address Detected

This workflow monitors a SecureX mailbox for incoming email with Bitcoin Address detected by Cisco Secure Email. When an email is received, the workflow get report from Bitcoinabuse for Bitcoin Address reputation. URL will be parse from the email body and send to Cisco Malware Analytics. A suspicious judgment will be set for Observables from the email. SecureX Casebook will be create with all details.
