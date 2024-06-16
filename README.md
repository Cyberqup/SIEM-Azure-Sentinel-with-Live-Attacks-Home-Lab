<h1>SIEM Azure Sentinel with Live Attacks Home Lab</h1>

<h2>Description</h2>
Project consists of using Microssoft Azure to build a SIEM to track live attacks for a single VM that is exposed to the internet. The goal is to assess the possiblities of attackers trying to Brute force and inform the follow reasons on why you shouldn't use default credentials and no matter how big or small the organisation/individual's are attackers will still try to brute force their way through to gain access.
<br />


<h2>Utilities Used</h2>

- <b>Microsoft Azure</b>
- <b>Sentinel</b>
- <b>Microsoft Defender for Cloud</b>
- <b>Log Analytics Workspace</b>
- <b>Virtual Machine</b>
- <b>PowerShell ISO</b>
- <b>Event Viewer</b>
- <b>Windows 10 Pro</b> (22H2)

<h2>Layout of the Project:</h2>

<p align="center">
<mark>Project goal:</mark> <br/>
<img src="https://i.imgur.com/NL8ioUi.png" height="80%" width="80%" alt="SIEM Building Steps"/>
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
<mark>Moving onto Log Analytics Workspace:</mark> <br/>
<img src="https://i.imgur.com/Uk8kyyw.png" height="50%" width="50%" alt="SIEM Building Steps"/>
<br />
<mark>Log Analytics Workspace Mainpage :</mark>  <br/>
<img src="https://i.imgur.com/kysqi1m.png" height="80%" width="80%" alt="SIEM Building Steps"/> 
<br />
<mark>Log creation settings filled out :</mark>  <br/>
<img src="https://i.imgur.com/LtfbDeT.png" height="80%" width="80%" alt="SIEM Building Steps"/> 
<br />
<mark>Log validation :</mark>  <br/>
<img src="https://i.imgur.com/02ieWRa.png" height="80%" width="80%" alt="SIEM Building Steps"/> 
<br />
<mark>Deployment of log success :</mark>  <br/>
<img src="https://i.imgur.com/NZtazgv.png" height="80%" width="80%" alt="SIEM Building Steps"/> 
</p>

<h2>Build walk-through Step 3 (Microsoft Defender for Cloud):</h2>
<p align="center">
<br />
<mark>Moving onto Microsoft Defender for Cloud:</mark> <br/>
<img src="https://i.imgur.com/jo77Ux5.png" height="50%" width="50%" alt="SIEM Building Steps"/>
<br />
<mark>Mainpage of Defender for Cloud:</mark> <br/>
<img src="https://i.imgur.com/35E4aUM.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Looking at the sidebar we move onto environment settings:</mark> <br/>
<img src="https://i.imgur.com/Ldhmm5Z.png" height="30%" width="30%" alt="SIEM Building Steps"/>
<br />
<mark>In environment setting we move onto the law-honeypot to turn on certain settings:</mark> <br/>
<img src="https://i.imgur.com/RhjKKy2.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>The following settings which are turned on:</mark> <br/>
<img src="https://i.imgur.com/gL75s8u.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Moving ontowards data collection selecting "ALL EVENTS":</mark> <br/>
<img src="https://i.imgur.com/sv4BVid.png" height="80%" width="80%" alt="SIEM Building Steps"/>
</p>

<h2>Build walk-through Step 3 (Microsoft Defender for Cloud):</h2>
<p align="center">
<br />
<mark>Moving back to Log Analytics Workspace:</mark> <br/>
<img src="https://i.imgur.com/yGpaJ3L.png" height="50%" width="50%" alt="SIEM Building Steps"/>
<br />
<mark>Enter into the Law-Honeypot:</mark> <br/>
<img src="https://i.imgur.com/etcGm6R.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Using the sidebar I find the Virtual Machine and proceed through :</mark> <br/>
<img src="https://i.imgur.com/q9GLHsa.png" height="30%" width="30%" alt="SIEM Building Steps"/>
<br />
<mark>Proceed to connect the VM with the workspace law-honeypot:</mark> <br/>
<img src="https://i.imgur.com/OsROCy6.png" height="50%" width="50%" alt="SIEM Building Steps"/>
<br />
<mark>Continuation:</mark> <br/>
<img src="https://i.imgur.com/jQvbjl6.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>VM connected with law-honeypot:</mark> <br/>
<img src="https://i.imgur.com/PkyRfPs.png" height="50%" width="50%" alt="SIEM Building Steps"/>
</p>

<h2>Build walk-through Step 4 (Microsoft Sentinel):</h2>
<p align="center">
<br />
<mark>Moving onto Sentinel:</mark> <br/>
<img src="https://i.imgur.com/RKPBkF4.png" height="50%" width="50%" alt="SIEM Building Steps"/>
<br />
<mark>Creating Sentinel:</mark> <br/>
<img src="https://i.imgur.com/ZojuRNU.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Adding Sentinel to the workspace law-honeypot:</mark> <br/>
<img src="https://i.imgur.com/Gd47Sjv.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Sentinel completed:</mark> <br/>
<img src="https://i.imgur.com/fsnPivm.png" height="80%" width="80%" alt="SIEM Building Steps"/>
</p>

<h2>Build walk-through Step 5 (Log Analytics Workspace):</h2>
<p align="center">
<br />
<mark>Moving back to Log Analytics Workspace:</mark> <br/>
<img src="https://i.imgur.com/jpYhyGK.png" height="50%" width="50%" alt="SIEM Building Steps"/>
<br />
<mark>Enter back into law-honeypot workspace:</mark> <br/>
<img src="https://i.imgur.com/pXAWgqg.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Enter into the Honeypot-VM:</mark> <br/>
<img src="https://i.imgur.com/xic0VSC.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Once in the VM information page we take and save the IP address to sign in using it later:</mark> <br/>
<img src="https://i.imgur.com/IXGcWGE.png" height="80%" width="80%" alt="SIEM Building Steps"/>
</p>

<h2>Build walk-through Step 6 (Using Remote Desktop Connection (RDP) to access the VM):</h2>
<p align="center">
<br />
<mark>Moving to the RDP VM and entering the VM IP address:</mark> <br/>
<img src="https://i.imgur.com/KWHiwvp.png" height="50%" width="50%" alt="SIEM Building Steps"/>
<br />
<mark>Connecting requires the credentials for the VM to sign in:</mark> <br/>
<img src="https://i.imgur.com/aNtmovr.png" height="50%" width="50%" alt="SIEM Building Steps"/>
<br />
<mark>Certificate not valid authorise to proceed through:</mark> <br/>
<img src="https://i.imgur.com/loVf22m.png" height="50%" width="50%" alt="SIEM Building Steps"/>
<br />
<mark>VM proceeding to login:</mark> <br/>
<img src="https://i.imgur.com/BGEDWk0.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>VM has loaded:</mark> <br/>
<img src="https://i.imgur.com/mjrdo6d.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>On the VM I open Event Viewer:</mark> <br/>
<img src="https://i.imgur.com/SX6vDB7.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Event Viewer application:</mark> <br/>
<img src="https://i.imgur.com/4HeFlPN.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Event Viewer Audit Logs:</mark> <br/>
<img src="https://i.imgur.com/xzg0cXB.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>While the VM is online I can reopen another RDP to try login with the wrong credentials to show an Audit Failure:</mark> <br/>
<img src="https://i.imgur.com/QROeHtU.png" height="50%" width="50%" alt="SIEM Building Steps"/>
<br />
<mark>Event Viewer showing Audit Failure:</mark> <br/>
<img src="https://i.imgur.com/GTwBZMa.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Event Viewer showing Audit Failure I pull the IP address and track:</mark> <br/>
<img src="https://i.imgur.com/R0xng92.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Go onto ipgeolocation.io to track IP source address and other details:</mark> <br/>
<img src="https://i.imgur.com/z6Fo1qN.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Going back to the main computer open CMD to try ping the VM, the VM pinging request timed out is due to the firewall still active on the VM:</mark> <br/>
<img src="https://i.imgur.com/knGERFA.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>On the VM desktop I move into the Firewall Advanced settings:</mark> <br/>
<img src="https://i.imgur.com/6hk0riv.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Firewall Advanced settings:</mark> <br/>
<img src="https://i.imgur.com/e81ATKl.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Enter "Windows Defender Firewall Properties" then turn off "Firewall state" for the following, Domain, Private, and Public profile:</mark> <br/>
<img src="https://i.imgur.com/9ho2ODJ.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Firewall Advanced settings all turned off:</mark> <br/>
<img src="https://i.imgur.com/aFtTd0C.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Re-trying ping command which shows feedback now:</mark> <br/>
<img src="https://i.imgur.com/OZ92Rli.png" height="80%" width="80%" alt="SIEM Building Steps"/>
</p>

<h2>Build walk-through Step 7 (VM PowerShell ISE Script):</h2>
<p align="center">
<br />
<mark>To relay log information to the SIEM I copy a custom script:</mark> <br/>
<img src="https://i.imgur.com/IlolTWQ.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Opening PowerShell ISE on the VM:</mark> <br/>
<img src="https://i.imgur.com/SdyjskL.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>PowerShell ISE:</mark> <br/>
<img src="https://i.imgur.com/SVLAUhj.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>PowerShell ISE create new file:</mark> <br/>
<img src="https://i.imgur.com/9MqKaSn.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>PowerShell ISE paste the custom script into the file:</mark> <br/>
<img src="https://i.imgur.com/59KcDOu.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Moving onto the geolocation website I needed to create an account to grab an API key for the custom script to work and gather geolocation information to graph out into the live map:</mark> <br/>
<img src="https://i.imgur.com/OLKj1j3.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<img src="https://i.imgur.com/80Let9f.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Insert API key into the custom script:</mark> <br/>
<img src="https://i.imgur.com/1Vi58vr.png" height="50%" width="50%" alt="SIEM Building Steps"/>
<br />
<mark>Test run the script to see if it pulls data from the failed login attempts that I've created earlier:</mark> <br/>
<img src="https://i.imgur.com/FTEVGi0.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Script logs are captured into the following directory and file labaled as "failed_rdp":</mark> <br/>
<img src="https://i.imgur.com/F1v6vEp.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>"failed_rdp" file captures information in the follow layout:</mark> <br/>
<img src="https://i.imgur.com/NfK7FHl.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Test another fail login attempt to see if this tracks:</mark> <br/>
<img src="https://i.imgur.com/g1u0qXl.png" height="30%" width="30%" alt="SIEM Building Steps"/>
<br />
<mark>As shown in the PowerShell ISE, it shows the new failed login attempt user "iamwrong":</mark> <br/>
<img src="https://i.imgur.com/A0s5uLY.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>As shown in "filed_rdp" file, it shows the new failed login attempt user "iamwrong":</mark> <br/>
<img src="https://i.imgur.com/vtwj72c.png" height="80%" width="80%" alt="SIEM Building Steps"/>
</p>

<h2>Build walk-through Step 8 (Log Analytics Workspace - Custom Logs):</h2>
<p align="center">
<br />
<mark>Moving onto Log Analytics Workspace > In the law-honeypot > To create a custom log:</mark> <br/>
<img src="https://i.imgur.com/nV0OW4j.png" height="50%" width="50%" alt="SIEM Building Steps"/>
<br />
<mark>Creating a new custom log (MMA-based):</mark> <br/>
<img src="https://i.imgur.com/mt3He3H.png" height="30%" width="30%" alt="SIEM Building Steps"/>
<br />
<mark>Custom Log creation process, firstly I needed a sample log:</mark> <br/>
<img src="https://i.imgur.com/jSsRAWJ.png" height="50%" width="50%" alt="SIEM Building Steps"/>
<br />
<mark>Sample log is taken from the "failed_rdp" file by copying it to transfer over to the main computer to then create a sample log for the custom log to analyse:</mark> <br/>
<img src="https://i.imgur.com/v7LgVhC.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Copied over from the "failed_rdp" file to the main computer for the sample log to proceed:</mark> <br/>
<img src="https://i.imgur.com/N4iWd0C.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<img src="https://i.imgur.com/EN8a8HU.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Sample log uploaded:</mark> <br/>
<img src="https://i.imgur.com/910Io5E.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Custom log with correct path in the VM to pull the "failed_rdp" logs:</mark> <br/>
<img src="https://i.imgur.com/blT9N8Q.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Create a custom log name = "FAILED_RDP_WITH_GEO":</mark> <br/>
<img src="https://i.imgur.com/4xzGouw.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Finally create the custom log:</mark> <br/>
<img src="https://i.imgur.com/0KeKmcr.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<img src="https://i.imgur.com/l0j6zVu.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Moving to Logs within Log Analytics Workspace > law-honeypot > Logs:</mark> <br/>
<img src="https://i.imgur.com/AAFlxtR.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Start a New Query and Test the "FAILED_RDP_WITH_GEO_CL. In some circumstances results may not show up this is due to the system need time to update this may take up to 20 minutes until it can show the proper results:</mark> <br/>
<img src="https://i.imgur.com/9Xub4sq.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Run "SecurityEvent" to see the Windows Event Viewer logs:</mark> <br/>
<img src="https://i.imgur.com/kqlq4MN.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Adding more commands where eventID is equal to 4625 will show the failed login attempts:</mark> <br/>
<img src="https://i.imgur.com/KYq9Zzb.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>After 20 minutes retry "FAILED_RDP_WITH_GEO_CL" now shows that it has been updated and fully loaded through:</mark> <br/>
<img src="https://i.imgur.com/7VGa3Ln.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>The VM is now being recongised around the world and starting to get attacked:</mark> <br/>
<img src="https://i.imgur.com/LkvGnfs.png" height="80%" width="80%" alt="SIEM Building Steps"/>
</p>

<h2>Build walk-through Step 9 (Live Attacks shown on a map):</h2>
<p align="center">
<br />
<mark>On the same query pull certain extracts from the logs with the following commands:</mark> <br/>
<img src="https://i.imgur.com/w622nlB.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Moving to Sentinel add a new workbook:</mark> <br/>
<img src="https://i.imgur.com/qhrqc7W.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Remove the prefilled data and start a fresh empty workbook then add:</mark> <br/>
<img src="https://i.imgur.com/SrxvKGo.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<img src="https://i.imgur.com/9h0zPWb.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Run the following query with a custom commands extracting certain data to plot onto the map:</mark> <br/>
<img src="https://i.imgur.com/wT32HQW.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Set visualisation as map to show failed login attempts:</mark> <br/>
<img src="https://i.imgur.com/Pg3ES7P.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<mark>Map settings are adjusted to prefences then applied and saved:</mark> <br/>
<img src="https://i.imgur.com/2kKlSuB.png" height="40%" width="40%" alt="SIEM Building Steps"/>
<img src="https://i.imgur.com/Kekfhdh.png" height="40%" width="40%" alt="SIEM Building Steps"/>
<img src="https://i.imgur.com/YZd5ZFv.png" height="50%" width="50%" alt="SIEM Building Steps"/>
<br />
<mark>This is the final capture before close the Honeypot-vm that was left for approximately 12 hours:</mark> <br/>
<img src="https://i.imgur.com/SwD10HC.png" height="80%" width="80%" alt="SIEM Building Steps"/>



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
