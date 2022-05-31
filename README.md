# Ansible Playbook for Kafka Operation

## Overview
An ansible role to simple operation kafka like
- [x] Get List Topic
- [x] Describe Topic
- [x] Get List User SCRAM
- [x] Create User SCRAM
- [x] Get List ACL
- [ ] Create User ACL Producer
- [ ] Create User ACL Consumer

### Getting Started
These instructions will get you a copy of the project up and running on your local machine or bastion host. 

### Prerequisites
Prerequisite Package :
```
ansible==2.6.20
cryptography==2.5
```

Just run ```pip install -r requirements.txt``` for install prerequisite packages

### How to Run
Before run ansible playbook please note that this playbook using tag for spesific task.

There are several type tags :
- kafka_topic_list
- kafka_topic_describe
- kafka_user_list
- kafka_user_create
- kafka_ACL_list
- etc


- Run Playbook
```
ansible-playbook -i inventory/<inventory-name-per-playbook>/hosts.ini playbook/<playbook-name> -t <type-tags>
```

Example
```
ansible-playbook -i inventory/ins-kafka-lab-maas/hosts.ini playbook/ins-kafka-lab-maas.yml -t kafka_topic_list
```


## Authors

* **Aas Suhendar** - *Initial Work* - [AasSuhendar](https://github.com/AasSuhendar)

See also the list of [contributors](https://github.com/AasSuhendar/ansible-kafka-operations/contributors) who participated in this project
