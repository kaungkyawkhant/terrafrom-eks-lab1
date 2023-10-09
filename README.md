# terrafrom-eks-lab1

##deploying AWS Elastic Kubernetes Service (EKS) k8s cluster using terraform, infrastructure as a code(IaaC).

1. Create [main.tf](http://main.tf) and [variables.tf](http://variables.tf) files using VS Code. 
2. Create AWS S3 bucket using aws cli command

```
aws s3 mb s3://mybucket1 —region=ap-southeast-2
```

3. issue the terraform commands to deploy all required resources in AWS cloud

```
terraform init

terraform plan
terraform apply
```

4. Download the kubeconfig file from aws using following command

```
aws eks update-kubeconfig —region ap-southeast-2 —name myekscluster
```  

5. verify the connection to eks cluster using ```kubectl get pod```
6. create new deployment using deployment.yml file

```
kubectl apply -f deployment.yml
```

7. create new loadbalancer to expose the web service to public internet

```
kubectl apply -f loadbalancer.yml
```

8. Copy the URL of loadbalancer and paste it to the Chrome with port number (or using curl)

```
curl http://[loadbalancerurl]:5000
```

9. Delete all the resources using the following commands

```
kubectl delete -f loadbalancer.yml

kubectl delete -f deployment.yml

terraform destory
```
