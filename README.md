## 概要

Ansible用playbookです
サーバ証明書／クライアント証明書を発行します。

### playbook実行


1. git clone

```
git clone https://github.com/mishikawan/generatecert-ansible.git
```


2. csvファイルの編集

2.1  generate_certs.yml 
```
- hosts: 127.0.0.1
  gather_facts: False
  vars:
    ca_private: "~/easy-rsa/pki/private/ca.key"
    ca_public: "~/easy-rsa/pki/ca.crt"
    publicdir: "~/easy-rsa/pki/issued"
    csrdir: "~/easy-rsa/pki/reqs"
    privatedir: "~/easy-rsa/privates"
    pkcs12dir: "~/easy-rsa/privates"
    server_csv: "server-certs.csv"
    client_csv: "client-certs.csv"
```


2-2. server-certs.csv 
```
name,country,state,locality,organization,organizational_unit
myhome.local,JP,Osaka,Osaka,MyHome,MyHome
```

2-3. client-certs.csv 
```
name,mailaddr,pass,organizational_unit
user001,user001@myhome.local,pass001,Development
user002,user002@myhome.local,pass002,Production
user003,user003@myhome.local,pass003,Sales
```

3. ansible実行

```
ansible-playbook generate_certs.yml
```

