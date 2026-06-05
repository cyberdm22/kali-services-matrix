[# Core Network Services & Exploitation Matrix: HTTP & SSH
An advanced reference repository tracking the architecture, configuration, defensive controls, and offensive methodologies associated with core Linux networking services. Built to serve as both a technical deep-dive and an intersectional reference for Cyber Law and Information Security practitioners.

## 🛠️ Repository Architecture
* **[HTTP_SERVICE.md](./HTTP_SERVICE.md):** Deep-dive into Web Server architectures (Apache2 vs Nginx), process isolation boundaries, credential harvesting mechanics, and Layer 7 attack/defense dynamics.
* **[SSH_SERVICE.md](./SSH_SERVICE.md):** Architectural breakdown of the Secure Shell protocol across the OSI model, asymmetric/symmetric cryptographic pipelines, secure tunneling/pivoting configurations, and authentication vulnerabilities.

## 🚀 Step-by-Step Local Deployment Guide

Follow these instructions to clone, verify, and interact with these services locally within an authorized environment (e.g., Kali Linux).

### 1. Service Enumeration and Analysis
To check the operational status of local sockets and map out daemon processes, use the following network statistics commands. Note that the process identifier (`-p`) requires root privileges due to kernel-level process isolation boundaries.

```bash
# Enumerate all listening TCP sockets and identify running services
sudo netstat -antp

# Specific filter to verify if Apache2 is bound to Port 80
sudo netstat -antp | grep apache

# Specific filter to verify if Nginx is bound to Port 80
sudo netstat -antp | grep nginx

# Modern alternative to netstat for socket enumeration
sudo ss -antpl]
