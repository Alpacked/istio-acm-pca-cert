# Overview

To use it, all you need to do is:
1. Install `image` with custom image [getmesh](../getmesh/Dockerfile)
2. Set arn `oidcRole` that have access to ACM PCA
3. Set `signingCAArn` arn AWS PCA


## OIDC Role

Here is example of the `Trust relationships` and `Permissions` that can help you

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "",
            "Effect": "Allow",
            "Principal": {
                "Federated": "arn:aws:iam::123456789012:oidc-provider/oidc.eks.us-east-1.amazonaws.com/id/D75405111A1111A06EA8222AF9123CA8"
            },
            "Action": "sts:AssumeRoleWithWebIdentity",
            "Condition": {
                "StringLike": {
                    "oidc.eks.us-east-1.amazonaws.com/id/D75405111A1111A06EA8222AF9123CA8:sub": "system:serviceaccount:istio-system:pca-manager
                }
            }
        }
    ]
}
``````

```
"acm-pca:DescribeCertificateAuthority",
"acm-pca:GetCertificate",
"acm-pca:IssueCertificate",
"acm-pca:GetCertificateAuthorityCertificate"
```