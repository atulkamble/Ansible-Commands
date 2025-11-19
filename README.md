# 📝 **Ansible Commands Cheat Sheet (Trainer-Ready)**

## 🔧 **1. Basic Ansible Commands**

| Purpose                       | Command                                |
| ----------------------------- | -------------------------------------- |
| Check Ansible version         | `ansible --version`                    |
| Check hosts connectivity      | `ansible all -m ping`                  |
| Run a command on all hosts    | `ansible all -a "uptime"`              |
| Run with a specific inventory | `ansible -i inventory.ini all -m ping` |
| Specify user                  | `ansible all -m ping -u azureuser`     |
| Ask password (SSH)            | `ansible all -m ping --ask-pass`       |

---

## 🗂 **2. Inventory Management**

| Description                 | Command                       |
| --------------------------- | ----------------------------- |
| List all hosts              | `ansible all --list-hosts`    |
| Target a group              | `ansible webservers -m ping`  |
| Target a single host        | `ansible node1 -m ping`       |
| Check inventory syntax      | `ansible-inventory --list -y` |
| Graphical view of inventory | `ansible-inventory --graph`   |

---

## 🧩 **3. Modules (Common)**

| Module        | Purpose                  | Command Example                                                    |
| ------------- | ------------------------ | ------------------------------------------------------------------ |
| `ping`        | Connectivity test        | `ansible all -m ping`                                              |
| `shell`       | Run shell commands       | `ansible all -m shell -a "df -h"`                                  |
| `command`     | Run commands (safer)     | `ansible all -m command -a "whoami"`                               |
| `copy`        | Copy files               | `ansible all -m copy -a "src=/tmp/a dest=/tmp/b"`                  |
| `file`        | Permissions, owner, mode | `ansible all -m file -a "path=/tmp/test mode=777"`                 |
| `yum` / `apt` | Package install          | `ansible all -m yum -a "name=httpd state=present"`                 |
| `service`     | Manage services          | `ansible all -m service -a "name=httpd state=started enabled=yes"` |
| `user`        | Manage users             | `ansible all -m user -a "name=atul state=present"`                 |

---

## 📦 **4. Playbook Commands**

| Action                 | Command                                             |
| ---------------------- | --------------------------------------------------- |
| Run a playbook         | `ansible-playbook site.yml`                         |
| Run with inventory     | `ansible-playbook -i inventory.ini site.yml`        |
| Check syntax           | `ansible-playbook site.yml --syntax-check`          |
| Dry run / preview      | `ansible-playbook site.yml --check`                 |
| Limit to specific host | `ansible-playbook site.yml --limit web01`           |
| Run specific tag       | `ansible-playbook site.yml --tags "install"`        |
| Skip a tag             | `ansible-playbook site.yml --skip-tags "configure"` |
| Verbose output         | `ansible-playbook site.yml -vvv`                    |

---

## 🔐 **5. Ansible Vault**

| Purpose                      | Command                                      |
| ---------------------------- | -------------------------------------------- |
| Create encrypted file        | `ansible-vault create secrets.yml`           |
| Edit encrypted file          | `ansible-vault edit secrets.yml`             |
| View encrypted file          | `ansible-vault view secrets.yml`             |
| Encrypt existing file        | `ansible-vault encrypt file.yml`             |
| Decrypt file                 | `anssible-vault decrypt file.yml`            |
| Run playbook with vault pass | `ansible-playbook site.yml --ask-vault-pass` |

---

## ⚙️ **6. Ad-Hoc Commands**

| Use case               | Command                                            |
| ---------------------- | -------------------------------------------------- |
| Install package        | `ansible all -m apt -a "name=nginx state=present"` |
| Change file permission | `ansible all -m file -a "path=/data mode=755"`     |
| Copy file              | `ansible all -m copy -a "src=test.txt dest=/tmp/"` |
| Gather facts           | `ansible all -m setup`                             |
| Reboot hosts           | `ansible all -m reboot`                            |

---

## 🧪 **7. Facts & Debugging**

| Purpose              | Command                                              |
| -------------------- | ---------------------------------------------------- |
| Gather all facts     | `ansible all -m setup`                               |
| Show selected fact   | `ansible all -m setup -a "filter=ansible_os_family"` |
| Show variables       | `ansible all -m debug -a "var=ansible_hostname"`     |
| Print custom message | `ansible all -m debug -a "msg='Hello Atul'"`         |

---

## 🛠 **8. Roles Management**

| Action                              | Command                                      |
| ----------------------------------- | -------------------------------------------- |
| Create role structure               | `ansible-galaxy init myrole`                 |
| Install role                        | `ansible-galaxy install geerlingguy.mysql`   |
| Install roles from requirements.yml | `ansible-galaxy install -r requirements.yml` |
| List installed roles                | `ansible-galaxy list`                        |

---

## 🌐 **9. Useful Options**

| Option              | Description         |
| ------------------- | ------------------- |
| `-u`                | SSH user            |
| `--become` or `-b`  | Run as sudo         |
| `--ask-become-pass` | Ask sudo password   |
| `--ask-pass`        | Ask SSH password    |
| `--ask-vault-pass`  | Ask vault password  |
| `-vvv`              | Debug level verbose |

---

## 🏁 **10. Quick Troubleshooting**

| Problem           | Solution                      |
| ----------------- | ----------------------------- |
| SSH issue         | `ansible all -m ping -vvv`    |
| Wrong inventory   | `ansible-inventory --list -y` |
| Permissions error | Use `-b` or check sudoers     |
| Playbook syntax   | `--syntax-check`              |
| Variable error    | Use `debug` module            |

---
