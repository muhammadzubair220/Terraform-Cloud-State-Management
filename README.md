# 🔨 Terraform Cloud State Management

A Terraform project demonstrating infrastructure management on AWS using Terraform Cloud for remote state management and GitHub Actions for CI/CD automation.

## 📋 Prerequisites

- [Terraform](https://www.terraform.io/downloads.html) >= 1.13.3
- [AWS CLI](https://aws.amazon.com/cli/) configured
- [Terraform Cloud](https://app.terraform.io/) account
- GitHub repository with Actions enabled

## 🚀 Setup

### 1. Terraform Cloud Configuration

1. Create a workspace in Terraform Cloud
2. Configure environment variables:
   - `AWS_ACCESS_KEY_ID`
   - `AWS_SECRET_ACCESS_KEY`
   - `AWS_DEFAULT_REGION`

### 2. GitHub Secrets

Add these secrets to your GitHub repository:

```
TF_API_TOKEN          # Terraform Cloud API token
TF_WORKSPACE          # Terraform Cloud workspace name
TF_CLOUD_ORGANIZATION # Terraform Cloud organization name
```

### 3. Local Development

```bash
# Clone repository
git clone <repository-url>
cd Terraform-Cloud-State-Management

# Initialize Terraform
terraform init

# Validate configuration
terraform validate

# Format code
terraform fmt
```

## 🎯 Usage

### GitHub Actions Workflow

The project includes an automated workflow that supports three actions:

- **Plan**: Review infrastructure changes
- **Apply**: Deploy infrastructure changes
- **Destroy**: Remove infrastructure

#### Running the Workflow

1. Go to **Actions** tab in GitHub
2. Select **Infrastructure Configuring using Terraform on AWS**
3. Click **Run workflow**
4. Choose your desired action (plan/apply/destroy)
5. Click **Run workflow**

### Local Commands

```bash
# Plan changes
terraform plan

# Apply changes
terraform apply

# Destroy infrastructure
terraform destroy
```

## 📁 Project Structure

```
.
├── .github/
│   └── workflows/
│       └── terraform.yml    # GitHub Actions workflow
├── main.tf                  # Main Terraform configuration
├── variables.tf             # Input variables
├── outputs.tf              # Output values
├── versions.tf             # Provider versions
└── README.md               # This file
```

## 🔧 Configuration

### Terraform Cloud Backend

The project uses Terraform Cloud for remote state management:

```hcl
terraform {
  cloud {
    organization = "your-org-name"
    workspaces {
      name = "your-workspace-name"
    }
  }
}
```

### AWS Provider

```hcl
provider "aws" {
  region = var.aws_region
}
```

## 🛡️ Security

- All sensitive data stored as GitHub secrets
- Terraform state managed remotely in Terraform Cloud
- AWS credentials configured as environment variables
- Production environment protection enabled

## 🔄 Workflow Features

- **Automated validation**: Format check and validation
- **Error handling**: Fail-fast on any errors
- **Caching**: Terraform plugins cached for faster runs
- **Plan output**: Readable plan display
- **Environment protection**: Production environment gates

## 📝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Run `terraform fmt` and `terraform validate`
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License.

## 🆘 Troubleshooting

### Common Issues

- **Authentication errors**: Verify AWS credentials and Terraform Cloud token
- **State lock errors**: Check Terraform Cloud workspace status
- **Permission errors**: Ensure proper IAM permissions for AWS resources

### Getting Help

- Check [Terraform Cloud documentation](https://www.terraform.io/cloud-docs)
- Review [AWS Provider documentation](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)
- Open an issue in this repository