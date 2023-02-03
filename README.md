# Linux_AutoRebooting_Script
This Script can reboot your linux server automatically on a given time



1. Create a new systemd service file with sudo nano /etc/systemd/system/reboot.service and paste the following:

[Unit]
Description=Reboot

[Service]
Type=oneshot
ExecStart=/sbin/reboot

2. Create a new systemd timer file with sudo nano /etc/systemd/system/reboot.timer and paste the following:

[Unit]
Description=Reboot every 30 minutes

[Timer]
OnBootSec=15min
OnUnitActiveSec=30min

[Install]
WantedBy=timers.target
 
 
3. Enable the timer to start on boot with sudo systemctl enable reboot.timer'

4. Start the timer with sudo systemctl start reboot.timer'

You can check the status of a systemd timer by using the systemctl command. Here are a few examples of how to check the status of a timer called "reboot.timer":

To check if the timer is currently active, use the command:

        systemctl is-active reboot.timer


This command will return "active" if the timer is currently running, and "inactive" if it is not.

To check the next scheduled time that the timer will run, use the command:


        systemctl list-timers --all
        
This command will list all timers on the system and show the next scheduled time for each one.

To check the status of the timer service, use the command:

        systemctl status reboot.timer
        
        
This command will provide detailed information on the current status of the timer, including whether it is running, when it was last started, and any errors that have occurred.



To check the logs of the timer service, use the command:


        journalctl -u reboot.timer
        
        
This command will show the log entries of the timer service, in case you are facing some issues and want to diagnose it.

You can also use systemctl list-timers --all to check all timers on the system, and check the name of your timer to check the status.




