# Cisco Switch CLI Cheat Sheet (Shorthand Focus) 🚀

---

## Basic Navigation & Show Commands 💻

* **Enter Privileged EXEC Mode:** ( Some admin accounts already do this automatically )
    ```
    enable
    ```
    (or `en`)
* **Enter Global Configuration Mode:**
    ```
    conf t
    ```
* **Exit Current Mode:**
    ```
    exit
    ```
* **Return to Privileged EXEC Mode:**
    ```
    end
    ```
    (or `Ctrl+Z`)
* **Show Running Configuration:**
    ```
    sh run
    ```
* **Show Startup Configuration:**
    ```
    sh start
    ```
* **Show IP Interface Brief:**
    ```
    sh ip int br
    ```
* **Show Interfaces Status:**
    ```
    sh int status
    ```
* **Show Specific Interface Status:**
    ```
    sh int <interface_type><interface_number> status
    ```
    (e.g., `sh int g0/1 status`)
* **Show VLANs:**
    ```
    sh vlan br
    ```
* **Show MAC Address Table (All):**
    ```
    sh mac add
    ```
    (or `sh mac-address-table`)
* **Show MAC Address Table for a Specific Interface:**
    ```
    sh mac add int <interface_type><interface_number>
    ```
    (e.g., `sh mac add int g0/1`)
* **Show MAC Address Table for a Specific VLAN:**
    ```
    sh mac add vlan <vlan_id>
    ```
    (e.g., `sh mac add vlan 10`)
* **Show CDP Neighbors (to see connected Cisco devices):**
    ```
    sh cdp nei
    ```
* **Show CDP Neighbors Detail:**
    ```
    sh cdp nei det
    ```
* **Show Interface Description:**
    ```
    sh int desc
    ```

---

## Interface Configuration ⚙️

* **Enter Interface Configuration Mode:**
    ```
    int <interface_type><interface_number>
    ```
    (e.g., `int g0/1` or `int fa0/1` for FastEthernet)
    (Can also use ranges: `int range g0/1-4`)
* **Shutdown Port:**
    ```
    shut
    ```
* **Enable Port (No Shutdown):**
    ```
    no shut
    ```
* **Add Port Description:**
    ```
    desc <your_description_here>
    ```
    (e.g., `desc User_PC_Port`)
* **Remove Port Description:**
    ```
    no desc
    ```
* **Set Port to Access Mode:**
    ```
    sw mo acc
    ```
    (short for `switchport mode access`)
* **Assign VLAN to Access Port:**
    ```
    sw acc vlan <vlan_id>
    ```
    (short for `switchport access vlan <vlan_id>`; e.g., `sw acc vlan 10`)
* **Set Port to Trunk Mode:**
    ```
    sw mo tr
    ```
    (short for `switchport mode trunk`)
* **Specify Allowed VLANs on Trunk (if not all):**
    ```
    sw tr allowed vlan <vlan_list>
    ```
    (e.g., `sw tr allowed vlan 10,20,30`)
    * **Add VLAN to trunk:** `sw tr allowed vlan add <vlan_id>`
    * **Remove VLAN from trunk:** `sw tr allowed vlan remove <vlan_id>`
* **Set Native VLAN for Trunk Port:**
    ```
    sw tr native vlan <vlan_id>
    ```

---

## VLAN Management 🌐

* **Create VLAN (from Global Configuration Mode):**
    ```
    vlan <vlan_id>
    ```
    (e.g., `vlan 10`)
    * **Then optionally add a name (within VLAN configuration sub-mode):**
        ```
        name <VLAN_Name>
        ```
        (e.g., `name Sales_VLAN`)
* **Remove VLAN (from Global Configuration Mode):**
    ```
    no vlan <vlan_id>
    ```
    (e.g., `no vlan 10`)

---

## Troubleshooting & Diagnostics 🛠️

* **Check Cable Integrity (Time Domain Reflectometer - TDR):**
    ```
    test cable-diagnostics tdr int <interface_type><interface_number>
    ```
    (e.g., `test cab tdr int g0/1`)
* **Show Cable Diagnostics Results:**
    ```
    sh cable-diagnostics tdr int <interface_type><interface_number>
    ```
    (e.g., `sh cab tdr int g0/1`)
    *(Note: The port usually needs to be `shut` down first for TDR test, then `no shut`. Some platforms might support it on live links with limitations.)*
* **Ping:**
    ```
    ping <ip_address_or_hostname>
    ```
* **Traceroute:**
    ```
    traceroute <ip_address_or_hostname>
    ```
* **Show Logs:**
    ```
    sh log
    ```

---

## Saving Configuration 💾

* **Copy Running Configuration to Startup Configuration:**
    ```
    wr mem
    ```
    (or `copy run start`)

---

**Remember to exit configuration modes properly (`exit`, `end`, or `Ctrl+Z`).**
Use `?` for command help (e.g., `sh ?` or `int g0/1 ?`).
Use `Tab` for command completion.
Interface names: `g` = GigabitEthernet, `fa` = FastEthernet, `te` = TenGigabitEthernet.
