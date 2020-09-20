# Technical-Assignment-2
Technical Task Details:
- Based on minikube
- Deploy 3 replicas of nginx/apache
- Include a simple "hello world" in the index.html of nginx/apache
- Deploy 1 replica of tomcat v8
- Deploy sample.war to tomcat deployment (use this:
https://tomcat.apache.org/tomcat-8.0-doc/appdev/sample/ )
- Deploy a jenkins pod (1 replica)
- Configure a static "dummy" job in jenkins
- Submit the project as a set of yaml manifests, Dockerfiles, bash scripts, xml files, and anything else
you deem appropriate.
- Include a simple/short README file that tells how to operate the project.


# Steps Followed

# Install Minukube 
curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 \
  && chmod +x minikube
sudo mkdir -p /usr/local/bin/
sudo install minikube /usr/local/bin/
minikube start --driver=docker
# verify minikube status
minikube status
# start minikube 
minikube start

# Install Helm
curl https://baltocdn.com/helm/signing.asc | sudo apt-key add -
sudo apt-get install apt-transport-https --yes
echo "deb https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
sudo apt-get update
sudo apt-get install helm

# Create and install Helm Chart for Nginx deployment
 helm create myassignment
 Change --> Myassignment --> values.yaml
 helm install my-bb-assign myassignment/ --values myassignment/values.yaml
  244  export NODE_PORT=$(kubectl get --namespace default -o jsonpath="{.spec.ports[0].nodePort}" services bb-assign-helm)
  245  export NODE_IP=$(kubectl get nodes --namespace default -o jsonpath="{.items[0].status.addresses[0].address}")
  246  echo http://$NODE_IP:$NODE_PORT
  247  kubectl get svc
  248  curl -v http://172.17.0.3:30873
  
# Create and install Helm Chart for Tomcat deployment
  helm create mytomcatbbchart
  change --> Myassignment --> values.yaml
  helm install my-kanbbtomcat-chart mytomcatbbchart/ --values mytomcatbbchart/values.yaml
  572  export NODE_PORT=$(kubectl get --namespace default -o jsonpath="{.spec.ports[0].nodePort}" services kamal-bb-tomcat)
  573  export NODE_IP=$(kubectl get nodes --namespace default -o jsonpath="{.items[0].status.addresses[0].address}")
  574  echo http://$NODE_IP:$NODE_PORT
  575  curl -v http://172.17.0.3:32475
  
# Create and install Helm Chart for Tomcat deployment
  







