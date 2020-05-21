## 概要

Ansible用playbookです
サーバ証明書／クライアント証明書を発行します。

## 自動設定内容

1. 発行したい証明書情報をCSVファイルに登録
    
$ cat server-certs.csv 
name,country,state,locality,organization,organizational_unit
myhome.local,JP,Osaka,Osaka,MyHome,MyHome

$ cat client-certs.csv 
name,mailaddr,pass,organizational_unit
user001,user001@myhome.local,pass001,Development
user002,user002@myhome.local,pass002,Production
user003,user003@myhome.local,pass003,Sales


### playbook実行

ansibleサーバで実行
```
git clone https://github.com/mishikawan/generatecert-ansible.git
ansible-playbook generate_certs.yml
```

