aws s3 cp /Users/manpreetsingh/Documents/devseccops/devseccops-service-configs/cloud-formation/setup-ssm.sh s3://devseccops-assets/setup-ssm.sh

aws s3 cp /Users/manpreetsingh/Documents/devseccops/devseccops-service-configs/cloud-formation/setup-iam.sh s3://devseccops-assets/setup-iam.sh

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