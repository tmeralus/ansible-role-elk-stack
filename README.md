# ansible-elasticsearch
An ansible playbook that installs elasticsearch 7.0.0

## Requirements
This playbook prompts for Session or Cache cluster
This only affects the parameters saved in the redis.conf file.

Cache Cluster: saves redis data in memory (normal behavior in an LRU/Memcached setup)
Session Cluster: saves data on disk (Setup for using Redis as a Sesssion store)


## Role Variables
### all variables can be found under group_vars/all.yml file
- es_listen_external: true
- elk_server_ssl_cert_port: 8080
- es_network_host: localhost
- es_path_data: /var/lib/elasticsearch
- es_path_logs: /var/log/elasticsearch
- es_http_port: "9200"
- elastic_version: 7.1.1
- elastic_repo_version: 7.x
- elk_repo_url: https://artifacts.elastic.co/packages/{{ elastic_repo_version }}/yum
- es_bootstrap_memory_lock: true # True | false
- es_jvm_options: "-Xms4g"
- sentinel_failtime: 800
- ansible_system_user: ansible
- epel_repo: https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
- yum_repo_gpgkey: https://artifacts.elastic.co/GPG-KEY-elasticsearch
- manage_firewall: true
- es_node_master: true
- gateway_recover_after_nodes: 3
- discovery_zen_minimum_master_nodes: 3
- action_destructive_requires_name: "true"
- es_discovery_zen_ping_unicast_hosts: ["127.0.0.1","127.0.0.2","127.0.0.3",]
- es_cluster_routing_allocation_same_shard_host: true

## Dependencies

## Test Playbook
 ansible-playbook -i inventory/local -l elk ansible-role-elk-stack/elk.yml

 Inventory group should be labeled as [elk]
 Example:
 [elk]
 dolly01

License
GNU GPLv3


Author Information
 Twitter: @TechGameTeddy
