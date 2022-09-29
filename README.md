# isd-ap-quick-install

**Quick install for ISD Services only.**

To experience ISD quickly, you can install it and deploy your applications. Note that the instructions below are intended to get you started quickly and try out ISD functionality. This is not suitable for production or any environment where security is a concern.
To begin installation, you'll need a Kubernetes cluster  (with 2 nodes with 32GB RAM each) and kubectl set-up.

**This is the ISD Autopilot which supports only for Argo**.

## Steps to be followed
- **Clone the repository**

      git clone https://github.com/OpsMx/isd-ap-quick-install.git

- **Namespace will be created automatically**

- **Apply the yaml files**

      kubectl -n opsmx-autopilot apply -f https://raw.githubusercontent.com/OpsMx/isd-ap-quick-install/main/ap-without-argo/ap-quickinstall.yaml

- **Create opsmx11 secret**

   Below Secret need to be created, Please updated the **password**

      kubectl create secret docker-registry opsmx11-secret --docker-server=docker.io --docker-username=opsmx11 --docker-password=xxxxx --docker-email=saiteja.katabhatina@opmx.io -n opsmx-autopilot

   WAIT for about 10-15 min, depending on network speed.
 
   It is normal for some pods to go into error/crashloop before stabilising.

 - **Check the status of the pods by executing this command**

       kubectl -n opsmx-autopilot get po

 - **Port-forward the service**
 
     Once all pods show "Running" or "Completed" status, execute below command below to port-forward
      
     Keep running, it shows messages such as "Forwarding from 127.0.0.1:8080 -> 8080"
       
       kubectl -n opsmx-autopilot  port-forward svc/oea-ui 8080 
      

 - **Access the UI**
      
     Login using browser with http://localhost:8080  
     
     - username **admin**
     - password **opsmxadmin123**
