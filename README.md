# OSQuery-Searches

OSquery allows you to query your devices like a database. It uses SQL commands to leverage a relational data-model to describe a device. Some EDR's come with it bundled in or you can download the software separately at https://osquery.io/

Below are some adhoc queries I've found to be useful:

### Rogue svchost
```SQL
SELECT * FROM processes WHERE name like 'svchost.exe' AND NOT path = "c:\windows\system32\";
```

### Listening Ports
```SQL
SELECT
op.pid,
op.local_address,
op.remote_address,
op.local_port,
op.remote_port,
op.state,'LISTEN',
p.path,
p.name,
p.cmdline
FROM process_open_sockets AS op
 JOIN processes AS p USING(pid);
```
### Check CurrentUser Run Registry key
```SQL
SELECT key, path, name, type, data FROM registry WHERE path like 'HKEY_USERS\%\Software\Microsoft\Windows\CurrentVersion\Run\%';
```
