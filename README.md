# isd-ap-quick-install
Quick install for ISD Services only for Argo


To experience ISD quickly, you can install it and deploy your applications. Note that the instructions below are intended to get you started quickly and try out ISD functionality. This is not suitable for production or any environment where security is a concern.
To begin installation, you'll need a Kubernetes cluster  (with 2 nodes with 32GB RAM each) and kubectl set-up.

Issue the following commands (copy paste in a terminal window)

- **Create opsmx11 secret:**

   Below Secret need to be created Please updated the password and create a secret

      kubectl create secret docker-registry opsmx11-secret --docker-server=docker.io --docker-username=opsmx11 --docker-password=xxxxx --docker-email=saiteja.katabhatina@opmx.io

- kubectl -n opsmx-autopilot apply -f https://raw.githubusercontent.com/OpsMx/isd-quick-install/main/isd312/isd-gitea-quick.yaml

WAIT for about 20-30 min, depending your network speed.
It is normal for some pods to go into error/crashloop before stabilising.

Check the status of the pods by executing this command:
- kubectl -n opsmx-autopilot get po

Once all pods show "Running" or "Completed" status, wait for a couple of minutes and execute this:
- kubectl -n opsmx-autopilot  port-forward svc/oea-ui 8080  ## Keep running, it shows messages such as "Forwarding from 127.0.0.1:8080 -> 8080"

Wait for about 5 min. The halyard pod might restart during this period.

Now, open your browser and navigate to http://localhost:8080
Login with username admin and password opsmxadmin123

