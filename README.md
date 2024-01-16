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