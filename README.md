# Overview

This solution helps to get CA certificate from AWS PCA and create custom secret for Istio.

![image](simple-diaram.png)

## How to use it

1. Build [getmesh](./getmesh/Dockerfile) docker image and push to AWS ECR
2. Create [AWS OIDC IAM role](./pca-manager/README.md#oidc-role) with access to the AWS PCA
3. Set correct helm [values](./pca-manager/README.md#overview)
4. Deploy it to your k8s cluster

## Pay attention

- Istio secret name is [cacerts](https://github.com/tetratelabs/getmesh/blob/cb1aa915ddbf28e1e8a396dbc7570d950313af40/internal/cacerts/k8s/secret.go#L36)
- This `cacerts` secret should be created before installing Istio OR after creation simply restart all Istio pods.
