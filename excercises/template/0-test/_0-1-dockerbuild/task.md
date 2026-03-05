# Task: Your own superfancy code
## How this works
 - Update code by pushing it to main. Yes - push directly to main. 
 - Directories with `_` are ignored


## 0: Log in to places
**In browser:**
 - ArgoCD: https://argocd.course.variant.dev 
 - Grafana: https://grafana.course.variant.dev
 - Container registry: [link](https://portal.azure.com/#@variant.no/resource/subscriptions/b7ef0cfa-36d4-4ba9-9063-f5868bf1273e/resourceGroups/rg-platform-lab-northeurope/providers/Microsoft.ContainerRegistry/registries/variantcourselabsacr/overview)

Passwords etc are shared on slack

Kubectl:
 1. Use the azure cli to login to the correct subscription: `az login` and choose "Kompetanseheving"
 2. Run `az aks get-credentials --resource-group rg-platform-lab-northeurope --name aks-platform-lab-northeurope`
 3. Test with `kubectl get po -n template` to check if kubectl is running 
 4. Optional: Open k9s (`brew install k9s`) with your namespace: `k9s -n yournamespace`
    - Note: Your namespace is created after the first time you `git push` your excercises-folder


## 1: Choose a domain
Go to `deployment.yml`, and see the ingress-section. Update the hostname to something you like, and ideally unique. 


## 2: Run it
Remove the leading underscore in the folder name to have ArgoCD pick up the folder and auto-deploy it. 

## 3: Update it: 
By doing nothing at all, GitHub actions is now building "your" code and making a PR to update the image in your deployment to a new image. Merge that PR if you like. 

## 4: Ports! 
The newly built dockerfile exposes port 8080 and not just 80. Fix that either by updating the dockerfile, or by changing `containerPort` in the deployment and adding `targetPort` in the service. 

## 5: Environemnt variables 
Add the environemnt-variable `FAV_LUNCH` to your deployment

## 6: Free practise 
It's 16:41 the day before Variantdag - and my kids at home must be starving by now :o 

Play around with these deployments however you like. Some ideas: 
 - Use secrets to connect to a database 
 - Try to fail fast on missing config 
 - Scale up and down 
 - Try to run a shell in the cluster. See if DNS is different 