

# Kaniko Lab

Created for the following videos in [The DevOps Lab Series YouTube channel]():

* [Kaniko - Building Container Images In Kubernetes Without Docker](https://youtu.be/EgwVQN6GNJg)


##########
# Kaniko #
##########

open https://github.com/lakshmojirao999/kaniko-lab

# Fork it

# Replace `[...]` with the GitHub organization or the username
export GH_ORG=[...]

git clone https://github.com/$GH_ORG/kaniko-lab.git

cd kaniko-lab

ls -1

cat Dockerfile

docker image build \
    --tag devops-lab \
    .

minikube start

cat docker.yaml

kubectl apply \
    --filename docker.yaml

kubectl wait \
    --for condition=containersready \
    pod docker

kubectl exec -it docker -- sh

apk add -U git

git clone https://github.com/lakshmojirao999/kaniko-lab.git

cd kaniko-lab

docker image build \
    --tag devops-lab \
    .

exit

kubectl delete --filename docker.yaml

cat docker-socket.yaml

kubectl apply \
    --filename docker-socket.yaml
    
kubectl wait \
    --for condition=containersready \
    pod docker

kubectl exec -it docker -- sh

apk add -U git

git clone https://github.com/lakshmojirao999/kaniko-lab.git

cd kaniko-lab

docker image build \
    --tag devops-lab \
    .

exit

kubectl delete \
    --filename docker-socket.yaml

cat kaniko-git.yaml

# Open kaniko-git.yaml
# Replace `lakshmojirao999` in `--context` and `--destination` with GitHub and Docker Hub users
# Save

git add .

git commit -m "Changed the registry"

git push

export REGISTRY_SERVER=https://index.docker.io/v1/

# Replace `[...]` with the registry username
export REGISTRY_USER=[...]

# Replace `[...]` with the registry password
export REGISTRY_PASS=[...]

# Replace `[...]` with the registry email
export REGISTRY_EMAIL=[...]

kubectl create secret \
    docker-registry regcred \
    --docker-server=$REGISTRY_SERVER \
    --docker-username=$REGISTRY_USER \
    --docker-password=$REGISTRY_PASS \
    --docker-email=$REGISTRY_EMAIL

kubectl apply \
    --filename kaniko-git.yaml
    
kubectl wait \
    --for condition=containersready \
    pod kaniko

kubectl logs kaniko --follow

# Open it in browser

cat kaniko-dir.yaml

