
On docker_push.sh

eval $(aws ecr get-login --no-include-email --region YOUR-AWS-REGION)


On ecs_deploy.sh


docker-deploy/ecs.sh -c $LIVE_CLUSTER_NAME -n $LIVE_SERVICE -i "$AWS_URL/$LIVE_APP_NAME:latest" -r YOUR-AWS-REGION -t 240


On .travis.yml

- LIVE_SERVICE=YOUR-ECS-SERVICE-NAME
- LIVE_CLUSTER_NAME=YOUR-ECS-CLUSTER-NAME
- LIVE_APP_NAME=YOUR-ECR-API-NAME
- AWS_URL=YOUR-AWS-ACCOUNT-ID.dkr.ecr.YOUR-AWS-REGION.amazonaws.com



