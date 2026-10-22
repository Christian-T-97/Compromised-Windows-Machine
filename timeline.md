<h1>Investigation Timeline</h1>

<h2>Purpose: This timeline organizes relevant observations, findings, and events collected during the Windows host investigation. It records timestamps, supporting evidence, and interpretations to practice reconstructing activity on a system.</h2>

------------------


<h3>Timeline:</h3>



Event #1: Initial system investigation began
   <br>
   Date and Time: Time not recorded
   <br>
   Evidence: Investigation notes
   <br>
   Interpretation: Established the starting point for the investigation

Event #2: Local accounts enumerated
<br>
   Date and Time: Time not recorded
   <br>
   Evidence: Screenshot: ![User enumeration](screenshots/01-Local accounts enumerated.png)
   <br>
   Interpretation: Recorded the existing accounts and their status

Event #3: Process and service baseline collected
<br>
   Date and Time: Time not recorded
   <br>
   Evidence: Screenshot: Process investigation, investigation-notes
   <br>
   Interpretation: Collected the number of processes and services running and investigated two processes deeper, uncovering their full path and purpose. 

Event #4: Network configurations and TCP connections examined
<br>
   Date and Time: Time not recorded
   <br>
   Evidence: Screenshot: Network configurations and connections, investigation-notes
   <br>
   Interpretation: Recorded the network configurations and connections observed

Event #5: Selected Windows event logs examined further
<br>
   Date and Time: 10/21/2026 6:59:09 PM
   <br>
   Evidence: Screenshot: Event log investigation-Event viewer-changed user account
   <br>
   Interpretation: reviewed available event evidence on a User account change of ID 4738

Event #6: LabTestUser created
<br>
   Date and Time: 10/22/2026 3:07:54 AM
   <br>
   Evidence: Screenshot: Simulated event - creating user
   <br>
   Interpretation: Confirmed the creation of the controlled account via PowerShell

Event #7: Account-creation event observed
<br>
   Date and Time: 10/22/2026 3:07:54 AM
   <br>
   Evidence: Screenshot: Evidence of new user - Event viewer
   <br>
   Interpretation: Corroborated the action using Windows security logs
   
   
   
