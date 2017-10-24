# concourse-continuous-delivery

gcloud container clusters create concourse --image-type ubuntu --machine-type n1-standard-2

## Install Concourse
### Install Helm


### Install Concourse Chart
helm install stable/concourse --set concourse.baggageclaimDriver=overlay

## Create pipeline
export CLUSTER_CA=$(kubectl get secret default-token-6fh97 -o jsonpath='{.data.ca\.crt}')
export TOKEN=$(kubectl get secret default-token-6fh97 -o jsonpath='{.data.token}' | base64 --decode)

cat > secrets.yaml <<EOF
cluster_ca: $CLUSTER_CA
token: $TOKEN
EOF

fly -t local set-pipeline -p chart-deploy -c pipeline.yaml -l secrets.yaml