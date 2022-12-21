# isd-rollouts-quick.yaml 

**Quick Install for ISD and Argo-rollouts**.

To experience ISD quickly, you can install it and deploy your applications. Note that the instructions below are intended to get you started quickly and try out ISD functionality. This is not suitable for production or any environment where security is a concern.
To begin installation, you'll need a Kubernetes cluster  (with 2 nodes with 32GB RAM each) and kubectl set-up.

## Steps to be followed

- **Namespace will be created automatically**

- **Apply the yaml files**

      kubectl -n opsmx-rollouts apply -f https://raw.githubusercontent.com/OpsMx/isd-ap-quick-install/main/isd-rollouts/isd-rollouts-quick.yaml

   WAIT for about 10-15 min, depending on network speed.
 
   It is normal for some pods to go into error/crashloop before stabilising.

 - **Check the status of the pods by executing this command**

       kubectl -n opsmx-rollouts get po

     Once all pods show "Running" or "Completed" status, execute below command
       
       kubectl -n opsmx-rollouts port-forward svc/oes-ui 8080 & kubectl -n opsmx-rollouts port-forward svc/isd-argo-rollouts-dashboard 3100
      

 - **Access the ISD UI**
      
     Login using browser with http://localhost:8080
     
     - username **admin**

     Password can be retrieve the by using the below command
     
       kubectl -n opsmx-rollouts get secret -n opsmx-rollouts openldap -o jsonpath='{.data.LDAP_ADMIN_PASSWORD}'| base64 -d
       
      
