# kubernetes-workshop
1) `vagrant up`

2) kubemaster setup

2.1) `vagrant ssh kubemaster`

2.2) `sudo -i`

2.3) `yum install wget -y`

2.4) `wget https://raw.githubusercontent.com/osipex/kubernetes-workshop/main/vm-config.sh`

3) `sh vm-config.sh`

4) `kubeadm init --apiserver-advertise-address=192.168.56.2 --pod-network-cidr 10.32.0.0/12`

Successfull init msg should appear. E.g:

Your Kubernetes control-plane has initialized successfully!

To start using your cluster, you need to run the following as a regular user:

  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config

You should now deploy a pod network to the cluster.
Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
  https://kubernetes.io/docs/concepts/cluster-administration/addons/

Then you can join any number of worker nodes by running the following on each as root:

kubeadm join 192.168.56.2:6443 --token x2iqyd.2ee3cylxcit8ofm5 \
    --discovery-token-ca-cert-hash sha256:fcfbbc61880c9792f56aa08649df533926c7b54d5e58d04095d1639c58ff9bbf
    
5) kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"
