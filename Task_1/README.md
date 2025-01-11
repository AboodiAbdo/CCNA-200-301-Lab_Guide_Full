# Network Task Documentation

## Task Overview
This project involves the configuration and setup of a network using Cisco Packet Tracer. The task demonstrates the design and implementation of routing between two networks to enable seamless communication. This document provides a detailed explanation of the setup, configurations, and verification steps, ensuring a comprehensive understanding of the network implementation process.

### Objectives:
1. Design a network topology with two subnetworks.
2. Configure IP addressing for all devices in the topology.
3. Set up static routing on the router to enable inter-network communication.
4. Perform testing to verify connectivity.
5. Document the process with screenshots, configuration commands, and a video walkthrough.

---

## Network Topology

The topology consists of:

1. **Network A (Green Zone):**
   - Subnet: 192.168.1.0/24
   - Gateway: 192.168.1.1 (Router Interface Fa0/0)
   - Devices: PC4, PC5, PC6, PC7, and SV1

2. **Router (Cisco 2811):**
   - Interfaces:
     - Fa0/0: 192.168.1.1 (Connected to Network A)
     - Fa0/1: 172.16.5.1 (Connected to Network B)

3. **Network B (Blue Zone):**
   - Subnet: 172.16.5.0/24
   - Gateway: 172.16.5.1 (Router Interface Fa0/1)
   - Devices: PC9, PC10, PC11, and SV1

---

## Configuration Details

### 1. **IP Addressing**

#### Network A Devices:
| Device  | Interface | IP Address    | Subnet Mask   | Gateway       |
|---------|-----------|---------------|---------------|---------------|
| PC4     | Fa0       | 192.168.1.2   | 255.255.255.0 | 192.168.1.1   |
| PC5     | Fa0       | 192.168.1.3   | 255.255.255.0 | 192.168.1.1   |
| PC6     | Fa0       | 192.168.1.4   | 255.255.255.0 | 192.168.1.1   |
| PC7     | Fa0       | 192.168.1.5   | 255.255.255.0 | 192.168.1.1   |
| SV1     | Fa0       | 192.168.1.10  | 255.255.255.0 | 192.168.1.1   |

#### Network B Devices:
| Device  | Interface | IP Address    | Subnet Mask   | Gateway       |
|---------|-----------|---------------|---------------|---------------|
| PC9     | Fa0       | 172.16.5.5    | 255.255.255.0 | 172.16.5.1    |
| PC10    | Fa0       | 172.16.5.6    | 255.255.255.0 | 172.16.5.1    |
| PC11    | Fa0       | 172.16.5.7    | 255.255.255.0 | 172.16.5.1    |
| SV1     | Fa0       | 172.16.5.10   | 255.255.255.0 | 172.16.5.1    |

---

### 2. **Switch Configuration**

#### Step-by-Step Commands for Switch (Green Zone):
1. **Enter privileged mode:**
   ```bash
   enable
   ```
2. **Enter configuration mode:**
   ```bash
   configure terminal
   ```
3. **Configure VLAN 1 IP address:**
   ```bash
   interface vlan 1
   ip address 192.168.1.10 255.255.255.0
   no shutdown
   exit
   ```
4. **Set default gateway:**
   ```bash
   ip default-gateway 192.168.1.1
   exit
   ```
5. **Save configuration:**
   ```bash
   write memory
   ```

#### Step-by-Step Commands for Switch (Blue Zone):
1. **Enter privileged mode:**
   ```bash
   enable
   ```
2. **Enter configuration mode:**
   ```bash
   configure terminal
   ```
3. **Configure VLAN 1 IP address:**
   ```bash
   interface vlan 1
   ip address 172.16.5.10 255.255.255.0
   no shutdown
   exit
   ```
4. **Set default gateway:**
   ```bash
   ip default-gateway 172.16.5.1
   exit
   ```
5. **Save configuration:**
   ```bash
   write memory
   ```

---

### 3. **Router Configuration**

The following commands were used to configure the router:

#### Step-by-Step Commands:

1. **Enter privileged mode:**
   ```bash
   enable
   ```

2. **Enter configuration mode:**
   ```bash
   configure terminal
   ```

3. **Configure interface Fa0/0 (connected to Network A):**
   ```bash
   interface fa0/0
   ip address 192.168.1.1 255.255.255.0
   no shutdown
   exit
   ```

4. **Configure interface Fa0/1 (connected to Network B):**
   ```bash
   interface fa0/1
   ip address 172.16.5.1 255.255.255.0
   no shutdown
   exit
   ```

5. **Set up static routes:**
   ```bash
   ip route 192.168.1.0 255.255.255.0 fa0/0
   ip route 172.16.5.0 255.255.255.0 fa0/1
   exit
   ```

6. **Save the configuration:**
   ```bash
   write memory
   ```

7. **Verify the configuration:**
   ```bash
   show running-config
   show ip route
   ```

---

## Testing and Verification

### 1. **Ping Test:**
   - Test connectivity between devices in different networks.
   - Example command from PC4:
     ```bash
     ping 172.16.5.5
     ```
   - Expected result: Successful response.

### 2. **Traceroute:**
   - Verify the routing path.
   - Example command:
     ```bash
     tracert 172.16.5.5
     ```

### 3. **Display Routing Table:**
   - Check the router's routing table:
     ```bash
     show ip route
     ```
   - Verify the presence of static routes for both subnets.

### 4. **Connectivity Test Summary:**
   Include results for all ping tests and traceroutes. For example:
   - PC4 to PC9: Successful.
   - PC5 to PC10: Successful.
   - PC6 to PC11: Successful.

---

## Media

### Screenshots
Include the following screenshots:
1. Network topology.
2. Router configurations (detailed step-by-step commands).
3. Switch configurations (step-by-step commands).
4. Ping and traceroute results.
5. Routing table display.

### Video Walkthrough
Create and include a video demonstrating:
1. The configuration steps on Packet Tracer.
2. The verification process, including ping tests and routing table checks.

---

## Repository Structure

```
Project-Name/
|
|-- Screenshots/
|   |-- topology.png
|   |-- router_config.png
|   |-- switch_config.png
|   |-- ping_test.png
|   |-- routing_table.png
|
|-- Videos/
|   |-- walkthrough.mp4
|
|-- README.md
|-- PacketTracer_Files/
    |-- project_file.pkt
```

---

## Contributing
Contributions are welcome! Fork the repository and submit a pull request for improvements or additional features.

---

## Author
**AbdulRhman AbdulGhaffar**  
*IT Technical Support and Network Engineer*

---

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.
