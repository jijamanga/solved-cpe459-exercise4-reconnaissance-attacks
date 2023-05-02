Download Link: https://assignmentchef.com/product/solved-cpe459-exercise4-reconnaissance-attacks
<br>
A reconnaissance attack is when an attacker targets a victim’s system to gather information about its vulnerabilities. In this assignment, you will use three tools to perform tasks: NMAP, SHODAN and S-MOD. This exercise has three parts to design and implement a Reconnaissance attack on a SCADA system.

<ol>

 <li>Perform a network scan (IP address &amp; MAC) to find all the IP addresses and MAC addresses of your Virtual Network. Use NMAP to also find open ports in your virtual network.</li>

 <li>Use S-MOD to identify registers, coils, and function codes available in a system.</li>

 <li>Discover information about devices connected to the internet using SHODAN.</li>

</ol>

<h1>2         Before Starting</h1>

<h2>2.1        Install a Kali Linux VM</h2>

<ol>

 <li>Make sure you have Kali Linux installed on a VM. If you don’t have it, please click on the below and go to part 5:  <a href="https://sites.google.com/uah.edu/openplctipsandtricks/initial-vm-setup">https://sites.google.com/uah.edu/openplctipsandtricks/initial-vm-setup</a></li>

</ol>

An attacker gathers information about a system by observing system operations and listening in on the network communication. Therefore, the network architecture of this assignment is as follows:

<h1>3         Network Scan with NMAP</h1>

<h2>3.1        Find all IP addresses and MAC addresses on your Virtual Network</h2>

<ol>

 <li>Kali Linux comes with some pre-installed tools such as NMAP. So, you <strong>do not</strong> need to install it.</li>

 <li>Open the terminal and type the command: “<strong>sudo</strong> <strong>nmap –sn [subnet/CIDR]</strong>”.</li>

 <li><em>Using the information that you have found, answer the post-exercise questions.</em></li>

</ol>

<h2>3.2        Use NMAP to find open ports in your virtual network.</h2>

<ol>

 <li>Open the terminal and type: <strong>“sudo nmap -sT -p [range of ports] [subnet/CIDR]”.</strong></li>

 <li>Close any other port that is does not use Modbus, ScadaBR and OpenPLC services. Type this command for each port you want to close:</li>

</ol>

“<strong><em>sudo iptables -A INPUT -p tcp –destination-port [port number] -j REJECT”</em></strong>

<ol>

 <li>Type again the command <strong>“sudo nmap -sT -p [range of ports] [subnet/CIDR]”</strong> to verify if all the ports are closed except the ones cited above.</li>

 <li><em>Using the information that you have found, answer the post-exercise questions.</em></li>

</ol>

<h1>4         Using S-MOD to identify registers, coils, and function codes</h1>

<h2>4.1        Initial Setup</h2>

<ol>

 <li>Open Kali terminal and install S-MOD, type: <strong>“sudo git clone https://github.com/theralfbrown/smod-1”</strong></li>

 <li>Next, type: “<strong>cd smod-1</strong>”</li>

 <li>Run smod-1: “<strong>python smod-1</strong>”</li>

 <li>After you run, type <strong>“show modules”</strong> to get the list containing all the functions available using this tool.</li>

</ol>

<h2>4.2        Use S-MOD to find the function codes</h2>

<ol>

 <li>Type: “<strong>use modbus/scanner/getfunc</strong>” and configure the module if it needs some additional settings before running (Check Reconnaissance slide deck for instructions).</li>

 <li><em>You will need this task completed in order to answer the post-exercise questions.</em></li>

</ol>

<h2>4.3        Use S-MOD to read coils and register values</h2>

<ol>

 <li>To read register values, use the steps from 5.2 except you type:<strong>use modbus/function/readHoldingRegister</strong></li>

 <li>After you run, you need to know if the values you obtained are correct or not – register values should be in front of the registerVal list. To find out that<strong>:</strong>

  <ol>

   <li>Go to your <em>HMI</em> and open <em>SCADABR</em>.</li>

   <li>Click on Data Sources.</li>

   <li>Click on the Edit icon for the Traffic Light.</li>

   <li>Under <em>Modbus read data,</em> choose <em>Holding Register</em> for Register range, change the number of registers to 8 and click on <em>Read data</em>.</li>

   <li>Note what you see and answer the post-exercise questions.</li>

  </ol></li>

 <li>To read coil values, use the steps from 4.2 except you type:<strong>use modbus/function/readCoils</strong></li>

 <li>After you run, you need to know if the values you obtained are correct or not – coil values should be in front of coilStatus list. To do this,

  <ol>

   <li>Go to your <em>HMI</em> and open <em>SCADABR</em>.</li>

   <li>Click on Data Sources.</li>

   <li>Under <em>Modbus read data,</em> choose <em>Coil Status</em> for Register range, change the number of registers to 8 and click on <em>Read data</em>.</li>

   <li><em>Note what you see and answer the post-exercise questions.</em></li>

  </ol></li>

</ol>

<h1>5         SHODAN</h1>

SHODAN is a search engine that lets users find certain types of computers connected to the Internet. Use SHODAN to answer the post-exercise questions.

<h1>6         Post Exercise Report</h1>

Submit your answers to the following questions.

<h2>6.1        Using what you found in section 3.1, please fill out the table below:</h2>

<table width="405">

 <tbody>

  <tr>

   <td width="65">Node</td>

   <td width="170">IP ADDRESS</td>

   <td width="170">MAC ADDRESS</td>

  </tr>

  <tr>

   <td width="65"> </td>

   <td width="170"> </td>

   <td width="170"> </td>

  </tr>

  <tr>

   <td width="65"> </td>

   <td width="170"> </td>

   <td width="170"> </td>

  </tr>

  <tr>

   <td width="65"> </td>

   <td width="170"> </td>

   <td width="170"> </td>

  </tr>

  <tr>

   <td width="65"> </td>

   <td width="170"> </td>

   <td width="170"> </td>

  </tr>

 </tbody>

</table>




<h2>6.2        Using what you found in section 3.2, please fill out the table below:</h2>

<table width="518">

 <tbody>

  <tr>

   <td width="114">Node</td>

   <td width="102">IP</td>

   <td width="104">MAC</td>

   <td width="104">Port</td>

   <td width="95">Service</td>

  </tr>

  <tr>

   <td width="114"> </td>

   <td width="102"> </td>

   <td width="104"> </td>

   <td width="104"> </td>

   <td width="95"> </td>

  </tr>

  <tr>

   <td width="114"> </td>

   <td width="102"> </td>

   <td width="104"> </td>

   <td width="104"> </td>

   <td width="95"> </td>

  </tr>

  <tr>

   <td width="114"> </td>

   <td width="102"> </td>

   <td width="104"> </td>

   <td width="104"> </td>

   <td width="95"> </td>

  </tr>

  <tr>

   <td width="114"> </td>

   <td width="102"> </td>

   <td width="104"> </td>

   <td width="104"> </td>

   <td width="95"> </td>

  </tr>

 </tbody>

</table>

<h2>1.</h2>

<h2>6.3        What are the function codes used in your system?</h2>

<h2>6.4        Is it possible to create a reconnaissance attack and change the values of registers or coils using function codes 5 through 16? Why or why not? Explain.<u>HINT</u>: Remember that the values are in decimal, but they are stored in binary/hexadecimal.</h2>

<h2>6.5        For Section 4.3, you read the registers and coils. For each of them, compare what you see on the HMI with what you see using S-Mod. Are they the same? Why or why not? Explain.<u>Hint</u>: Consider how coils are read either in Little Endian or Big Endian.</h2>

<h2>6.6        How many Modbus ports are found in the world?</h2>

<h2>6.7        How many DNP3 ports can you find using SHODAN? Are they all real DNP3 ports? Justify your answer.</h2>




<h1>2.</h1>

<h1>7         Exercise Rubric</h1>




<table width="582">

 <tbody>

  <tr>

   <td width="123">Questions + Criteria</td>

   <td width="56">Full marks</td>

   <td width="108">Mostly correct, missing one or two considerations</td>

   <td width="102">Partially correct, missing many considerations</td>

   <td width="96">Partially correct, explanation is lacking details</td>

   <td width="96">Missing or does not explain answers</td>

  </tr>

  <tr>

   <td width="123">1.    NMAP IP address table</td>

   <td width="56">10</td>

   <td width="108">8</td>

   <td width="102">5</td>

   <td width="96">1</td>

   <td width="96">0</td>

  </tr>

  <tr>

   <td width="123">2.    NMAP open ports table</td>

   <td width="56">10</td>

   <td width="108">8</td>

   <td width="102">5</td>

   <td width="96">1</td>

   <td width="96">0</td>

  </tr>

  <tr>

   <td width="123">3.    List of S-MOD function codes</td>

   <td width="56">10</td>

   <td width="108">8</td>

   <td width="102">5</td>

   <td width="96">1</td>

   <td width="96">0</td>

  </tr>

  <tr>

   <td width="123">4.    S-MOD read coils + recon attack question</td>

   <td width="56">25</td>

   <td width="108">22.5</td>

   <td width="102">17.5</td>

   <td width="96">5</td>

   <td width="96">0</td>

  </tr>

  <tr>

   <td width="123">5.    Comparing reading registers and coils</td>

   <td width="56">25</td>

   <td width="108">22.5</td>

   <td width="102">17.5</td>

   <td width="96">5</td>

   <td width="96">0</td>

  </tr>

  <tr>

   <td width="123">6.    Number of Modbus ports</td>

   <td width="56">5</td>

   <td width="108">4</td>

   <td width="102">2.5</td>

   <td width="96">1</td>

   <td width="96">0</td>

  </tr>

  <tr>

   <td width="123">7.    DNP3 ports using SHODAN</td>

   <td width="56">10</td>

   <td width="108">8</td>

   <td width="102">5</td>

   <td width="96">1</td>

   <td width="96">0</td>

  </tr>

 </tbody>

</table>





