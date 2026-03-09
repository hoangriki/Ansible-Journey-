From your repo root:

```
ansible-playbook -i inventory/hosts.ini advanced-playbooks/nginx-webserver.yml

```

Example targeting web servers:
```
ansible webservers -m ping
```
