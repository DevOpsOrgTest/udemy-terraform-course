
## Demo 1

Spinning up instance with the AWS account and secret id.

##### Create resource EC2


```resource "aws_instance" "example" {
  ami           = "${lookup(var.AMIS, var.AWS_REGION)}"
  instance_type = "t2.micro"
}```

