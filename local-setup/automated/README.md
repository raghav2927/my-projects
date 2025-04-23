# Automated Setup – VProfile Project

This folder automates the VProfile infrastructure using Vagrant and provisioning scripts.

### 🧰 Stack & Tools
- Vagrant
- Shell Scripts
- Oracle VirtualBox

### 🖥️ VMs Created
| VM        | Role            |
|-----------|------------------|
| db01      | MariaDB          |
| mc01      | Memcache         |
| rmq01     | RabbitMQ         |
| app01     | Tomcat + App     |
| web01     | Nginx            |

### ▶️ How to Run
```bash
vagrant plugin install vagrant-hostmanager
vagrant up
```
