# learnkubernetes

## Project
- zodiac-app

Sample application to create a docker container.
This app return your sun sign based on the month and day passed in the URL. See Uage below.

### Usage 

http://localhost:8080/zodiac/{month}/{day}

http://localhost:8080/zodiac/06/01 should return Gemini

- K8s

Kubernetes configuration

1. POD

To create a POD, Run this command -> kubectl apply -f zodiac-app-pod.yml

To see the pod status, Run this command -> kubectl get pods -o wide


2. Service

2.1. Imperative Way

Run this command -> kubectl expose pod zodiac-pod --name=zodiac-svc-i --target-port=8080 --type=NodePort

To see the service status Run this command -> kubectl get svc
 
Note the IP and port and run the below command to access your zodiac application

curl http://localhost:32128/zodiac/06/01

2.2. Declarative Way

Run this command -> kubectl apply -f zodiac-app-service.yml

To see the service status Run this command -> kubectl get svc

Note the IP and port and run the below command to access your zodiac application

curl http://localhost:31111/zodiac/07/02

3. Deployments

To create a deployment, Run this command -> kubectl apply -f zodiac-app-deployment.yml

To see output, Run this command -> kubectl get deployments

optionally you can also run -> kubectl get all
This command will show everything pod, service, deployment, replica sets etc.

# Local Kubernetes Dashboard

Follow this link -> https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/

Always run this command to access dashboard -> kubectl proxy

Get the token using this command -> kubectl -n kubernetes-dashboard create token admin-user

Login url -> http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/


kubectl -n kubernetes-dashboard create token admin-user