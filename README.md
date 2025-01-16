# javaappk8s-helm-argocddeploment



#FOR helm just create a helm repo in instance

helm create benzcarsite

#inside of this benzcarsite there is values.yaml edit the imagepath and service port and conatianer port
#add nexus-secret.yaml inside the benzcarsite 


#this below command will give u base64 nexus username and passwrd authentication token add that token in nexus-secret.yaml file 

 token    "eyJhdXRocyI6eyIxMy4yMzIuNjYuNzM6NTAwMCI6eyJ1c2VybmFtZSI6ImFkbWluIiwicGFzc3dvcmQiOiJhZG1pbiIsImF1dGgiOiJZV1J0YVc0NllXUnRhVzQ9In19fQo="

   
#echo '{"auths":{"13.232.66.73:5000":{"username":"admin","password":"admin","auth":"'"$(echo -n 'admin:admin' | base64 -w 0)"'"}}}' > config.json
#cat config.json


#like this 

apiVersion: v1
kind: Secret
metadata:
  name: nexus-secret
  namespace: argocd
type: kubernetes.io/dockerconfigjson
data:
  .dockerconfigjson: eyJhdXRocyI6eyIxMy4yMzIuNjYuNzM6NTAwMCI6eyJ1c2VybmFtZSI6ImFkbWluIiwicGFzc3dvcmQiOiJhZG1pbiIsImF1dGgiOiJZV1J0YVc0NllXUnRhVzQ9In19fQo=



#do apply this secret speratly

kubectl apply -f nexus-secret.yaml -m argocd

#check if its deployed

kubectl get secret -n argocd
  


#if argocd installed then this github path we need to add in argocd website /create a application in argocd url / then this will pick auto to deploy into k8s environment.



 kubectl exec -it germancar-benzcarsite-6b8c744f86-6qd2j /bin/bash -n argocd






