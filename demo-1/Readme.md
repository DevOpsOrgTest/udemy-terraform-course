
## Demo 1

Spinning up instance with the AWS account and secret id.

##### Create `vars.tf` file with below content

```terraform
variable "AWS_ACCESS_KEY" {}
variable "AWS_SECRET_KEY" {}
variable "AWS_REGION" {
  default = "eu-west-1"
}
variable "AMIS" {
  type = "map"
  default = {
    us-east-1 = "ami-13be557e"
    us-west-2 = "ami-06b94666"
    eu-west-1 = "ami-0d729a60"
  }
}
```

##### Create `instance.tf` file with below content

```terraform 
resource "aws_instance" "example" {
  ami           = "${lookup(var.AMIS, var.AWS_REGION)}"
  instance_type = "t2.micro"
}
```

##### Create `provider.tf` file with below content

```terraform
provider "aws" {
    access_key = "${var.AWS_ACCESS_KEY}"
    secret_key = "${var.AWS_SECRET_KEY}"
    region = "${var.AWS_REGION}"
}
```

Open the terminal from the above files location and execute below commands.

`terraform init`

`terraform plan`

`terraform apply`

