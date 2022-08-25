# OSQuery-Searches

OSquery allows you to query your devices like a database. It uses SQL commands to leverage a relational data-model to describe a device. Some EDR's come with it bundled in or you can download the software separately at https://osquery.io/

Below are some adhoc queries I've found to be useful:

### Rogue svchost
```
SELECT * FROM processes WHERE name like 'svchost.exe' AND NOT path = "c:\windows\system32\";
```
