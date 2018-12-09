# smartthings-sensor_open_close
_Smartthing SmartApp that monitors sensors opening and closing and sends SMS notifications to up to two recipients_

## Features
I couldn't find another App that allowed for SMS's to be sent to two phones numbers.  So I added that feature.

Lets you select multiple sensors, whether you want to monitor open and/or close an

SMS contains timestamp to the second, including timezone info, and which sensor fired which event

E.g.
```
Sun, Dec 9 12:16:13 AM (EST) 
Kitchen Door changed to 
CLOSED
```

## Notes
When working with the EcoLink Z-Wave plus sensors I noticed that they consistantly send TWO events each time they are opened or closed.

Because of this, if you use most SmartApps to send notifications of events you will get duplicates.  To work around this I am writing to [atomic state](https://docs.smartthings.com/en/latest/smartapp-developers-guide/state.html#state-and-atomic-state-overview) with a value of the last timestamp of an update.  Then I check if it's been at least 500ms since the last event was handled.  If so, I handle the event.


### Todo
- add the ability to also send in-app notifications.  (Easily done, but they weren't important to me so I left this out)
