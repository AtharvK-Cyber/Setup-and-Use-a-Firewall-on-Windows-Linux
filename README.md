# Task 4: Setup and Use a Firewall on Windows & Linux

## 📌 Objective
To configure and test basic firewall rules to allow or block network traffic, demonstrating an understanding of network security principles using Windows Firewall and UFW (Uncomplicated Firewall) on Parrot OS.

## 🛠️ Tools & Environment
* **Windows:** Windows 10 (Windows Defender Firewall with Advanced Security)
* **Linux:** Parrot OS (Using GUFW - Graphical Uncomplicated Firewall)
* **Target Ports:** Port 23 (Telnet - Block), Port 22 (SSH - Allow)

---

## 1. Windows Firewall Configuration (Windows 10)

### Steps Taken:
1. **Open Configuration Tool:**
   - Pressed `Win + R`, typed `wf.msc`, and pressed Enter to open **Windows Defender Firewall with Advanced Security**.
2. **Review Current Rules:**
   - Navigated to **Inbound Rules** to view the existing traffic policies.
3. **Create Block Rule (Port 23):**
   - Selected **New Rule** in the right-hand pane.
   - **Rule Type:** Selected "Port".
   - **Protocol/Ports:** Selected "TCP" and specified "Specific local ports: 23".
   - **Action:** Selected "Block the connection".
   - **Profile:** Applied to Domain, Private, and Public profiles.
   - **Name:** Named the rule "Block Telnet (Port 23)".
4. **Verification:**
   - Verified the rule appeared at the top of the Inbound Rules list with a "Block" icon.

### 📸 Evidence
*Below is the screenshot showing the newly created Inbound Rule blocking Port 23 on Windows.*
<img width="1561" height="690" alt="8" src="https://github.com/user-attachments/assets/a40ba0d0-d9de-4f5d-9c9b-e66442041359" />
<img width="1559" height="709" alt="9" src="https://github.com/user-attachments/assets/798a7604-d8ee-4224-9166-a437c4e496c1" />
<img width="1563" height="708" alt="10" src="https://github.com/user-attachments/assets/1a147e0f-4b43-40ac-973a-06330511b74e" />
<img width="1563" height="709" alt="11" src="https://github.com/user-attachments/assets/25e9e213-fd76-4c83-a030-c70ecf2e91d7" />
<img width="1563" height="708" alt="12" src="https://github.com/user-attachments/assets/df7f3c40-fd5a-4d23-a49b-caa7f7f955e1" />
<img width="1560" height="710" alt="13" src="https://github.com/user-attachments/assets/6391cb50-a636-4ad9-b991-2dc14ea4b547" />
<img width="1561" height="710" alt="14" src="https://github.com/user-attachments/assets/e4c400f4-3c0a-4e3d-b056-33f5308b1e3f" />
<img width="1560" height="711" alt="15" src="https://github.com/user-attachments/assets/a721c716-8f7e-4580-8215-30130902faef" />
<img width="1104" height="642" alt="16" src="https://github.com/user-attachments/assets/2340ee61-d0e6-46ca-8d4f-452938051e55" />
<img width="1561" height="708" alt="17" src="https://github.com/user-attachments/assets/29791f6f-9667-4333-ad66-bf0be955bff5" />
<img width="1563" height="709" alt="18" src="https://github.com/user-attachments/assets/c3611809-9746-4127-9d95-872ed62b3413" />
<img width="1561" height="711" alt="19" src="https://github.com/user-attachments/assets/ce2562de-2947-4aed-95a4-1c72d355c829" />



---

## 2. Linux Firewall Configuration (Parrot OS)

### Steps Taken:
1. **Open Firewall GUI:**
   - Opened the application menu and launched **Firewall Configuration** (GUFW).
   - Unlocked the settings using the root/sudo password.
2. **Enable Firewall:**
   - Switched the Status toggle to **ON** to enable UFW.
3. **Add SSH Rule (Allow):**
   - Clicked the "+" (Add) button.
   - Configured the rule to **Allow** traffic on **Port 22 (SSH)** to ensure remote access capabilities.
4. **Add Telnet Rule (Block):**
   - Clicked the "+" (Add) button.
   - Configured the rule to **Deny** (Block) Inbound traffic on **Port 23 (Telnet)**.
5. **Verification:**
   - Reviewed the rules list in the main GUFW window to confirm both rules were active and correctly configured.

### 📸 Evidence
*Below is the screenshot from Parrot OS (GUFW) showing the status enabled and the rules for SSH and Telnet.*

<img width="377" height="566" alt="1" src="https://github.com/user-attachments/assets/e4ebf771-ff06-48c6-8533-272f23eab04c" />
<img width="373" height="564" alt="2" src="https://github.com/user-attachments/assets/90b996b1-f0c6-44f0-80ce-c7796e08a2fc" />
<img width="655" height="667" alt="3" src="https://github.com/user-attachments/assets/7345f44c-8bb8-43bf-a3b6-6ca0094c6fa2" />
<img width="646" height="663" alt="4" src="https://github.com/user-attachments/assets/f9a5d29e-9523-4c80-9bd5-0a83a361d93e" />
<img width="647" height="666" alt="5" src="https://github.com/user-attachments/assets/54c8295c-f9c5-4e30-afc7-f7b1ffd9d09e" />
<img width="1105" height="639" alt="6" src="https://github.com/user-attachments/assets/664d7dac-4b72-4d53-bfb5-8c1730278a34" />
<img width="647" height="668" alt="7" src="https://github.com/user-attachments/assets/ce931644-4cab-41e1-9177-20e14b50beba" />


### Method B: Using Terminal (CLI)
*Alternatively, the following commands were used to configure the firewall via the terminal:*

1.  **Check UFW Status:**
    ```bash
    sudo ufw status
    ```
2.  **Allow SSH (Port 22):**
    ```bash
    sudo ufw allow 22/tcp
    ```
3.  **Block Telnet (Port 23):**
    ```bash
    sudo ufw deny 23/tcp
    ```
4.  **Enable Firewall:**
    ```bash
    sudo ufw enable
    ```
5.  **Verify Rules:**
    ```bash
    sudo ufw status verbose
    ```

---

## 🧠 Theory: How Firewalls Filter Traffic

**Summary:**
A firewall acts as a security barrier between a device and the network. It filters traffic based on a defined set of rules (Access Control Lists).

* **Packet Inspection:** The firewall examines the header of every data packet entering (inbound) or leaving (outbound) the system.
* **Filtering Criteria:** It makes decisions to **Allow** or **Deny** the packet based on:
  - **Source/Destination IP:** Who is sending the data and where is it going?
  - **Port Number:** What service is being requested? (e.g., Port 80 for Web, Port 23 for Telnet).
  - **Protocol:** Is it TCP, UDP, or ICMP?
* **Default Policy:** Most firewalls are set to "Deny All" inbound traffic by default, meaning everything is blocked unless specifically allowed.

## ✅ Outcome
Successfully demonstrated the ability to manage network traffic by creating custom rules to allow essential services (SSH) and block insecure services (Telnet) across both Windows and Linux environments.
