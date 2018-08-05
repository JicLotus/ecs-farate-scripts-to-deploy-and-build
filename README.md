## First of all these files and configuration were based on:

https://dev.mikamai.com/2016/05/17/continuous-delivery-with-travis-and-ecs/

## How to install:

### On docker_push.sh change 'YOUR-AWS-REGION':

    eval $(aws ecr get-login --no-include-email --region YOUR-AWS-REGION)


### The same on ecs_deploy.sh:

    docker-deploy/ecs.sh -c $LIVE_CLUSTER_NAME -n $LIVE_SERVICE -i "$AWS_URL/$LIVE_APP_NAME:latest" -r YOUR-AWS-REGION -t 240

### On .travis.yml, put your aws configurations:

    - LIVE_SERVICE=YOUR-ECS-SERVICE-NAME
    - LIVE_CLUSTER_NAME=YOUR-ECS-CLUSTER-NAME
    - LIVE_APP_NAME=YOUR-ECR-API-NAME
    - AWS_URL=YOUR-AWS-ACCOUNT-ID.dkr.ecr.YOUR-AWS-REGION.amazonaws.com

### Put your AWS credentials on .travis file:

Install travis on your OS, then execute the followings commands where travis file (.travis.yml) was located:

    travis encrypt AWS_ACCESS_KEY_ID="HERE_PUT_YOUR_ACCESS_KEY_ID" --add
    travis encrypt AWS_SECRET_ACCESS_KEY="HERE_PUT_YOUR_SECRET_ACCESS_KEY" --add


