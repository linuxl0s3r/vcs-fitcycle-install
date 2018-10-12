#!/bin/bash
#Place this file in /etc/cron.hourly
#Place the serverlist file in a directory called /generatessh on MGMT

LINUX_COMMAND='uptime'

for i in `cat /generatessh/serverlist`
do
    ssh ${i} ${LINUX_COMMAND}
done