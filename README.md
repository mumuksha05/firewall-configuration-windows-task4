# Task 4 – Setup and Use a Firewall on Windows

## 🎯 Objective
Configure and test basic firewall rules to allow or block traffic.

**Tools Used:** Windows Defender Firewall with Advanced Security  
**Test Case:** Block inbound traffic on Port 23 (Telnet) and verify the block.

---

## 📌 Steps Performed

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
4. Test the Firewall Rule
Open Command Prompt.

Run:
```cmd
telnet localhost 23
```
---
### Expected result:
<i>Connecting to localhost...Could not open connection to the host, on port 23: Connect failed
This confirms the firewall blocked the port.</i>
---
5. Remove the Rule
Go back to Inbound Rules.

Right-click Block Telnet Port 23 → Delete.
---
##📷 Screenshots
Before rule creation: Existing firewall rules.

After rule creation: Block Telnet Port 23 visible in Inbound Rules.

Testing: Telnet connection failed message.

After removal: Rule deleted and firewall restored to original state.
---
## How a Firewall Filters Traffic
A firewall examines network traffic and applies rules to allow or block packets.

Rules can be based on:

Port number
Protocol (TCP/UDP)
IP address
Direction (Inbound/Outbound)
Allow rules let matching packets pass through.
Block/Deny rules drop or reject packets.
Windows Defender Firewall is stateful, meaning it tracks active connections and allows response traffic automatically.
---
## Conclusion
The firewall successfully blocked inbound Telnet traffic on port 23. This demonstrated how to:

Create a new inbound rule
Test the block using Telnet
Remove the rule to restore the firewall
---
Author: Mumuksha Kashyap
Date: 8/8/2025
