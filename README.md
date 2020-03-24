# BSMN ndasynapse-manifests AWS Infrastructure

## Overview

Infrastructure for the [NDA Synapse manifest reporting](https://github.com/bsmn/ndasynapse-manifests) application.

It uses a Docker image from [bsmn/ndasynapse-manifests](https://github.com/bsmn/ndasynapse-manifests).

## Purpose

This repository contains CloudFormation infrastructure templates for the processes required by the application:

1. Query the NDA API for live data (<https://github.com/bsmn/ndasynapse-manifests/blob/master/bin/run-live-manifests.sh>)
1. Query the NDA API for historical data (<https://github.com/bsmn/ndasynapse-manifests/blob/master/bin/run-original-manifests.sh>)

These tasks are run once per day using an AWS CloudWatch Event Rule that submits an AWS Batch array job.

To look at errors, login to sandbox and use this [link](https://signin.aws.amazon.com/switchrole?roleName=cloudwatch-cross-account-CWCrossAccountSharingRol-7CATGO45E4K6&account=org-sagebase-scicomp) to switch roles and look at CloudWatch Logs.

## Continuous Integration

We have configured Travis to deploy CF template updates.  Travis deploys using
[sceptre](https://sceptre.cloudreach.com/latest/about.html)
