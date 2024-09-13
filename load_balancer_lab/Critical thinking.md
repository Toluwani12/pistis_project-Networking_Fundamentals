# CRITICAL THINKING: Subnetting Plan for Growing Organization

**1. Identify Subnet Requirements:**


| Departments | Finance,  Human Resources, Sales  , Marketing, IT  | 
| :---:   | :---: | 
| Future Growth | Plan for at least 50% growth in each department over the next five years   | 
|Network Topology| Centralized data center for servers|

Each department has its own floor in the office building.

**Answer:**


### **1. Identify Subnet Requirements**

#### **Departments and Current Devices**:
- **Finance**: 50 hosts
- **Human Resources**: 30 hosts
- **Sales**: 70 hosts
- **Marketing**: 40 hosts
- **IT**: 100 hosts
- **Operations**: 80 hosts

#### **Future Growth (50% Increase in Hosts)**:
To account for future growth, we will ensure that subnets are large enough to accommodate a 50% increase in the number of hosts for each department.

| Department          | Current Hosts | Future Growth (50%) | Future Hosts |
|---------------------|---------------|---------------------|--------------|
| Finance             | 50            | +50%                | 75           |
| Human Resources     | 30            | +50%                | 45           |
| Sales               | 70            | +50%                | 105          |
| Marketing           | 40            | +50%                | 60           |
| IT                  | 100           | +50%                | 150          |
| Operations          | 80            | +50%                | 120          |

### **2. Allocate IP Addresses**

We will allocate the subnets based on the number of hosts required and the appropriate subnet size:

| Department          | Hosts Required | Subnet Size | Subnet Mask            | Usable Hosts | IP Address Range          |
|---------------------|----------------|-------------|------------------------|--------------|---------------------------|
| Finance             | 75             | `/25`       | 255.255.255.128         | 126          | 10.0.0.0 - 10.0.0.127      |
| Human Resources     | 45             | `/26`       | 255.255.255.192         | 62           | 10.0.0.128 - 10.0.0.191    |
| Sales               | 105            | `/25`       | 255.255.255.128         | 126          | 10.0.0.192 - 10.0.1.63     |
| Marketing           | 60             | `/26`       | 255.255.255.192         | 62           | 10.0.1.64 - 10.0.1.127     |
| IT                  | 150            | `/24`       | 255.255.255.0           | 254          | 10.0.1.128 - 10.0.2.127    |
| Operations          | 120            | `/25`       | 255.255.255.128         | 126          | 10.0.2.128 - 10.0.3.63     |

### **3. Subnet Masking**

Here’s a detailed breakdown of the subnet masks:

- **Finance**: `/25` → 255.255.255.128 → IP range: 10.0.0.0 - 10.0.0.127 (126 usable hosts)
- **Human Resources**: `/26` → 255.255.255.192 → IP range: 10.0.0.128 - 10.0.0.191 (62 usable hosts)
- **Sales**: `/25` → 255.255.255.128 → IP range: 10.0.0.192 - 10.0.1.63 (126 usable hosts)
- **Marketing**: `/26` → 255.255.255.192 → IP range: 10.0.1.64 - 10.0.1.127 (62 usable hosts)
- **IT**: `/24` → 255.255.255.0 → IP range: 10.0.1.128 - 10.0.2.127 (254 usable hosts)
- **Operations**: `/25` → 255.255.255.128 → IP range: 10.0.2.128 - 10.0.3.63 (126 usable hosts)

### **4. Documentation**

| Department          | IP Range                   | Purpose                                                     |
|---------------------|----------------------------|-------------------------------------------------------------|
| **Finance**         | `10.0.0.0 - 10.0.0.127`    | Financial transactions and accounting systems                |
| **Human Resources** | `10.0.0.128 - 10.0.0.191`  | Employee data and payroll systems                            |
| **Sales**           | `10.0.0.192 - 10.0.1.63`   | CRM and sales data                                           |
| **Marketing**       | `10.0.1.64 - 10.0.1.127`   | Marketing campaigns and analytics                            |
| **IT**              | `10.0.1.128 - 10.0.2.127`  | Network infrastructure, servers, and support systems         |
| **Operations**      | `10.0.2.128 - 10.0.3.63`   | Production, supply chain, and operations management          |

### **5. Troubleshooting Scenarios**

- **Connectivity Issues**:
  - Check routing tables and ensure correct routes are set up between subnets.
  - Verify firewall rules allow communication between subnets if needed.
- **IP Conflicts**:
  - Review DHCP server logs to check for duplicate IPs.
  - Consider manually assigning static IP addresses for critical devices to avoid conflicts.
- **Overlapping Subnets**:
  - Ensure each department has a unique IP range.
  - Double-check subnet masks to prevent overlaps.

### **6. Future Growth**

- **Expand Subnets**: Adjust subnet masks if additional hosts are needed (e.g., expand Finance from `/25` to `/24` for more hosts).
- **New Subnets**: Allocate additional subnets for new departments or organizational growth.
- **Update Documentation**: Keep IP ranges and subnet masks documented for future changes.

### **7. Optimization**

- **Routing Efficiency**: Use routing protocols (e.g., OSPF, EIGRP) for efficient traffic handling between subnets.
- **VLANs**: Implement VLANs to segment traffic between departments while keeping the network secure and scalable.
- **DHCP**: Use DHCP for dynamic IP assignment, and reserve static IPs for servers, printers, or other critical devices.
- **Monitoring and Alerts**: Set up network monitoring tools to detect potential IP conflicts or subnet issues early.

