Overview
This project provides a comprehensive, tested configuration for deploying a two-node high-availability load balancer cluster. The cluster uses:

HAProxy - Layer 4/7 load balancer for distributing traffic
Keepalived - VRRP implementation for floating VIP management
Nginx - Backend web servers for content delivery

Why This Setup?
✅ Zero Downtime - Automatic failover in 1-2 seconds
✅ Load Distribution - Round-robin traffic balancing
✅ Health Monitoring - Automatic backend health checks
✅ Easy Maintenance - Take nodes offline without service interruption
✅ Production Ready - Tested configurations with SELinux support

✨ Features

🔄 Automatic Failover: Keepalived detects failures and migrates VIP instantly
⚖️ Load Balancing: HAProxy distributes traffic using the round-robin algorithm
🏥 Health Checks: Backend servers monitored every 2 seconds
🔒 SELinux Compatible: Proper permissions configured for RHEL 9
📊 Monitoring Ready: HAProxy stats endpoint available
🛡️ Security Focused: VRRP authentication and configurable firewall rules
📝 Well Documented: Complete runbook with troubleshooting guide


<img width="1024" height="1024" alt="image" src="https://github.com/user-attachments/assets/87918817-2da0-4fdb-b87a-d2bc09f5e5c7" />


🚀 Quick Start

1. Clone Repository
bashgit clone https://github.com/Omkar8284/ha-loadbalancer-cluster.git
cd ha-loadbalancer-cluster
2. Install Packages (Both Nodes)
bashsudo dnf install -y nginx haproxy keepalived policycoreutils-python-utils
3. Deploy Configurations
On Node1 (MASTER):
bash# Copy configuration files
sudo cp node1/nginx.conf /etc/nginx/nginx.conf
sudo cp node1/haproxy.cfg /etc/haproxy/haproxy.cfg
sudo cp node1/keepalived.conf /etc/keepalived/keepalived.conf
sudo cp node1/index.html /usr/share/nginx/html/index.html

# Configure SELinux
sudo setsebool -P haproxy_connect_any 1

# Start services
sudo systemctl enable --now nginx haproxy keepalived
On Node2 (BACKUP):
bash# Copy configuration files
sudo cp node2/nginx.conf /etc/nginx/nginx.conf
sudo cp node2/haproxy.cfg /etc/haproxy/haproxy.cfg
sudo cp node2/keepalived.conf /etc/keepalived/keepalived.conf
sudo cp node2/index.html /usr/share/nginx/html/index.html

# Configure SELinux
sudo setsebool -P haproxy_connect_any 1

# Start services
sudo systemctl enable --now nginx haproxy keepalived
4. Verify Setup
bash# Check VIP assignment (should be on Node1)
ip addr show | grep 192.168.59.100

# Test from client
curl http://192.168.59.100

🏗️ Architecture

<img width="1024" height="1024" alt="image" src="https://github.com/user-attachments/assets/218f9959-682f-4dfa-8707-c2aed64dbff6" />



📁 Configuration Files
![Uploading image.png…]()


Done!!
