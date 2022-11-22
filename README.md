# 2420_week11_Lab
**[My GitHub Repo]** ***(https://github.com/loiderson/2420_week11_Lab)***

**ASSUMPTIONS**

- You have watched and completed the DO video tutorial in the D2L.
- You have some sort of knowledge of the following commands and functionality:
```
rsync
redirects for example, the append: ">>"
#!/bin/bash scripts
```

# 2420 Week 11 Lab

## Co-Authors
  1. Jacob Lloyderson
  2. Coburn Nguyen

## Backup 

The backup service will backup a directory from one server to a backup server every Friday at 01:00

### config.sh

  1. Copy the configuration file into the opt

    sudo cp .git/2420_week11_Lab/config.sh /opt

  2. Set the FILE_PATH_COPY variable to the path of the directory you want to backup

  3. Set the IP_DESTINATION variable to  IP of your designated backup server

  ***### backup-script***

  1. Copy the backup script into the opt

    sudo cp .git/2420_week11_Lab/backup-script /opt

  2. Call the confirguration file

    . /opt/backup-file

  3. Than use rsync with the variables from the confirguration files

    rsync -r ${FILE_PATH_COPY} backup-user@${IP_DESTINATION}:/home/backup-user/Backup -e "ssh -i ~/.ssh/backup-server-KEY"
 
  ***### backup-service***

  1. Copy the service file into the systemd

    sudo cp .git/2420_week11_Lab/backup-service.service /etc/systemd/system

  2. Reload the Service

    sudo systemctl daemon-reload

  3. Starting the Service

    sudo systemctl start backup.service

  4. Enabling the Service

    sudo systemctl enable --now backup.service

  5. Checking the Service

    systemctl status backup.service

    ***### backup-timer***

  1. Copy the Timer file into the systemd

    sudo cp .git/2420_week11_Lab/backup-timer.timer /etc/systemd/system

  2. Starting the Timer

    sudo systemctl enable --now backup.timer

  3. Enabling the Timer

    sudo systemctl enable --now backup.timer

  4. Checking the Timer

    sytemctl list-timers
