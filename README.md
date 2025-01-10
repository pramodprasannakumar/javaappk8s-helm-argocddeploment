# javaappk8s-helm-argocddeploment



#FOR helm just create a helm repo in instance

helm create benzcarsite

#inside of this benzcarsite there is values.yaml edit the imagepath and service port and conatianer port
#add nexus-secret.yaml inside the benzcarsite 


#if argocd installed then this github path we need to add in argocd website /create a application in argocd url / then this will pick auto to deploy into k8s environment.
