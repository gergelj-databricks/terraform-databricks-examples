AWS Databricks Unity Catalog - Stage 2
=========================

In this template, we show how to dpeloy Unity Catalog related resources such as unity metastores, account level users and groups.

This is stage 2 of UC deployment, you can also run this stage 2 template directly without stage 1 (which helps you create `account admin` identity), but you need to make sure using account admin identity to authenticate the `databricks mws` provider, instead of using `account owner`. One major reason of not using `account owner` in terraform is you cannot destroy yourself from admin list.

If you don't have an `account admin` identity, you can refer to stage 1: 
[aws-databricks-unity-catalog-bootstrap](https://github.com/databricks/terraform-databricks-examples/tree/main/examples/aws-databricks-uc-bootstrap)

![alt text](https://raw.githubusercontent.com/databricks/terraform-databricks-examples/main/examples/aws-databricks-uc/images/uc-tf-onboarding.png?raw=true)

When running tf configs for UC resources, due to sometimes requires a few minutes to be ready and you may encounter errors along the way, so you can either wait for the UI to be updated before you apply and patch the next changes; or specifically add depends_on to accoune level resources

## Get Started

> Step 1: Fill in values in `terraform.tfvars`; also configure env necessary variables for AWS and Databricks provider authentication. Such as:


```bash
export TF_VAR_databricks_account_client_id=your_account_level_spn_application_id
export TF_VAR_databricks_account_client_secret=your_account_level_spn_secret
export TF_VAR_databricks_account_id=your_databricks_account_id

export AWS_ACCESS_KEY_ID=your_aws_role_access_key_id
export AWS_SECRET_ACCESS_KEY=your_aws_role_secret_access_key
``` 

> Step 2: Run `terraform init` and `terraform apply` to deploy the resources. This will deploy both AWS resources that Unity Catalog requires and Databricks Account Level resources.
