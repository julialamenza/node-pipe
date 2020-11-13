Create environment and deployment pipelines using ECS, ECR, CodePipeline and Git with Terraform

## Architecture 

![Arch](.github/images/ECS-Arquitetura.png)

## Deploy Pipeline

![Steps](.github/images/pipeline-demo.png)

# How to Deploy

## Edit your preferences

Edit `variables.tf` file to customize application preferences like Github account, repo and owner, Load Balancer ports and cluster preferences. 

```hcl
# Customize the Cluster Name
variable "cluster_name" {
  description = "ECS Cluster Name"
  default     = ""
}

# Customize your ECR Registry Name
variable "app_repository_name" {
  description = "ECR Repository Name"
  default     = ""
}

###### APPLICATION OPTIONS  ######
variable "container_name" {
  description = "Container app name"
  default     = ""
}
```

Edit the Github preferences in the same file to specify infos like repo, owner or organization, branches e etc. 

```hcl
# Github Repository Owner
variable "git_repository_owner" {
  description = "Github Repository Owner"
  default     = ""
}

# Github Repository Project Name
variable "git_repository_name" {
  description = "Project name on Github"
  default     = ""
}

# Default Branch
variable "git_repository_branch" {
  description = "Github Project Branch"
  default     = ""
}
```

## Edit Auto Scaling Metrics

```hcl
# Number of containers
variable "desired_tasks" {
  description = "Number of containers desired to run app task"
  default     = 2
}

variable "min_tasks" {
  description = "Minimum"
  default     = 2
}

variable "max_tasks" {
  description = "Maximum"
  default     = 4
}

variable "cpu_to_scale_up" {
  description = "CPU % to Scale Up the number of containers"
  default     = 80
}

variable "cpu_to_scale_down" {
  description = "CPU % to Scale Down the number of containers"
  default     = 30
}
```


## How to Deploy

### 1) Github Access Token

* Export Github Token as an environment variable. 

```bash
export GITHUB_TOKEN=YOUR_TOKEN
``` 
* Export AWS Credencials. 

```bash
export AWS_SECRET_ACCESS_KEY=
``` 
```bash
export AWS_ACCESS_KEY_ID
``` 

### 2) Terraform 

* Initialize Terraform 

```bash
terraform init
```

* Plan our modifications

```bash
terraform plan
```

* Apply the changes on AWS

```bash
terraform apply
```



