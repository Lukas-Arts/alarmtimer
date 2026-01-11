# alarmtimer
An Alarm / Timer CLI-Tool with Notifications using notify-send.

A short notification appears, when an Alarm / Timer is started or killed. When an Alarm / Timer is finished, a critical notification is shown, that needs user-interaction to disappear.

Tasks/Alarms will be resumed after reboot using a ~/.config/autostart shortcut.

## Install

* download the script
* make the script executable (e.g. `chmod +x ./alarmtimer`)
* execute the script with `./alarmtimer -install`

This will:
* create the ~/scripts directory
* copy the script to ~/scripts/alarmtimer
* update ~/.profiles to include ~/scripts in $PATH
* create symlinks for 'alarm' and 'timer'
* create the ~/scripts/AlarmTimer directory to handle the Alarms / Timers
* create a ~/.config/autostart/alarmtimer.desktop to resume existing Timers / Alarms after reboot

## How to use

    alarmtimer <alarm name> <datetime>        Set Alarm/Timer. <datetime> uses the *date* syntax. So valid inputs may be '10mins', 'tomorrow 10', 'Monday 10:15', '10', '10:00' etc. 
    alarmtimer -k <alarm name>                Kill Alarm/Timer
    alarmtimer -l                             List running Alarms/Timer

### Exmaples

| Command | Description |
| ----------- | ----------- |
| timer pizza 12mins | creates a Timer called "pizza" that takes 12mins |
| alarm pizza 12mins | creates a Timer called "pizza" that takes 12mins |
| alarmtimer pizza 12mins | creates a Timer called "pizza" that takes 12mins |
| alarm bus 15:00 | creates an Alarm called "bus" that will trigger at 15:00 | 


**Tipp:** Add `${if_running timer}${execi 10 timer -l}${else}${if_running alarm}${execi 10 alarm -l}${else}${if_running alarmtimer}${execi 10 alarmtimer -l}$endif$endif$endif` to your conky-file to get a list of running alarms/timer with the time left
