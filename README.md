<h2 dir="rtl" align="center">
بسم الله الرحمن الرحيم
</h2>

# Essential Server Commands

This is a list of **Essential Server Commands** for a Backend developer to troubleshoot, debug, and interact with servers effectively. These commands are commonly used in **Windows environments**, though some are universal across operating systems.

**Content**
- [1. `whoami`](#1-whoami)  
- [2. `ipconfig`](#2-ipconfig)  
- [3. `ping`](#3-ping)  
- [4. `telnet`](#4-telnet)  
- [5. `tracert`](#5-tracert)  
- [6. `nslookup`](#6-nslookup)  
- [7. `curl`](#7-curl)  
- [8. `iisreset`](#8-iisreset)  
- [9. `netstat`](#9-netstat)  
- [10. `tasklist` and `taskkill`](#10-tasklist-and-taskkill)  
- [11. `sc`](#11-sc)  
- [12. `net share` and `net use`](#12-net-share-and-net-use)  


## **1. `whoami`**
- **Purpose:** Displays the current logged-in user and domain.
- **Usage:**
  ```bash
  whoami
  ```
  - **Result:** Verifies which user account is executing the commands, especially useful for permission issues.


## **2. `ipconfig`**
- **Purpose:** Displays network configuration details of your system.
- **Usage:**
  ```bash
  ipconfig
  ```
  - Use `ipconfig /all` for more detailed information.
  - **Result:** Shows IP address, default gateway, subnet mask, and DNS servers of your system.

## **3. `ping`**
- **Purpose:** Tests network connectivity to a server or domain.
- **Usage:**
  ```bash
  ping <hostname or IP>
  ```
  - Example: `ping google.com` or `ping 192.168.1.1`
  - **Result:** Checks if a server is reachable and measures the time it takes for packets to travel to the server and back.
  


## **4. `telnet`**
- **Purpose:** Tests connectivity to a specific port on a remote server.
- **Usage:**
  ```bash
  telnet <hostname or IP> <port>
  ```
  - Example: `telnet 192.168.1.1 80`
  - **Result:** Helps verify if a service is running and accessible on a specific port. Useful for troubleshooting web servers or APIs.


## **5. `tracert`**
- **Purpose:** Traces the path packets take to reach a server.
- **Usage:**
  ```bash
  tracert <hostname or IP>
  ```
  - Example: `tracert google.com`
  - **Result:** Lists all routers (hops) that data passes through to reach the destination. Useful for diagnosing slow connections or network issues.


## **6. `nslookup`**
- **Purpose:** Queries DNS servers for domain information.
- **Usage:**
  ```bash
  nslookup <domain>
  ```
  - Example: `nslookup google.com`
  - **Result:** Returns the IP address of a domain and the DNS server resolving the query.

## **7. `curl`**
- **Purpose:** Sends HTTP requests to APIs or servers to test endpoints.
- **Usage:**
  ```bash
  curl -X GET <URL>
  ```
  - Example: `curl -X GET https://api.example.com`
  - **Result:** Verifies that API endpoints are responding correctly.
  
## **8. `iisreset`**
- **Purpose:** Restarts IIS (Internet Information Services).
- **Usage:**
  ```bash
  iisreset
  ```
  - **Result:** Restarts IIS to resolve issues with web apps deployed on the server.

## **9. `netstat`**
- **Purpose:** Displays active network connections and open ports.
- **Usage:**
  ```bash
  netstat -an
  ```
  - Use `netstat -b` to see the associated application names.
  - **Result:** Identifies which ports are open and which services are running. Helps detect issues with APIs or listening ports.


## **10. `tasklist` and `taskkill`**
- **Purpose:** 
  - `tasklist`: Lists all running processes.
  - `taskkill`: Stops a specific process.
- **Usage:**
  ```bash
  tasklist
  taskkill /PID <process ID> /F
  ```
  - Example: `taskkill /PID 1234 /F`
  - **Result:** Useful for stopping problematic processes or freeing resources on the server.


## **11. `sc`**  
- **Purpose:** Service Control (SC) is a command-line tool for managing Windows services.  
- **Usage:**  
  ```bash  
  sc <command> <service_name>  
  ```  
  - **Commands:**  

    - `sc query state= all`: List all services (Ensure there's a space after state= (this is required for the command to work)).  
    - `sc query state= running`: Filter running services only. 
    - `sc query state= inactive`: Filter stopped services only.   
    - `query <service_name>`: Displays the status of a service.  
    - `start <service_name>`: Starts a service.  
    - `stop <service_name>`: Stops a service.  
    - `stop <service_name>`: Stops a service.  

  - **Example:**  
    ```bash  
    sc query wuauserv  
    ```  

## **12. `net share` and  `net use`**

### **`net share`**

- **Purpose:** Shares a folder or checks shared resources on a system.  
- **Usage:**  
  ```bash  
  net share <sharename>=<folderpath>  
  ```  
  - **Example:** `net share MyShare=C:\SharedFolder`  
  - **Result:** Shares the specified folder with the given share name.  

- **Check Existing Shares:**  
  ```bash  
  net share  
  ```  
  - **Result:** Lists all shared resources on the system.  

- **Delete a Share:**  
  ```bash  
  net share <sharename> /delete  
  ```  
  - **Example:** `net share MyShare /delete`  
  - **Result:** Removes the specified share.  
  
---

### **`net use`**
- **Purpose:** Maps a network drive or checks shared folder connectivity.
- **Usage:**
  ```bash
  net use <drive letter>: \\<server>\<shared folder>
  ```
  - Example: `net use Z: \\192.168.1.1\share`
  - **Result:** Maps a shared folder to a drive letter on your system.

### **Key Differences**

| Feature               | `net share`                       | `net use`                       |
|-----------------------|------------------------------------|----------------------------------|
| **Purpose**           | To share a folder on the network. | To access a shared folder on the network. |
| **Role**              | You are the host (sharing the resource). | You are the client (accessing the resource). |
| **Effect**            | Creates a shared folder for others to access. | Maps a shared folder to your local computer. |
---
