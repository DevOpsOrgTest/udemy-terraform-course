
## Demo 1

Spinning up instance with the AWS account and secret id.

##### Create instance.tf file with below content

` resource "aws_instance" "example" {
  ami           = "${lookup(var.AMIS, var.AWS_REGION)}"
  instance_type = "t2.micro"
} `

##### Create provider.tf file with below content

`provider "aws" {
    access_key = "${var.AWS_ACCESS_KEY}"
    secret_key = "${var.AWS_SECRET_KEY}"
    region = "${var.AWS_REGION}"
}
`
