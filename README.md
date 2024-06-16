<h1>SIEM Azure Sentinel with Live Attacks Home Lab</h1>

<h2>Description</h2>
Project consists of using Microssoft Azure to build a SIEM to track live attacks for a single VM that is exposed to the internet. The goal is to assess the possiblities of attackers trying to Brute force 
<br />


<h2>Languages and Utilities Used</h2>

- <b>Microsoft Azure</b>
- <b>Sentinel</b>
- <b>Log Analytics Workspace</b>
- <b>Virtual Machine</b>
- <b>PowerShell ISO</b>
- <b>Event Viewer</b>

<h2>Environments Used </h2>

- <b>Windows 10 Pro</b> (22H2)

<h2>Layout of the Project:</h2>

<p align="center">
Project goal: <br/>
<img src="https://i.imgur.com/IKkyYyz.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />

<h2>Build walk-through Step 1 (VM Setup):</h2>

<p align="center">
<br />
<mark>Starting up Azure (Using the free subscription):</mark> <br/>
<img src="https://i.imgur.com/cqC7JpG.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<br />
<mark>Using Azure I create a Windows VM to be exposed for attackers to attempt logins:</mark> <br/>
<img src="https://i.imgur.com/vN7Q8QO.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<br />
<mark>VM creation settings:</mark>  <br/>
<img src="https://i.imgur.com/EmcEYaf.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<br />
<mark>Naming the VM as Honeypotlab:</mark>  <br/>
<img src="https://i.imgur.com/LA3593B.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<br />
<mark>Selected Windows 10 Pro (22H2) image for the VM:</mark>  <br/>
<img src="https://i.imgur.com/purRcv5.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<br />
<mark>VM user creation:</mark> <br/>
<img src="https://i.imgur.com/jLkdtTV.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>VM Disk settings:</mark>  <br/>
<img src="https://i.imgur.com/ZW9O1EK.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>VM networking :</mark>  <br/>
<img src="https://i.imgur.com/hRIuTqm.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>VM network rule creation :</mark>  <br/>
<img src="https://i.imgur.com/OVUjTHh.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>VM network, adding a new inbound rule to permit traffic anywhere and everywhere:</mark>  <br/>
<img src="https://i.imgur.com/FLYSjMY.png" height="80%" width="80%" alt="SIEM Building Steps"/>
 <br />
<mark>Proceed to add the rule :</mark>  <br/>
<img src="https://i.imgur.com/eJrE76k.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Review and create the VM :</mark>  <br/>
<img src="https://i.imgur.com/koQyaK6.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>VM creation validation :</mark>  <br/>
<img src="https://i.imgur.com/hIkmV0E.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Deploying the VM :</mark>  <br/>
<img src="https://i.imgur.com/KlvYEIO.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>VM completed :</mark>  <br/>
<img src="https://i.imgur.com/5feBRXf.png" height="80%" width="80%" alt="SIEM Building Steps"/> 
</p>

<h2>Build walk-through Step 2 (Log Analytics Workspace):</h2>
<p align="center">
<br />
<mark>Moving onto Log Analytics workspace:</mark> <br/>
<img src="https://i.imgur.com/Uk8kyyw.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>VM completed :</mark>  <br/>
<img src="https://i.imgur.com/5feBRXf.png" height="80%" width="80%" alt="SIEM Building Steps"/> 

</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
