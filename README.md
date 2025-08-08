# Task 4 – Setup and Use a Firewall on Windows

## 🎯 Objective
Configure and test basic firewall rules to allow or block traffic.

**Tools Used:** Windows Defender Firewall with Advanced Security  
**Test Case:** Block inbound traffic on Port 23 (Telnet) and verify the block.

---

## Steps Performed

### 1. Open Windows Defender Firewall
- Press `Windows + S`, search for **Windows Defender Firewall with Advanced Security**, and open it.
- This shows existing inbound and outbound rules.

---

### 2. Create a New Rule to Block Port 23 (Telnet)
**GUI Method:**
1. In the **Inbound Rules** section, click **New Rule**.
2. Select **Port** → Click **Next**.
3. Choose **TCP**, enter `23` in **Specific local ports** → Click **Next**.
4. Select **Block the connection** → Click **Next**.
5. Check all profiles (Domain, Private, Public) → Click **Next**.
6. Name the rule: `Block Telnet Port 23` → Click **Finish**.

---

### 3. Install Telnet Client
Since Telnet is disabled by default:
1. Open **Command Prompt as Administrator**.
2. Run:
   ```cmd
   dism /online /Enable-Feature /FeatureName:TelnetClient
---
Wait until the installation finishes.
---
### 4. Test the Firewall Rule
Open Command Prompt.

Run:
```cmd
telnet localhost 23
```
---
## Expected result:
<i>Connecting to localhost...Could not open connection to the host, on port 23: Connect failed
This confirms the firewall blocked the port.</i>
---
### 5. Remove the Rule
Go back to Inbound Rules.<br>
Right-click Block Telnet Port 23 → Delete.

---

##  📷 Screenshots
Before rule creation: Existing firewall rules.<br>
After rule creation: Block Telnet Port 23 visible in Inbound Rules.<br>
Testing: Telnet connection failed message.<br>
After removal: Rule deleted and firewall restored to original state.

---

## How a Firewall Filters Traffic
A firewall examines network traffic and applies rules to allow or block packets.<br>
Rules can be based on:<br>
Port number<br>
Protocol (TCP/UDP)<br>
IP address<br>
Direction (Inbound/Outbound)<br>
Allow rules let matching packets pass through.<br>
Block/Deny rules drop or reject packets.<br>
Windows Defender Firewall is stateful, meaning it tracks active connections and allows response traffic automatically.<br>

---

## Conclusion
The firewall successfully blocked inbound Telnet traffic on port 23. This demonstrated how to:<br>
Create a new inbound rule<br>
Test the block using Telnet<br>
Remove the rule to restore the firewall<br>

---

##  Author: Mumuksha Kashyap<br>
Date: 8/8/2025
