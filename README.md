httpd
==============

This role is used to deploy httpd(supporting tls configuration).


Inventory file demo
-------------------

```
httpd-1 ansible_ssh_host=192.168.168.200 ansible_ssh_port=3322 ansible_ssh_user=centos

[httpd]
httpd-1
```

Notice:

* ansible_ssh_host variable in the inventory file is requried for httpd configurations


Role Variables
--------------
No required vars, the optional var as follows:


If you want to change the http protocal listening port, set **httpd_listen_port** variable:

```
httpd_listen_port: 18080
```

If you want to config httpd to use ssl, set **config_ssl** variable:

```
config_ssl: true
```

If you want to automatically generating ssl private key and cert, set the following variables:

```
config_ssl: true
ssl_auto_generate_key_and_cert: true
ssl_cert_validate_days: 3650
ssl_private_key_path: /etc/pki/tls/private/httpd.key
ssl_cert_path: /etc/pki/tls/certs/httpd.cert
ssl_cert_cn: 192.168.168.200
```

> Note: ssl_cert_cn should be the ip or hostname of the https server


If you want to use existed ssl private key and cert, set the following variables:

```
config_ssl: true
ssl_auto_generate_key_and_cert: false
ssl_private_key_path: /etc/pki/tls/private/httpd.key
ssl_cert_path: /etc/pki/tls/certs/httpd.cert
```


If you want to change the https protocal listening port, set **httpd_ssl_listen_port** variable:

```
httpd_ssl_listen_port: 443
```


Example Playbook
----------------

```
---
- hosts: httpd
  become: true
  roles:
    - frank6866.httpd
```


License
-------

MIT

