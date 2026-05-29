# devseccops-stack


# Commands to make chart

helm dependency build devseccops-stack/


helm package devseccops-stack/
helm repo index . --url https://manpreetsinghdevseccops.github.io/devseccops-stack

rm -rf ./devseccops-stack/helm 
rm -rf ./devseccops-stack/cloud-formation 


git add .
git commit -m"changes in devsecops-stack package"
git push origin gh-pages

#helm uninstall devseccops -n devseccops   

helm repo add devseccops https://manpreetsinghdevseccops.github.io/devseccops-stack/
helm repo update

helm upgrade --install devseccops devseccops/devseccops-stack -n devseccops 



helm upgrade --install devseccops devseccops/devseccops-stack \
    -n devseccops \
    --set global.domain.frontend="demo.devseccops.ai" \
    --set global.domain.backend="demo-api.devseccops.ai" \
    --set global.certificateArn="arn:aws:acm:ap-south-1:130705418859:certificate/29231324-d2ff-4880-b554-6c0478a839f2" \
    --set global.albGroupName="shared-prod-alb" \
    --create-namespace


helm upgrade --install devseccops devseccops/devseccops-stack -n devseccops --create-namespace


<!-- helm install devseccops-stack ./devseccops-stack-*.tgz -n devseccops -->

helm install devseccops ./devseccops-stack/ -n devseccops






aws s3 cp /Users/manpreetsingh/Documents/devseccops/devseccops-service-configs/cloud-formation/setup-ssm.sh s3://devseccops-assets/setup-ssm.sh
aws s3 cp /Users/manpreetsingh/Documents/devseccops/devseccops-service-configs/cloud-formation/setup-iam.sh s3://devseccops-assets/setup-iam.sh
