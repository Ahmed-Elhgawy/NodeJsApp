# NodeJS application
This repo is used to build application on kubernetes cluster using Jenkins pipeline \
Plugin needed to installed:
>[Slack Notification](https://plugins.jenkins.io/slack/)

Credential needed:
1. Docker
2. Slack

## Pipeline Stages:
1. login to docker repo
2. buid docker image
3. push docker image to repo
4. deploy application on cluster

## Build EKS Cluster and deploy jenkins in same cluster 👇👇

### [Deploying Appliction on EKS cluster using jenkins pipeline](https://github.com/Ahmed-Elhgawy/aws-k8s-jenkins.git)