# devseccops-stack


# Commands to make chart

helm dependency build devseccops-stack/


helm package devseccops-stack/
helm repo index . --url https://manpreetsinghdevseccops.github.io/devseccops-stack


git add .
git commit -m"changes in devsecops-stack package"
git push origin gh-pages

helm uninstall devseccops -n devseccops   

helm repo add devseccops https://manpreetsinghdevseccops.github.io/devseccops-stack/

helm repo update
helm upgrade --install devseccops devseccops/devseccops-stack -n devseccops 


 helm upgrade --install devseccops devseccops/devseccops-stack -n devseccops --create-namespace


<!-- helm install devseccops-stack ./devseccops-stack-*.tgz -n devseccops -->

helm install devseccops ./devseccops-stack/ -n devseccops


terraform apply \
    -var="aws_account_id=111122223333" \
    -var="region=us-east-1" \
    -var="cluster_name=client-eks-cluster" \
    -var="prefix=clienta" \
    -var="namespace=clienta-devseccops-namespace"




 bash <(curl -fsSL https://devseccops-assets.s3.ap-south-1.amazonaws.com/setup-iam.sh) --cluster prod-devseccops-eks-cluster --prefix prod --namespace devseccops --region ap-south-1




  aws s3 cp /Users/manpreetsingh/Documents/devseccops/devseccops-service-configs/terraform/iam/setup-ssm.sh s3://devseccops-assets/setup-ssm.sh