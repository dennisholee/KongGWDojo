# Kong Gateway

## Execute Kong's Ansible playbook

1. Create host file based on environment.
Note the 'hosts' file needs to be harden for real usage.
```
# cat hosts
[nodes]
node.1 ansible_host=${hostname_or_ipaddress} ansible_user=${ssh_username} ansible_password=${ssh_password} ansible_become_password=${sudo_password}
```

2. Apply the playbook.
```
ansible -i hosts  all -m ping

ansible-playbook -i hosts konggw-dependencies.yml
```

3. Start Kong gateway
```
kong start -c /etc/kong/kong.conf
```

4. Check the Kong gateway is running
```
curl http://${host}:8001
```

5. Test the proxy connection to the XRP API
```
curl http://${host}:8000/wallets
```
