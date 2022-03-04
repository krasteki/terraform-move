# Move resources with Configuration Driven Move

Learn how to move your existing resources to module with the `moved` configuration block.

Follow along with the [Learn Guide](https://learn.hashicorp.com/tutorials/terraform/move-config) at HashiCorp Learn.


This configuration contains a VPC module, a security group that allows ingress HTTP traffic on port 8080, and an EC2 instance that uses the security group. Later in this tutorial, these resources will be moved into separate modules to make the configuration more manageable.

I. Refactor the configuration

1. In your main.tf file, remove the AMI data source, the instance resource, and security group resource.

2. Create compute module
-Create a new modules directory with a compute subdirectory.
-Create a new `main.tf` file in the compute directory and add the following configuration.
-create a new outputs.tf file to capture your instance IP address. You will use this output to pass as a variable into another module.
This is a modified version of the initial Terraform configuration for the EC2 instance.

3. Create security group module
-create a new directory for your security_group module.
-Create a new main.tf file in the security_group directory and add the following configuration.
-Create a new outputs.tf file to capture your security group ID. You will pass this output value as an input variable into another module.

4. Update configuration with modules
Open the main.tf file and add the new module blocks to the end of your configuration.

II. Move your resources with the moved configuration block

In previous versions of Terraform, you had to refactor your existing infrastructure manually, by using terraform state mv to rename your resources in your project's state to match the changes to your configuration.

With the moved configuration block, you can inform Terraform about all resource address changes in your configuration. Terraform also validates those changes to provide you with clearer operational output and you can safely review plans before applying.


1. In the root main.tf file, add moved configuration blocks for each of the resources moved into modules in the previous step.

III. Rename and move a resource

1. Rename your vpc module, and update the references to it in the rest of your configuration.

2. Add the moved block for your VPC changes at the bottom of the file.