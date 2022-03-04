# Move resources with Configuration Driven Move

Learn how to move your existing resources to module with the `moved` configuration block.

Follow along with the [Learn Guide](https://learn.hashicorp.com/tutorials/terraform/move-config) at HashiCorp Learn.


This configuration contains a VPC module, a security group that allows ingress HTTP traffic on port 8080, and an EC2 instance that uses the security group. Later in this tutorial, these resources will be moved into separate modules to make the configuration more manageable.