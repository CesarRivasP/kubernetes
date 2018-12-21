# Install Kubernetes

### 1.- First, Run the script kubernetes-install-script1.sh

### 2.- Then 'kubectl describes pod' will assign a 'guids', enter it with the following command:

**Example guids: guids-7cdb55649f-976pj**

	kubectl describe pod "enter the guids" | grep IP:

### 3.- Done that...

The command will return an IP address, which must be entered 2 times in the next command

	curl http://"IP ADDRESS":9000/guid ; echo


### 4.- Done the two previous steps, add your 'guids' to the following two commands

	kubectl logs "enter the guids"
	kubectl exec -t -i "enter the guids" sh


### 5.- In this last step, you must enter the following:

	head -n3 /etc/os-release

### 5.1.- And to finish that step 'exit'

### 6.- Once all the steps above are completed, run kubernetes-install-script2.sh

### 7.- Enter the following route to the browser:

	http://"ip-address":8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/#!/login

### Other sentences
In case of errors when trying to run kubernetes, some of these sentences can help solve the problem ...

	sudo systemctl enable kubelet

	sudo systemctl start kubelet

	sudo kubeadm init --ignore-preflight-errors=all

	sudo kubectl cluster-info
