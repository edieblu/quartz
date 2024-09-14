---
tags:
  - ✅
published: true
sr-due: 2025-11-28
sr-interval: 514
sr-ease: 250
---

⬅️ [[FEM Aws for FE]]
 
- `aws configure`
- If you have more than one AWS account, you can create additional profiles in `.aws/credentials`.
```
[default]
aws_access_key_id=[KEY]
aws_secret_access_key=[SECRET_KEY]

[sideproject]
aws_access_key_id=[KEY]
aws_secret_access_key=[SECRET_KEY]
```

List the contents of a bucket:
`aws s3 ls s3://superawesome.xyz`

Copy our built website to the S3 bucket
`aws s3 cp dist/ s3://mysuperfunwebsite.com/ --recursive`