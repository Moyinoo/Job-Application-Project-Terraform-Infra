<!-- BEGIN_TF_DOCS -->
# Project overview

This project is intended for demostrating practical application of knowledge in the field of cloud technology and DevOps, as well as the deployment of web applications with the best practices. The stack is designed to cover a number of technologies and simultaneously carry the functional and meaningful load on each. This project applies a declarative approach to infrastructure building and shows the deployment automation process for the entire stack. All components of the project and their relationships are considered in detail to see how the application and its operation services work in the actual cloud on a concrete example.

# Tools Utilized

1. Terraform cli 
2. AWS account (where everything will be deployed)
3. Domain (e.g. "moyinopoola.com")
4. Terraform Cloud (https://app.terraform.io/session)
5. Github 
6. ArgoCD
7. Datadog

# Infrastructure deployment

The Infrastucture is a Hybrid setup with the cloud infrastructure deployed on AWS and an onsite environment exposed to the cloud through aws Storage Gateway. The infrastructure is deployed by trigarring a run on terafform cloud which is connected to this github repo. 
NOTE!! to reduce cost, some resources shown in the architecture diagram were not deployed (e.g. Storage Gateway), since there's no onsite available to deploy an agent. 

# Infrastucture Architecture
![Screenshot](img/CloudArchitecture.png)

# Application deployment

After deploying infrastructure we moving to application section desribed in application repository - https://github.com/moyinoo/Job-App-Project-ci.



## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](https://developer.hashicorp.com/terraform/install) | >= 1.4.2 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_aws"></a> [aws](https://registry.terraform.io/providers/hashicorp/aws/latest/docs) | 5.35.0 |
| <a name="provider_helm"></a> [helm](https://registry.terraform.io/providers/hashicorp/helm/latest/docs) | 2.12.1 |
| <a name="provider_kubernetes"></a> [kubernetes](https://registry.terraform.io/providers/hashicorp/kubernetes/latest/docs) | 2.25.2 |
| <a name="provider_random"></a> [random](https://registry.terraform.io/providers/hashicorp/random/latest/docs) | 3.6.0 |
| <a name="provider_cloudinit"></a> [cloudinit](https://registry.terraform.io/providers/hashicorp/cloudinit/latest/docs) | 2.3.3 |
| <a name="provider_null"></a> [null](https://registry.terraform.io/providers/hashicorp/null/latest/docs) | 3.2.2 |
| <a name="provider_time"></a> [time](https://registry.terraform.io/providers/hashicorp/time/latest/docs) | 0.10.0 |
| <a name="provider_tls"></a> [tls](https://registry.terraform.io/providers/hashicorp/tls/latest/docs) | 4.0.5 |

## Modules

| Name | Source | Version |
|------|--------|---------|
| <a name="module_vpc"></a> [vpc](https://registry.terraform.io/modules/terraform-aws-modules/vpc/aws/latest) | terraform-aws-modules/vpc/aws | 5.5.1 |
| <a name="module_dynamodb"></a> [dynamodb](https://registry.terraform.io/modules/terraform-aws-modules/dynamodb-table/aws/latest) | terraform-aws-modules/dynamodb-table/aws | 4.0.0 |
| <a name="module_ecr"></a> [ecr](https://registry.terraform.io/modules/cloudposse/ecr/aws/latest) | cloudposse/ecr/aws | 0.40.0 |
| <a name="module_eks"></a> [eks](https://registry.terraform.io/modules/terraform-aws-modules/eks/aws/latest) | terraform-aws-modules/eks/aws | 20.2.1 |
| <a name="module_iam_assumable_role_for_lambda_execution"></a> [iam\_assumable\_role\_for\_lambda\_execution](https://registry.terraform.io/modules/terraform-aws-modules/iam/aws/latest/submodules/iam-assumable-role) | terraform-aws-modules/iam/aws//modules/iam-assumable-role | 5.33.1 |
| <a name="module_iam_policy_for_lambda_execution"></a> [iam\_policy\_for\_lambda\_execution](https://registry.terraform.io/modules/terraform-aws-modules/iam/aws/latest) | terraform-aws-modules/iam/aws//modules/iam-policy | ~> 5.33.1 |
| <a name="module_rds"></a> [rds](https://registry.terraform.io/modules/cloudposse/rds-cluster/aws/latest) | cloudposse/rds-cluster/aws | 1.7.0 |
| <a name="module_s3_bucket_for_output_files"></a> [s3\_bucket\_for\_output\_files](https://registry.terraform.io/modules/terraform-aws-modules/s3-bucket/aws/latest) | terraform-aws-modules/s3-bucket/aws | 4.1.0 |
| <a name="module_sqs"></a> [sqs](https://registry.terraform.io/modules/terraform-aws-modules/sqs/aws/latest) | terraform-aws-modules/sqs/aws | 4.1.0 |

## Resources

| Name | Type |
|------|------|
| [aws_caller_identity.current](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/caller_identity) | data source |
| [aws_key_pair.devops](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/key_pair) | resource |
| [aws_eks_cluster.cluster](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/eks_cluster) | data source |
| [aws_eks_cluster_auth.cluster](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/eks_cluster_auth) | data source |
| [aws_availability_zones.available](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/availability_zones) | data source |
| [random_password.rds_db_name](https://registry.terraform.io/providers/hashicorp/random/latest/docs/resources/password) | resource |
| [random_password.rds_password](https://registry.terraform.io/providers/hashicorp/random/latest/docs/resources/password) | resource |
| [random_password.rds_admin_username](https://registry.terraform.io/providers/hashicorp/random/latest/docs/resources/password) | resource |
| [aws_ssm_parameter.save_rds_db_name_to_ssm](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/ssm_parameter) | resource |
| [aws_ssm_parameter.save_rds_endpoint_to_ssm](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/ssm_parameter) | resource |
| [aws_ssm_parameter.save_rds_password_to_ssm](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/ssm_parameter) | resource |
| [aws_ssm_parameter.save_rds_admin_username_to_ssm](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/ssm_parameter) | resource |
| [aws_ssm_parameter.save_dynamodb_table_name_to_ssm](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/ssm_parameter) | resource |
| [aws_ssm_parameter.save_name_of_s3_for_output_files_to_ssm](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/ssm_parameter) | resource |
| [aws_ssm_parameter.save_lambda_iam_role_arn_to_ssm](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/ssm_parameter) | resource |
| [aws_ssm_parameter.sqs_arn](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/ssm_parameter) | resource |
| [aws_ssm_parameter.sqs_name](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/ssm_parameter) | resource |
| [aws_ssm_parameter.sqs_url_path](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/ssm_parameter) | resource |
| [aws_cloudformation_stack.DatadogIntegration](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/cloudformation_stack) | resource |
| [helm_release.ack-lambda](https://registry.terraform.io/providers/hashicorp/helm/latest/docs/resources/release) | resource |
| [helm_release.crd-helm-chart](https://registry.terraform.io/providers/hashicorp/helm/latest/docs/resources/release) | resource |
| [helm_release.cert-manager](https://registry.terraform.io/providers/hashicorp/helm/latest/docs/resources/release) | resource |
| [helm_release.actions-runner-controller](https://registry.terraform.io/providers/hashicorp/helm/latest/docs/resources/release) | resource |
| [helm_release.ingress-nginx](https://registry.terraform.io/providers/hashicorp/helm/latest/docs/resources/release) | resource |
| [helm_release.argocd](https://registry.terraform.io/providers/hashicorp/helm/latest/docs/resources/release) | resource |
| [helm_release.argocd-apps](https://registry.terraform.io/providers/hashicorp/helm/latest/docs/resources/release) | resource |
| [helm_release.datadog](https://registry.terraform.io/providers/hashicorp/helm/latest/docs/resources/release) | resource |
| [kubernetes_service.ingress_gateway](https://registry.terraform.io/providers/hashicorp/kubernetes/latest/docs/data-sources/service) | data source |
| [aws_route53_record.eks_domain](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/route53_record) | resource |
| [aws_route53_record.eks_domain_cert_validation_dns](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/route53_record) | resource |
| [aws_acm_certificate.eks_domain_cert](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/acm_certificate) | resource |
| [aws_acm_certificate_validation.eks_domain_cert_validation](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/acm_certificate_validation) | resource |
| [aws_lb.ingress](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/lb) | data source |
| [aws_route53_record.bastion_host_record](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/route53_record) | resource |
| [aws_route53_zone.base_domain](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/route53_zone) | data source |
| [kubernetes_namespace.application](https://registry.terraform.io/providers/hashicorp/kubernetes/latest/docs/resources/namespace) | resource |
| [kubernetes_secret.demo-repo](https://registry.terraform.io/providers/hashicorp/kubernetes/latest/docs/resources/secret) | resource |
| [aws_eip.bastion_host](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/eip) | resource |
| [aws_security_group.bastion_host](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/security_group) | resource |
| [aws_instance.bastion_host](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/instance) | resource |
| [aws_ami.latest-ubuntu](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/ami) | data source |


