# K8s Rbac
1. create the service account sa under rbac namespace
	```
	 kubectl create -f sa-rbac.yaml
	```
2. create the clusterrole and clusterrolebindings for created service account.
	```
	 kubectl create -f cr-ns-only.yaml
	```
3. create the rolebinding with clusterrole and service account which you previously created above under namespace that you want to access.
	```
	 kubectl create -f rb-with-sa.yaml
	```
4. copy the token of service account and decrypt the token value with **base64** command.
	```
	 kubectl -n rbac get secret **sa** -oyaml
	```
	

	```
	 echo " **sa-base64-encrypt-token** " | base64 -d
	```


5. paste the above decrypt token in kubeconfig token value field.

@yannainglin

refurl:
https://learnk8s.io/rbac-kubernetes
https://kubernetes.io/docs/reference/access-authn-authz/rbac/
