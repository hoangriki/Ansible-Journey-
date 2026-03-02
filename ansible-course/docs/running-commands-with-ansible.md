# 🚀 Running Commands with Ansible

Ansible lets you execute commands on remote hosts quickly and consistently using ad-hoc commands. These are one-off tasks — perfect for testing connectivity, checking system status, or troubleshooting prior to writing full playbooks.

---

## 📌 1) Ansible Ad-Hoc Commands

An ad-hoc command has this basic format:

```bash
ansible <group_or_host> -m <module> -a "<arguments>"
```
<group_or_host> → Target defined in inventory

-m → Module to use

-a → Arguments for that module

) Basic Ping

The simplest command you can run:

ansible all -m ping

This uses the ping module (not ICMP) to test Ansible connectivity.
If successful you’ll see:

host | SUCCESS => pong


🛠 3) Running Shell/Command

Ansible has two modules for remote command execution:

| Module    | Behavior                                                          |
| --------- | ----------------------------------------------------------------- |
| `shell`   | Runs via remote shell (`bash`) and supports pipes, chaining, etc. |
| `command` | Runs commands without shell processing (safer, no pipes)          |

Using command

ansible all -m ansible.builtin.command -a "uptime"

Output shows remote load and uptime.

🔹 Using shell

ansible all -m ansible.builtin.shell -a "df -h"

Runs with shell context — good for complex commands.

📊 4) Using Variables in Commands

You can interpolate inventory/group variables:

ansible webservers -m shell -a "echo $HOSTNAME"

On managed hosts it will print each host’s name.

🛡 5) Running with Privilege Escalation

If a command requires root, add --become:

ansible all -m ansible.builtin.shell -a "whoami" --become

You may be prompted for a password — unless configured in ansible.cfg.

🔎 6) Examples of Useful Ad-Hoc Commands
📌 Check disk usage

ansible all -m shell -a "df -h"

📌 List packages
ansible all -m shell -a "apt list --installed"

📌 Restart a service
ansible webservers -m ansible.builtin.service -a "name=nginx state=restarted"

💡 Best Practices

✅ Prefer modules (e.g., service, package) when possible
✅ Use shell only when necessary
✅ Keep ad-hoc commands simple and idempotent when possible

🧠 Summary
| Task              | Command                                                         |
| ----------------- | --------------------------------------------------------------- |
| Test connectivity | `ansible all -m ping`                                           |
| Run uptime        | `ansible all -m command -a "uptime"`                            |
| Check disk space  | `ansible all -m shell -a "df -h"`                               |
| Restart service   | `ansible webservers -m service -a "name=nginx state=restarted"` |

leverage Ansible ad-hoc commands to interactively manage your infrastructure — a powerful productivity boost before writing full playbooks.


---

## 📌 Where to Put It

Add this to:
