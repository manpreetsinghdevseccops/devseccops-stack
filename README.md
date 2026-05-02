# devseccops-stack


# Commands to make chart

helm package devseccops-stack/
helm repo index . --url https://manpreetsinghdevseccops.github.io/devseccops-stack


git add .
git commit -m"changes in devsecops-stack package"
git push origin gh-pages

helm uninstall devseccops -n devseccops   

helm repo add devseccops https://manpreetsinghdevseccops.github.io/devseccops-stack/

helm repo update
helm upgrade --install devseccops devseccops/devseccops-stack -n devseccops