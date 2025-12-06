# FitSync CD - Continuous Deployment

This repository contains GitHub Actions workflows for deploying and managing the FitSync K3s cluster on AWS.

## Current Workflows

### Test AWS Connectivity
- **File**: `.github/workflows/test-connectivity.yml`
- **Purpose**: Verify GitHub Actions can connect to AWS and access FitSync EC2 instances via SSM
- **Triggers**: Manual dispatch or push to main branch

## AWS Resources Accessed

The GitHub Actions workflows have access to:
- **EC2 Instances**: List and describe FitSync-tagged instances
- **SSM**: Send commands and manage sessions on EC2 instances
- **Load Balancers**: Check K3s API NLB status
- **Region**: us-east-2

## Authentication

Uses OIDC (OpenID Connect) with AWS IAM role:
- **Role**: `fitsync-prod-hub-github-actions-role`
- **Secret**: `AWS_ROLE_ARN` (automatically managed by Terraform)
- **Permissions**: EC2 describe, SSM commands, ELB describe

## Next Steps

Future workflows will handle:
1. K3s master setup and configuration
2. K3s worker node joining
3. Cilium CNI installation
4. Istio service mesh deployment
5. FitSync application deployment
