# Check_mk notification script for MS Teams

## Introduction

This is a script designed to bounce Check_MK/OMD notifications 
into a MS Teams Channel, using Incoming Webhooks API.

## HOW TO USE:

1) Create an incoming webhook in your teams room and note down the URL.

2) Put into /usr/(local/)share/check_mk/notifications (or 
~/share/check_mk/notifications on OMD installs) directory and 
edit configuration variables in the 'msteams' script, and make 
sure that the script is executable (chmod +x msteams)

3) Create a user for msteams in WATO, use flexible custom notifications and 
select 'CMK-MSTeams Websocket integration' as the notifier.

4) Wait for something to send an alert or generate a test alert.

## Good to know

I haven't tested this with Notification Bulking (in newer cmk 
releases), I assume it doesn't work. Where it has been used 
bulk notification setups, bulking for the msteams script has 
been explicitly disabled.

Requires "requests", so `apt-get install python-requests` or `pip install requests`

### Test it

if you want to test if you have configured the slack script correcty you can try:
```
export NOTIFY_HOSTNAME=TestHost
export NOTIFY_WHAT=""
export NOTIFY_HOSTACKCOMMENT=false
export NOTIFY_NOTIFICATIONAUTHOR=""
export NOTIFY_HOSTSTATE=DOWN
export NOTIFY_NOTIFICATIONTYPE="WARNING"
```
