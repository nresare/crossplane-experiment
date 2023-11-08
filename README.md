# Crossplane experiment 

This repository contains some experimental stuff for setting up a bunch
of things in AWS using crossplane. A stretch goal is to quickly bring up
a tiny kubernetes cluster that is set up such that crossplane custom
resources can create a whole new AWS account with networking and then
in turn spin up a target kubernetes cluster in that new environment.

## Bootstrap

* Install awscli, eksctl and kubectl on your macbook with `brew install awscli eksctl`
* Obtain credentials for the command line tools from your AWS acount with `aws configure sso`
  I used the profile default, which I have some vaugue idea about it being the default
* Create a cluster. I used `eksctl create cluster --name cp0 --region eu-north-1 --fargate` 
  (This takes about 15 minutes)
* I had some trouble with the pregenerated kubectl config, so I ran `aws eks
  update-kubeconfig --region eu-north-1 --name cp0` after which I could interact with
  the cluster
* Remember to delete your cluster afterwards: `eksctl delete cluster cp0`
