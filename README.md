#  Automating deploy  multimaster k8s cluster with kubeadm with ansible


in this project i deploy a multi master k8s cluster with kubeadm.The CNI that use is Flsnnel. You can have your k8s cluster in less than 10mins with this ansible.

## What each role does?
There are 6 roles that describe what each of them does in order they have to run in servers below:

#### 1- [haproxy](https://github.com/mona-mp/HA-K8sCluster-ansible/tree/main/roles/haproxy "haproxy") :
Because whe have multiple masters we need a Haproxy to load balance the traffic to all healthy control plane nodes in its target list.
Whenever yo add new node in master group in your inventoury it will add to haproxy targets in template file.

#### 2- [k8s-prerequsites](https://github.com/mona-mp/HA-K8sCluster-ansible/tree/main/roles/k8s-prerequsites "k8s-prerequsites") : 

in this role all the prerequsites that reqiured for k8s cluster will installed .it has to run in all nodes in cluster.

#### 3- [k8s-firstmaster-initialize](https://github.com/mona-mp/HA-K8sCluster-ansible/tree/main/roles/k8s-firstmaster-initialize "k8s-firstmaster-initialize") :

the first master is  intialized in this role and the cni is applyed.

#### 4- [k8s-join-master/tasks](https://github.com/mona-mp/HA-K8sCluster-ansible/tree/main/roles/k8s-join-master/tasks "This path skips through empty directories") : 

Use this role to join new master.

#### 5- [k8s-prerequsites](https://github.com/mona-mp/HA-K8sCluster-ansible/tree/main/roles/k8s-prerequsites "k8s-prerequsites") : 

Use this role to join a new worker.
