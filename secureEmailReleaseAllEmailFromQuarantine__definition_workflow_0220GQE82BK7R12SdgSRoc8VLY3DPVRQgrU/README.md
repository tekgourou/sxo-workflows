# Cisco Secure Email SMA quarantine release all emails

This workflow release all emails from a specific Cisco Secure Email SMA quarantine. 

## Configuration

## Targets
Target Group: `Default TargetGroup`

By default, the `Default TargetGroup` may not include `SMTP Endpoint` targets. If this is the case, you will need to update the target group and add `SMTP Endpoint` to the target types included.

| Target Name | Type | Details | Account Keys | Notes |
|:------------|:-----|:--------|:-------------|:------|
|Cisco Secure Email - SMA| HTTP Endpoint | _Protocol:_ `HTTPS`<br />_Host:_ `YOUR SMA URL`<br />_Path:_ `` | Cisco Secure EMAIL - SMA | Created by default |
| SMTP endpoint | SMTP Endpoint | Configured for your SMTP Credentials | |

## Account Keys

| Account Key Name | Type | Details | Notes |
|:-----------------|:-----|:--------|:------|
| Cisco Secure Email - SMA | HTTP Basic | Username: API_user Username<br /> Password: API_password | |
