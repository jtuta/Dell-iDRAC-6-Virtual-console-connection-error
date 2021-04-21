# Dell iDRAC 6 Virtual console connection error

**TL;DR; Downgrade Java from 8 to Java 7 - build 79 and your problems are solved if you encounter this.**

I am system administrator for national Scouting organizator in my country and a few days ago I had to preform some tasks on our two Dell R510 servers that are equipped with Integrated Dell Remote Access Controller 6 - enterprise version (iDRAC6).  After connecting over Cisco VPN, I could access the iDRAC web application, but after launching Virtual console, connection returned error: **"Connection failed."**.

![error](https://user-images.githubusercontent.com/15046120/115597420-8a7d4300-a2d9-11eb-899e-222666240d15.png)

I already had problems with Javas security permissions and iDRAC virtual console, so firstly I went to Java Security settings and  I changed settings to allow everything - from false certificates to unknown sources and everything in-between. After retrying I still got error and enabling console gave me following error:

```
java.util.prefs.WindowsPreferences <int>
WARNING: Could not open/create prefs root node Software\JavaSoft\Prefs at root 0 ...

Starting Client
====setPowerMenuStatus: (##2)

ProtocolAPCP: Version [1.0]

Connection failed.
```

After trying literally everything (changing virtual console settings in iDRAC, resetting iDRAC, updating iDRAC to latest version, even changing registry as suggested by: [1](https://coderanch.com/t/635066/java/create-prefs-warning-Windows) and [2](https://stackoverflow.com/questions/5354838/java-java-util-preferences-failing) ) i stil could not connect. I don't remember if registry changes solved that java.util.prefs.WindowsPreferences error, but nevertheless I still could not connect to virtual console.  Last option coming to my mind was to downgrade Java from 8 to 7. In short this helped.

I have latest iDRAC updates installed (version 2.85 ) released in May 2016 - way later than last public Java 7 release on java.com (April 14, 2015)

![java7](https://user-images.githubusercontent.com/15046120/115597392-83563500-a2d9-11eb-896f-9e26822e1d46.png)

*This has previously been published on my wordpress blog at https://jure.tuta.si/?p=120 which has been since moved offline*
