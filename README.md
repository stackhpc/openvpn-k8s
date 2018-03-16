# openvpn-setup

Add the following to your `~/.ssh/config` to jump to remote hosts

```
Host 172.17.8.*
  User centos
  IdentityFile ~/.ssh/k8s
  ProxyCommand ssh -q -W %h:%p 78.31.111.99 #-q only required on Mac
Host 78.31.111.99
  User centos
  IdentityFile ~/.ssh/id_rsa
  ForwardAgent yes
```

Then run:

```
ansible-playbook -i inventory/hybrid/hosts.ini -b openvpn.yml
