# SOC Homelab – Sysmon Detection Lab

## Overview

In this lab, I simulated attacker-like behaviour and analysed it using Sysmon logs to understand how activity appears at the endpoint level.

The focus was on identifying process execution and outbound network connections, and then correlating those events to build a clearer picture of what happened on the system.

---

## Environment

* VirtualBox lab environment
* Host-only network for isolation (Sandbox environment)
* Windows 10 machine with Sysmon installed (Victim)
* Kali Linux used to simulate attacker activity (Attacker)
* Separate Windows machine prepared for future Splunk integration (Analysis)

---

## Lab Setup

* Kali machine configured as a listener on port 4444 
* Windows machine used as the target system
* Sysmon configured to capture process creation and network connections

---

## Network Details

* Attacker (Kali): 192.168.20.11
* Victim (Windows): 192.168.20.10
* Port used: 4444

---

## Attack Simulation

To replicate attacker behaviour:

* A listener was started on the Kali machine
* The Windows system initiated a connection using PowerShell
* A command (`whoami`) was executed on the endpoint

This represents a scenario where a system executes a command and communicates externally.

---

## What I Observed

### Event ID 1 – Process Creation

* PowerShell execution was logged
* Command line showed the executed command (`whoami`)

This confirms command execution on the endpoint.

---

### Event ID 3 – Network Connection

* Outbound connection to the Kali machine
* Destination port: 4444

This shows the system communicating with an external host.

---

## Analysis

When viewed individually, these events may not immediately stand out. However, when correlated:

* PowerShell execution
* Followed by an outbound network connection

This sequence is something that would typically warrant further investigation in a SOC environment, as it can indicate command execution followed by external communication.

---

## Screenshots

### ![Home lab](main/Screenshots/Home-lab-overview.png)

### ![Kali Listener](Screenshots/Kalilistener.png)

### ![PowerShell Execution](powershellexecution.png)

### ![Event ID 3 - Network Connection](eventid3analysis.png)

### ![Event ID 1 - Process Creation](analysiseventid1.png)

### ![Sysmon Install](sysmoninstalled.png) 

---

## Detection Approach

Detection in this lab was based on:

* Monitoring PowerShell activity (Event ID 1)
* Reviewing outbound network connections (Event ID 3)
* Correlating both event types to understand the sequence of activity

---

## Project Structure

* screenshots/ → evidence from the lab
* queries/ → detection queries
* report/ → analysis summary

---

## Next Steps

* Forward logs into Splunk for centralised analysis
* Develop detection rules and alerts
* Test additional techniques such as encoded PowerShell or lateral movement scenarios

---

## Takeaway

This lab highlights how endpoint telemetry can be used to piece together activity on a system, and how correlating different event types provides better context during investigation.
