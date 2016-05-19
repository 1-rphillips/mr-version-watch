# mr-version-watch
[under construction]

This is a bash script that interacts with a blink(1) usb device to indicate that an updated version of MunkiReport-PHP is available, called by a launchAgent at a specified time. The script pulls the current version of a designated instance of MunkiReport-PHP (i.e., your MR-PHP server), and compares against the latest version found at https://github.com/munkireport/munkireport-php/releases . If the latest version is newer (higher version number) than the instance's current version, the latest version is downloaded locally and the blink(1) device lights up. If the instance's current version is equal to the latest version, the script finishes and nothing else occurs. I suppose it is possible to be running a version greater than the latest version - say, in testing or similar - but this is not accounted for here, NB.


The following assumptions are present:

- OS X, only tested with 10.10 & 10.11
- the script ("MRversionWatch.sh") lives at /Library/Networks/ and has appropriate execute permissions
- the host system has a blink(1) usb device connected [see: https://blink1.thingm.com/ ]
- the blink1Control.app bundle is present at /Applications [see: https://github.com/thingm/blink1/ ]
- the blink1 API server is able to run locally


LaunchAgent Configuration:
- modify ProgramArguments to change the path to MRversionWatch.sh (if a location other than /Library/Networks is desired)
- modify StartCalendarInterval values to change the time at which MRversionWatch.sh is called

Script Configuration:
- modify savePath to point to the place where downloaded new releases of MunkiReport-PHP should be saved
- modify designatedServerPlistURL to reflect the URL of the MunkiReport-PHP server desired, with the full path being something like https://munkireport.your.org/index.php?/install/plist <--- not a real URL


