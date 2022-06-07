# Ansible Playbook for Kafka Operation

## Overview
An ansible role to simple operation kafka like
- [x] Get List Topic
- [x] Create Topic
- [x] Describe Topic
- [x] Delete Topic
- [x] Get List User SCRAM
- [x] Create User SCRAM
- [x] Delete User SCRAM
- [x] Get List ACL
- [x] Create User ACL Producer
- [x] Delete User ACL Producer
- [x] Create User ACL Consumer
- [x] Delete User ACL Consumer

### Getting Started
These instructions will get you a copy of the project up and running on your local machine or bastion host. 

### Prerequisites
Prerequisite Package :
```
ansible==2.6.20
cryptography==2.5
```

Just run ```pip install -r requirements.txt``` for install prerequisite packages

### Inventory
This is some example for Inventory
```
[kafka]
192.168.10.10 
```

### Playbook
Playbook run for each kafka cluster. Let say you have some cluster, so you have to create each file playbook for that kafka cluster.

```
inventory
	- kafka-cluster-1
		- hosts.ini
	- kafka-cluster-2
		- hosts.ini
playbook
	- kafka-cluster-1.yml
	- kafka-cluster-2.yml
   
```

This is some vars example for run playbook
```
# vars for create new kafka user
new_kafka_user_username: logeedistr
new_kafka_user_password: logeedistr-Pass

# vars for remove kafka user
deleted_kafka_username: logeedistr

# vars for create new topic
new_topic_name: logee-logee-inbox

# vars for remove topic
deleted_topic_name: test-topic-cmak

# vars for user access as that user for execute some action like kafka list topic, kafka describe topic etc
kafka_user: admin
kafka_pass: adminPass

# vars for create/remove ACL as Consumer to user with prefixed topic
acl : {
      kafka_user: user1,
      topic_name: indicar-v1-,
      type: consumer,
      group: indicar-consumers-
    }

# vars for create/remove ACL as Delete to user with prefixed topic
acl : {
      kafka_user: user1,
      topic_name: indicar-v1-,
      type: producer
    }

# vars for get list ACL with spesifix topic
acl_search : {
      topic_name: logeedistr-,
      resource_pattern: prefixed
    }
```

### How to Run
Before run ansible playbook please note that this playbook using tag for spesific task.

There are several type tags :
- kafka_topic_list
- kafka_topic_describe
- kafka_topic_create
- kafka_topic_remove
- kafka_user_list
- kafka_user_create
- kafka_user_remove
- kafka_acl_list
- kafka_acl_create
- kafka_acl_remove
- etc soon

## Run Playbook
```
ansible-playbook -i inventory/<inventory-name-per-playbook>/hosts.ini playbook/<playbook-name> -t <type-tags>
```

Example
```
ansible-playbook -i inventory/kafka-cluster-1/hosts.ini playbook/kafka-cluster-1.yml -t kafka_topic_list
```


## Authors

* **Aas Suhendar** - *Initial Work* - [AasSuhendar](https://github.com/AasSuhendar)

See also the list of [contributors](https://github.com/AasSuhendar/ansible-kafka-operations/contributors) who participated in this project
