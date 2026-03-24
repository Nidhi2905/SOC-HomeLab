# Analysis Report

## Summary

Activity was generated on a Windows endpoint to simulate command execution followed by external communication.

---

## Observed Behaviour

### Process Execution

* PowerShell was executed on the system
* Command: whoami

### Network Activity

* Outbound connection to external system
* Port: 4444

---

## Correlation

The process execution event (Event ID 1) was followed by a network connection event (Event ID 3).

This sequence indicates that a command was executed and the system subsequently communicated externally.

---

## Interpretation

This pattern aligns with behaviour often seen during:

* Remote command execution
* Command-and-control communication

---

## Conclusion

By correlating process and network events, it is possible to identify activity that may otherwise appear normal when viewed in isolation.

