# tf-github
Terraform GitHub provider

# Introduction
The GitHub provider is used to interact with GitHub organization resources. See detailed desciption here : [GitHub Provider](https://www.terraform.io/docs/providers/github/index.html)

The provider allows you to manage your GitHub organization's members and teams easily. It needs to be configured with the proper credentials before it can be used. 

# Requirements
This repo assumes general knowledge about Terraform for AWS, if not, please get yourself accustomed first by going through [getting started guide](https://learn.hashicorp.com/terraform?track=getting-started#getting-started) . Please also have your AWS credentials prepared in some way, preferably environment variables. See in details here : [Section - Keeping Secrets](https://aws.amazon.com/blogs/apn/terraform-beyond-the-basics-with-aws/)

To learn more about the mentioned above tools and technologies -  please check section [Technologies near the end of the README](#technologies)

# How to use

1. 
2. You will need first to create Personal Access Token in GitHub, use this link `https://github.com/settings/tokens`, write it down, as you are going to see it only once!

# To do

- [ ] create demo code
- [ ] test code
- [ ] update readme

# Done
- [x] initial README
- [x] introduction section
- [x] prepare environment (create tokens and etc)

# Technologies

1. **To download the content of this repository** you will need **git command-line tools**(recommended) or **Git UI Client**. To install official command-line Git tools please [find here instructions](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) for various operating systems. 
2. **For managing infrastructure** we using Terraform - open-source infrastructure as a code software tool created by HashiCorp. It enables users to define and provision a data center infrastructure using a high-level configuration language known as Hashicorp Configuration Language, or optionally JSON. More you encouraged to [learn here](https://www.terraform.io). 
3. **This project for virtualization** relies on **AWS EC2** - Amazon Elastic Compute Cloud (Amazon EC2 for short) - a web service that provides secure, resizable compute capacity in the cloud. It is designed to make web-scale cloud computing easier for developers. You can read in details and create a free try-out account if you don't have one here :  [Amazon EC2 main page](https://aws.amazon.com/ec2/)
