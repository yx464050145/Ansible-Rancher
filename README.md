Ansible-Rancher
==============

This role uses docker to build rancher2 on Linux server
It has three roles
 - 1. rancher-server
 - 2. rancher-master :k8s master node
 - 3. rancher-worker :k8s worker node

It has four functions
 - 1. Building the lancher server container
 - 2. Build k8s cluster and join rancher
 - 3. Build k8s cluster's project
 - 4. BUild k8s app and Start some services，app git address is mayun


rancher-server roles
-------------
- rancher_name: 'rancher_server'  > rancher server container name
- rancher_port: 80 > rancher server container http port
- rancher_image: rancher/rancher:stable > rancher server container image
- rancher_data: /var/rancher > rancher server container volumes 
- rancher_ssl_ports: 443 > rancher server https port
- rancher_url: "https://" > rancher server url
- rancher_admin_password: "" > rancher server login password 
- validate_certs: false  > do not use ssl

rancher-master roles
--------------------
- rancher_network_provider: "calico"
- rancher_cluster_name: bangwo8
- rancher_master_role: "--etcd --controlplane"      > node roles
- rancher_project_name: "bangni8"
- rancher_app_name: "bangwo8"
- rancher_app_password: ""
- rancher_app_url: ""
- rancher_app_username: ""
- log_values: ""
- log_pilot_version: ""
- bangwo8_version: ""
- aliyun_sls_access_key_id: ""
- aliyun_sls_access_key_secret: ""
- aliyun_username: ""   > aliyun Authentication username
- aliyun_password: ""  > aliyun Authentication password 

rancher-worker roles
--------------------
- rancher_url: ""
- rancher_admin_password: "bangwo8"
- validate_certs: false
- rancher_network_provider: "calico"
- rancher_cluster_name: bangwo8
- rancher_worker_role: "--worker"  > node roles


LICENSE
--------
SXU

THANKS
-------
https://github.com/sylflo-ansible-kubernetes/rancher2-ansible
