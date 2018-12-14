# Linux notes

Replace text in a file: four -> tesera
```
$ sed -i -e 's/four/tesera/g' numbers.txt 
```

Find a file under current dir:
```
$ find . -name filename.*
```

Find any file containing specified text or regex:
```
$ grep -r "search\stext" *
```

Make a file executable:
```
$ chmod +x filename 
```

Get IP addresses:
```
$ ip addr show 
```
