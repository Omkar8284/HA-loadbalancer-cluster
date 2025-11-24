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



🏗️ Architecture

<img width="1024" height="1024" alt="image" src="https://github.com/user-attachments/assets/87918817-2da0-4fdb-b87a-d2bc09f5e5c7" />


Done!!
