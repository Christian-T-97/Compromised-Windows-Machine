# Compromised-Windows-Machine

# Windows Host Investigation Lab

## Overview

This project documents a hands-on investigation of a Windows 11 virtual machine using built-in Windows tools and PowerShell.

The objective was to establish a baseline of the system, examine key areas of activity, and practice identifying and investigating potentially suspicious indicators.

A controlled test scenario will be used to explore how system changes can be reflected in Windows event logs.

## Objectives

- Enumerate local user accounts and groups.
- Inspect running processes and Windows services.
- Examine network configuration and TCP connections.
- Explore Windows Event Logs.
- Review startup applications and potential persistence locations.
- Investigate unfamiliar executable files.
- Construct a timeline from observed evidence.

## Environment

- Operating system: Windows 11 VM
- Tools: PowerShell, Windows Event Viewer, built-in Windows utilities
- Environment: Personal virtual machine used for learning and testing

## Investigation Methodology

The investigation began with a baseline review of user accounts, processes, services, network activity, event logs, startup entries, and executable files.

PowerShell command discovery was also used to identify relevant commands and explore the available system information.

## Initial Findings

### Users and Groups
Documented local accounts and their enabled/disabled status.

### Processes and Services
Recorded process and service counts and began examining system activity.

### Network
Inspected the network profile, connectivity status, and active TCP connections.

### Event Logs
Identified available event logs and recorded entry counts.

### Startup and Persistence
Reviewed startup commands, registry Run entries, and scheduled tasks.

### File Investigation
Investigated an executable with an unexpected signature-check result. Further validation was required before drawing a conclusion about its legitimacy.

## Timeline

Timeline of these events and their relevant evidence including screenshots, paths, commands used.

## Limitations

The initial investigation was performed on a personal Windows VM. A baseline review alone cannot establish whether a system is compromised. Process counts, unfamiliar filenames, and signature-check errors are not sufficient proof of malicious activity.

## Lessons Learned
* Certain processes or executables may show a strange error while checking validity, this does not mean it is automatically malicious, you need to look at context and certain details such as location, CA, path, and provide overall deeper investigation to confirm its level of concern if any.
* Understanding how to move across a machine using various commands is essential in conducting a deep investigation.
* It is best to have an explorative curious mindset when doing certain projects, following the thread of curiosity can lead to a higher level of competence.

## Evidence

Screenshots and detailed investigation notes are stored in this repository.


