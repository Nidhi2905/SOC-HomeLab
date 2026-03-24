# Detection Queries

## PowerShell Execution Monitoring

```
EventCode=1 Image="*powershell.exe"
```

Detects execution of PowerShell on the endpoint.

---

## Network Connection Monitoring

```
EventCode=3 DestinationPort=4444
```

Filters network connections to the port used in the lab.

---

## Combined Activity View

```
EventCode=1 OR EventCode=3
```

Used to review process execution alongside network activity.

---

## Investigation Approach

* Identify suspicious process execution (PowerShell)
* Check for corresponding network connections
* Correlate timestamps between events

