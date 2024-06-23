<h1>SIEM Azure Sentinel with Live Attacks Home Lab</h1>

<h2>Description</h2>
This project provides a comprehensive guide on building a Security Information and Event Management (SIEM) system with Azure Sentinel, aimed at tracking live RDP brute force attacks worldwide and plotting them on a map. The map displays data related to the attacks, such as country, IP address, username, and more.
<br />

<h2>Utilities Used</h2>
<table>
 <tr>
  <td>Microsoft Azure</td>
  <td>Sentinel</td>
 </tr>
 <tr>
  <td>Defender for Cloud</td>
  <td>Log Analytics Workspace</td>
 </tr>
 <tr>
  <td>Virtual Machine</td>
  <td>PowerShell ISO</td>
 </tr>
 <tr>
  <td>Event Viewer</td>
  <td>Windows 10 Pro (22H2)</td>
 </tr>
</table>
<br/>

<h2>Instructions</h2>

<p align="center">
<strong><mark>Project Diagram</mark></strong> <br/>
<img src="https://i.imgur.com/NL8ioUi.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />

 <h2>Section 1 - VM Setup</h2>

<p align="center">
<br />
<mark>Whilst using Azure this is the main hub page. First step is to setup a VM to be the device of vulnerability (honeypot). To do so we must use <strong>"deploy a virtual machine"</strong>.</mark> <br/>
<img src="https://i.imgur.com/cqC7JpG.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<br />
<mark>Creating a Windows VM (Virtual Machine) to be exposed for attackers to attempt RDP (Remote Desktop Protocol) logins.</mark> <br/>
<img src="https://i.imgur.com/vN7Q8QO.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<br />
<mark>Moving on to the creation process for the VM, proceeding through the settings to deploy.</mark>  <br/>
<img src="https://i.imgur.com/EmcEYaf.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<br />
<mark>As shown below in the image, I <strong>"Create new"</strong> and name the VM <strong>"Honeypotlab"</strong> then proceeding to hit <strong>"OK"</strong>.</mark>  <br/>
<img src="https://i.imgur.com/LA3593B.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<br />
<mark>Moving along through <strong>"Instance details"</strong> filling in further details and selecting Windows 10 Pro (22H2) <strong>"Image"</strong> for the VM</mark>  <br/>
<img src="https://i.imgur.com/purRcv5.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<br />
<mark>Moving down the page to setup the VM Administrator account as shown in the image below. Selecting <strong>"Allow selected ports"</strong>, setting inbound ports as <strong>"RDP 3389"</strong> and finally confirming the licensing tick box to proceed over to <strong>"Disks"</strong>.</mark> <br/>
<img src="https://i.imgur.com/jLkdtTV.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
<br />
<mark>Follow up to the <strong>"Disk"</strong> page, and setting up the basic needs for the VM.</mark>  <br/>
<img src="https://i.imgur.com/ZW9O1EK.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Moving on to the <strong>"Networking"</strong> page, only setting I changed are <strong>"NIC network security group"</strong> set to <strong>"Advanced"</strong> and moving onto <strong>"Configure network security group"</strong> I create new and proceed through as shown below.</mark>  <br/>
<img src="https://i.imgur.com/hRIuTqm.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>This following image shows the follow up from selecting <strong>"create new"</strong>. This preset rule has to be deleted for the custom rule.</mark>  <br/>
<img src="https://i.imgur.com/OVUjTHh.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Once preset is deleted, I <strong>"Add an inbound rule"</strong> and set the following changes <strong>"Destination port ranges" to *, "Priority" to 100, and "Name" to Danger_any_in</strong> and proceed to add the rule.</mark>  <br/>
<img src="https://i.imgur.com/FLYSjMY.png" height="80%" width="80%" alt="SIEM Building Steps"/>
 <br />
 <br />
<mark>Once the rule is added it'll display the following.</mark>  <br/>
<img src="https://i.imgur.com/eJrE76k.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Finally <strong>"review + create"</strong> the VM.</mark>  <br/>
<img src="https://i.imgur.com/koQyaK6.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>VM creation validation passed as shown.</mark>  <br/>
<img src="https://i.imgur.com/hIkmV0E.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Proceeding to deploy the VM.</mark>  <br/>
<img src="https://i.imgur.com/KlvYEIO.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>VM deployment completed.</mark>  <br/>
<img src="https://i.imgur.com/5feBRXf.png" height="80%" width="80%" alt="SIEM Building Steps"/> 
</p>

<h2>Section 2 - Log Analytics Workspace</h2>
<p align="center">
<br />
<mark>Moving to Log Analytics Workspace.</mark> <br/>
<img src="https://i.imgur.com/Uk8kyyw.png" height="50%" width="50%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Log Analytics Workspace main page. Proceeding to <strong>"Create log analytics workspace"</strong>.</mark>  <br/>
<img src="https://i.imgur.com/kysqi1m.png" height="80%" width="80%" alt="SIEM Building Steps"/> 
<br />
 <br />
<mark>Proceeding through the creation of the workspace selecting from <strong>"Resource group"</strong> Honeypotlab and <strong>"Instance details" - Name</strong> law-honeypot, continuing to <strong>"Review + Create"</strong>.</mark>  <br/>
<img src="https://i.imgur.com/LtfbDeT.png" height="80%" width="80%" alt="SIEM Building Steps"/> 
<br />
 <br />
<mark>Validation passed after <strong>"Review + Create"</strong>.</mark>  <br/>
<img src="https://i.imgur.com/02ieWRa.png" height="80%" width="80%" alt="SIEM Building Steps"/> 
<br />
 <br />
<mark>Deployment completed.</mark>  <br/>
<img src="https://i.imgur.com/NZtazgv.png" height="80%" width="80%" alt="SIEM Building Steps"/> 
</p>

<h2>Section 3 - Microsoft Defender for Cloud</h2>
<p align="center">
<br />
<mark>Moving onto Microsoft Defender for Cloud.</mark> <br/>
<img src="https://i.imgur.com/jo77Ux5.png" height="50%" width="50%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Main page of Defender for Cloud.</mark> <br/>
<img src="https://i.imgur.com/35E4aUM.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Looking at the sidebar I proceed into environment settings.</mark> <br/>
<img src="https://i.imgur.com/Ldhmm5Z.png" height="30%" width="30%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>In environment setting I move onto the law-honeypot to turn <strong>"On"</strong> plans.</mark> <br/>
<img src="https://i.imgur.com/RhjKKy2.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>As shown below the 2 following defender plans are turned <strong>"On"</strong>.</mark> <br/>
<img src="https://i.imgur.com/gL75s8u.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Moving ontowards <strong>"data collection"</strong> selecting <strong>"ALL EVENTS"</strong> and save the following changes.</mark> <br/>
<img src="https://i.imgur.com/sv4BVid.png" height="80%" width="80%" alt="SIEM Building Steps"/>
</p>

<h2>Section 4 - Connecting VM to Law-Honeypot</h2>
<p align="center">
<br />
<mark>Moving back to Log Analytics Workspace.</mark> <br/>
<img src="https://i.imgur.com/yGpaJ3L.png" height="50%" width="50%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Enter into the Law-Honeypot.</mark> <br/>
<img src="https://i.imgur.com/etcGm6R.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Using the sidebar I proceed into <strong>"Virtual Machine"</strong>.</mark> <br/>
<img src="https://i.imgur.com/q9GLHsa.png" height="20%" width="20%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Proceed to connect the VM with the workspace law-honeypot.</mark> <br/>
<img src="https://i.imgur.com/OsROCy6.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Proceed to connect.</mark> <br/>
<img src="https://i.imgur.com/jQvbjl6.png" height="50%" width="50%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>VM connected with law-honeypot.</mark> <br/>
<img src="https://i.imgur.com/PkyRfPs.png" height="50%" width="50%" alt="SIEM Building Steps"/>
</p>

<h2>Section 5 - Microsoft Sentinel</h2>
<p align="center">
<br />
<mark>Moving onto Sentinel.</mark> <br/>
<img src="https://i.imgur.com/RKPBkF4.png" height="50%" width="50%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Proceed to <strong>"Create Microsoft Sentinel"</strong>.</mark> <br/>
<img src="https://i.imgur.com/ZojuRNU.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Add Sentinel to the workspace law-honeypot.</mark> <br/>
<img src="https://i.imgur.com/Gd47Sjv.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Sentinel and law-honeypot workspaced is now linked.</mark> <br/>
<img src="https://i.imgur.com/fsnPivm.png" height="80%" width="80%" alt="SIEM Building Steps"/>
</p>

<h2>Section 6 - Log Analytics Workspace</h2>
<p align="center">
<br />
<mark>Moving back to Log Analytics Workspace.</mark> <br/>
<img src="https://i.imgur.com/jpYhyGK.png" height="50%" width="50%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Enter back into law-honeypot workspace.</mark> <br/>
<img src="https://i.imgur.com/pXAWgqg.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Enter into the Honeypot-VM as shown.</mark> <br/>
<img src="https://i.imgur.com/xic0VSC.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Once in the VM information page I take note of the IP address to sign in to the VM.</mark> <br/>
<img src="https://i.imgur.com/IXGcWGE.png" height="80%" width="80%" alt="SIEM Building Steps"/>
</p>

<h2>Section - 7 Using Remote Desktop Connection (RDP) to access the VM</h2>
<p align="center">
<br />
<mark>Moving to the RDP VM and entering the VM IP address.</mark> <br/>
<img src="https://i.imgur.com/KWHiwvp.png" height="50%" width="50%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Connecting requires the <strong>"Administrator credentials"</strong> that were created earlier during the VM setup.</mark> <br/>
<img src="https://i.imgur.com/aNtmovr.png" height="50%" width="50%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Once credentials are used to sign in the <strong>"Certificate"</strong> prompt shows that it's not valid but to continue we must authorise to proceed through.</mark> <br/>
<img src="https://i.imgur.com/loVf22m.png" height="50%" width="50%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>VM opening process.</mark> <br/>
<img src="https://i.imgur.com/BGEDWk0.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>VM loaded in.</mark> <br/>
<img src="https://i.imgur.com/mjrdo6d.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Once the VM is open, proceed into <strong>"Event Viewer"</strong>.</mark> <br/>
<img src="https://i.imgur.com/SX6vDB7.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>As shown this is the <strong>"Event Viewer"</strong> application.</mark> <br/>
<img src="https://i.imgur.com/4HeFlPN.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Following the image <strong>"Window Logs > Security"</strong> to show logs of login attempts successfully and unsuccessfully attempts to login.</mark> <br/>
<img src="https://i.imgur.com/xzg0cXB.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>While the VM is online I can reopen another RDP to try login with the wrong credentials to show an Audit Failure (Failed Login Attempt).</mark> <br/>
<img src="https://i.imgur.com/QROeHtU.png" height="50%" width="50%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Event Viewer showing the attempt as - Audit Failure.</mark> <br/>
<img src="https://i.imgur.com/GTwBZMa.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Event Viewer is showing the audit failure from the attempt made by me. By looking in deeper within the failure I can see the IP address and other information based on the attempt made.</mark> <br/>
<img src="https://i.imgur.com/R0xng92.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Moving onto <strong>"ipgeolocation.io"</strong> this is used to track IP source address and other details for the purpose of display data on the live map. Using the IP address for the recent Failure it shows the following information.</mark> <br/>
<img src="https://i.imgur.com/z6Fo1qN.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Going back to the main computer open CMD to try ping the VM, the VM pinging request timed out. This is due to the firewall still active on the VM preventing the pings.</mark> <br/>
<img src="https://i.imgur.com/knGERFA.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>On the VM desktop, I move into the Firewall Advanced settings.</mark> <br/>
<img src="https://i.imgur.com/6hk0riv.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Firewall Advanced settings.</mark> <br/>
<img src="https://i.imgur.com/e81ATKl.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Enter <strong>"Windows Defender Firewall Properties"</strong> then turn off <strong>"Firewall state"</strong> for the following, Domain, Private, and Public profile.</mark> <br/>
<img src="https://i.imgur.com/9ho2ODJ.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Firewall Advanced settings all turned off.</mark> <br/>
<img src="https://i.imgur.com/aFtTd0C.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Proceed to re-try the ping command which shows feedback from the VM.</mark> <br/>
<img src="https://i.imgur.com/OZ92Rli.png" height="80%" width="80%" alt="SIEM Building Steps"/>
</p>

<h2>Section 8 - VM PowerShell ISE Script</h2>
<p align="center">
<br />
<mark>While still in the VM, to relay log information to the SIEM I copy a custom script from the following Github repository made by <strong>"Josh Madakor"</strong>. The script is for ipgeolocation.io to link with the SIEM to input data into a visulised map for the live attacks.</mark> <br/>
<img src="https://i.imgur.com/IlolTWQ.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Moving onto opening PowerShell ISE on the VM.</mark> <br/>
<img src="https://i.imgur.com/SdyjskL.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>PowerShell ISE.</mark> <br/>
<img src="https://i.imgur.com/SVLAUhj.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>PowerShell ISE create a new file.</mark> <br/>
<img src="https://i.imgur.com/9MqKaSn.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Paste the custom script into the file.</mark> <br/>
<img src="https://i.imgur.com/59KcDOu.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Moving onto the geolocation website I needed to create an account to grab a API key for the custom script to work and gather geolocation information to graph out into the live map.</mark> <br/>
<img src="https://i.imgur.com/OLKj1j3.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<img src="https://i.imgur.com/80Let9f.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Insert API key into the custom script.</mark> <br/>
<img src="https://i.imgur.com/1Vi58vr.png" height="50%" width="50%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Test run the script to see if it pulls data from the failed login attempts that I've created earlier.</mark> <br/>
<img src="https://i.imgur.com/FTEVGi0.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Script logs are captured into the following directory and file labaled as <strong>"failed_rdp"</strong>.</mark> <br/>
<img src="https://i.imgur.com/F1v6vEp.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark><strong>"failed_rdp"</strong> file captures information in the follow layout.</mark> <br/>
<img src="https://i.imgur.com/NfK7FHl.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Test another fail login attempt to see if this is tracked.</mark> <br/>
<img src="https://i.imgur.com/g1u0qXl.png" height="30%" width="30%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>As shown in the PowerShell ISE, it shows the new failed login attempt user "iamwrong".</mark> <br/>
<img src="https://i.imgur.com/A0s5uLY.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>As shown in <strong>"failed_rdp"</strong> file, it shows the new failed login attempt user "iamwrong".</mark> <br/>
<img src="https://i.imgur.com/vtwj72c.png" height="80%" width="80%" alt="SIEM Building Steps"/>
</p>

<h2>Section 9 - Log Analytics Workspace with Custom Logs</h2>
<p align="center">
<br />
<mark>Moving onto <strong>Log Analytics Workspace > In the law-honeypot > To create a custom log</strong>.</mark> <br/>
<img src="https://i.imgur.com/nV0OW4j.png" height="50%" width="50%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Creating a new custom log (MMA-based).</mark> <br/>
<img src="https://i.imgur.com/mt3He3H.png" height="30%" width="30%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>For the custom Log creation process, a sample log must be provided so the custom log can learn the data it will be extracting.</mark> <br/>
<img src="https://i.imgur.com/jSsRAWJ.png" height="50%" width="50%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>The sample log is extracted from the <strong>"failed_rdp"</strong> file by copying it to the main computer, where it is then used to create a sample log for the custom log to analyse.</mark> <br/>
<img src="https://i.imgur.com/v7LgVhC.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Submitting the sample log from the main computer on the custom log creation page.</mark> <br/>
<img src="https://i.imgur.com/N4iWd0C.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<img src="https://i.imgur.com/EN8a8HU.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Sample log uploaded.</mark> <br/>
<img src="https://i.imgur.com/910Io5E.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>The custom log needs to link to the correct path in the VM to retrieve the <strong>"failed_rdp"</strong> logs.</mark> <br/>
<img src="https://i.imgur.com/blT9N8Q.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>The custom log was named the following: <strong>"FAILED_RDP_WITH_GEO"</strong></mark> <br/>
<img src="https://i.imgur.com/4xzGouw.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Custom log proceeding to <strong>"review + create"</strong>.</mark> <br/>
<img src="https://i.imgur.com/0KeKmcr.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<img src="https://i.imgur.com/l0j6zVu.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Moving to Logs within <strong>Log Analytics Workspace > law-honeypot > Logs</strong>.</mark> <br/>
<img src="https://i.imgur.com/AAFlxtR.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Start a 'New Query' and 'Run' the <strong>"FAILED_RDP_WITH_GEO_CL"</strong>. In some circumstances results may not show up immediately, this is because the system needs time to update, which can take up to 20 minutes.</mark> <br/>
<img src="https://i.imgur.com/9Xub4sq.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>While waiting you can 'Run' <strong>"SecurityEvent"</strong> to see the Windows Event Viewer logs.</mark> <br/>
<img src="https://i.imgur.com/kqlq4MN.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>By adding further commands <strong>"where eventID == 4625"</strong> this will only extract failed attempts on logins. <i>EventID 4625 dcouments every failed attempt at logging on to a local computer</i>.</mark> <br/>
<img src="https://i.imgur.com/KYq9Zzb.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>After 20 minutes retry <strong>"FAILED_RDP_WITH_GEO_CL"</strong>. Once it updates the results should show as seen below.</mark> <br/>
<img src="https://i.imgur.com/7VGa3Ln.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>While waiting during that period, the VM was being recongised around the world and started to see some failed RDP login attempts.</mark> <br/>
<img src="https://i.imgur.com/LkvGnfs.png" height="80%" width="80%" alt="SIEM Building Steps"/>
</p>

<h2>Section 10 - Live attacks visualised on a map</h2>
<p align="center">
<br />
<mark>On the same query, I needed the following commands to pull certain extracts from the logs using the following commands as shown.<br/></mark>
<i>Further explaination : "FAILED_RDP_WITH_GEO_CL" is the name of the log table I was querying, <strong>"extend"</strong> creates columns by extracting data from the <strong>'RawData'</strong> field, extracts are made by using a regex (regular expression) pattern which is a sequence of characters that defines a search pattern. Regex are used for tasks such as validating input, seraching for patterns within text, and extracting specific information from text. <strong>"project"</strong> selects the columns to be included in the output. This query is designed to parse specific information from the <strong>'RawData'</strong> field and present it in a structured format as a geographic map. </i> <br/>
<img src="https://i.imgur.com/w622nlB.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Moving to Sentinel, I add a new workbook.</mark> <br/>
<img src="https://i.imgur.com/qhrqc7W.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>I've removed the prefilled graphs and data to start a fresh empty workbook then proceeded to <strong>"add"</strong> a new item to setup the <strong>"map"</strong>. </mark> <br/>
<img src="https://i.imgur.com/SrxvKGo.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<img src="https://i.imgur.com/9h0zPWb.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>I ran the following query as shown in the image below.<br/></mark>
<i>Further explaination : "FAILED_RDP_WITH_GEO_CL" as per the previous commands at the start of Section 10, the following commands are similar except for the additional <strong>"summarize"</strong> which aggregates data by counting occurences <strong>"event_count"</strong> grouped by 'source host', 'latitude', 'longitude', 'country', 'label', and 'destinationhost'. <strong>"where destinationhost != "samplehost"</strong> filters out records that are equal to samplehost. <strong>"where sourcehost != """</strong> filters out records where 'sourcehost' is empty.</i> <br/>
<img src="https://i.imgur.com/wT32HQW.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Set visualisation as <strong>'map'</strong> to display the failed login attempts from around the world.</mark> <br/>
<img src="https://i.imgur.com/Pg3ES7P.png" height="80%" width="80%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>Map settings were adjusted to prefences then applied and saved. The following images shows the current setup for the map.</mark> <br/>
<img src="https://i.imgur.com/2kKlSuB.png" height="40%" width="40%" alt="SIEM Building Steps"/>
<img src="https://i.imgur.com/Kekfhdh.png" height="40%" width="40%" alt="SIEM Building Steps"/>
<img src="https://i.imgur.com/YZd5ZFv.png" height="50%" width="50%" alt="SIEM Building Steps"/>
<br />
 <br />
<mark>The final capture before I closed the Honeypot-vm that was left for approximately 12 hours over night to assess further more attacks as displayed below.</mark> <br/>
<img src="https://i.imgur.com/SwD10HC.png" height="80%" width="80%" alt="SIEM Building Steps"/>

</p>

<h2>Key Takeaways</h2>
The project utilizes Microsoft Azure to build a Security Information and Event Management (SIEM) system to monitor live attacks on a single internet-exposed virtual machine (VM). The aim is to evaluate the likelihood of brute force attacks and highlight the necessity of avoiding default credentials, as well as the importance of removing or changing guest and admin accounts. Once any device, whether a computer or a routable public IP address, is connected to the internet, it becomes a target for attackers. These attacks, often conducted by automated bots, indiscriminately seek to exploit weak authentication regardless of the organization’s size or the value of the data. Over a 12-hour period, the SIEM detected approximately 140 login attempts, underscoring the importance of implementing stronger, more complex passwords and multi-factor authentication to enhance security and prevent unauthorized access.
<br/>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
