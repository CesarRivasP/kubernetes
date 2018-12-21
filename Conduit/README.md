# Install Conduit CLI

	   curl https://run.conduit.io/install | sh
	   export PATH=$PATH:$HOME/.conduit/bin

## To add Conduit CLI, to your path permanently you can also edit your ~/.bashrc to add path and reload it. For .zshrc, I added following line.

	   export PATH="$HOME/.conduit/bin:$PATH"

- To verify if everything is in place now, run the following command that should print the client and server version

    conduit version


- Initially, the server version will not be available since we have not yet created the control plane.


# Install Conduit Control Plane

## Running below command generates a Kubernetes config file, and then pipes it to kubectl.

    conduit install | kubectl apply -f -

    conduit install my-namespace | kubectl apply -f -

## At this point, control plane should be up and running. We can validate this by opening Conduit dashboard

    conduit dashboard


- Example with emojivoto


- First, we are going to clone the repository

   **git clone https://github.com/runconduit/conduit-examples.git
    cd conduit-examples/emojivoto**


## Second, we will create data plane for this emojivoto app
    conduit inject emojivoto.yml --skip-inbound-ports=80 | kubectl apply -f -


##   To see the status in real time of the conduit pods

	watch kubectl --namespace=conduit get po -l conduit.io/control-plane-ns=conduit
