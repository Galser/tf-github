# tf-github
Terraform GitHub provider

# Introduction
The GitHub provider is used to interact with GitHub organization resources. See detailed desciption here : [GitHub Provider](https://www.terraform.io/docs/providers/github/index.html)

The provider allows you to manage your GitHub organization's members and teams easily. It needs to be configured with the proper credentials before it can be used. 

This repo demonstrates usage of some basic feature of the GitHub provider , not all of them. 

# Requirements
This repo assumes general knowledge about Terraform for AWS, if not, please get yourself accustomed first by going through [getting started guide](https://learn.hashicorp.com/terraform?track=getting-started#getting-started) . Please also have your AWS credentials prepared in some way, preferably environment variables. See in details here : [Section - Keeping Secrets](https://aws.amazon.com/blogs/apn/terraform-beyond-the-basics-with-aws/)

To learn more about the mentioned above tools and technologies -  please check section [Technologies near the end of the README](#technologies)

# How to use

- Download copy of the code (*clone* in Git terminology) - go to the location of your choice (normally some place in home folder) and run in terminal; in case you are using alternative Git Client - please follow appropriate instruction for it and download(*clone*) [this repo](https://github.com/Galser/tf-github.git). 
```
git clone https://github.com/Galser/tf-github.git
```

- Previous step should create the folder that contains a copy of the repository. Default name is going to be the same as the name of repository e.g. `tf-github`. Locate and open it.
 ```
 cd tf-github
 ```
- You will need first to create Personal Access Token in GitHub, use [this link](https://github.com/settings/tokens), write down the token, as you are going to see it only once! And note also your organization name. 
- Export token as environment variable, execute : 
```
export GITHUB_TOKEN=YOUR_TOKEN_HERE
```
- This repository already contains all required ode, so let's just do customization. Put your organization name and desired repository name with description in [variables.tf](variables.tf) :
    ```terraform
    variable "github_organization" { 
        default = "ORGatization"  ## your organization name here
    }

    variable "repo_name"  {
        description = "Repository name"
        default     = "example"   ## your repository name here
    }
    ```
- Init Terraform by running :
    ```
    terraform init
    ```
    Output should start with something like : 
    ```
    Initializing the backend...

    Initializing provider plugins...
    - Checking for available provider plugins...
    - Downloading plugin for provider "github" (hashicorp/github) 2.2.1...
    ```
- Apply the code with :
    ```
    terraform apply
    ```
    Output going to be :
    ```shell
    An execution plan has been generated and is shown below.
    Resource actions are indicated with the following symbols:
    + create

    Terraform will perform the following actions:

    # github_repository.example will be created
    + resource "github_repository" "example" {
        + allow_merge_commit = true
        + allow_rebase_merge = true
        + allow_squash_merge = true
        + archived           = false
        + default_branch     = (known after apply)
        + description        = "Example codebase repo"
        + etag               = (known after apply)
        + full_name          = (known after apply)
        + git_clone_url      = (known after apply)
        + html_url           = (known after apply)
        + http_clone_url     = (known after apply)
        + id                 = (known after apply)
        + name               = "example"
        + ssh_clone_url      = (known after apply)
        + svn_url            = (known after apply)
        }

    Plan: 1 to add, 0 to change, 0 to destroy.

    Do you want to perform these actions?
    Terraform will perform the actions described above.
    Only 'yes' will be accepted to approve.

    Enter a value: yes

    github_repository.example: Creating...
    github_repository.example: Creation complete after 4s [id=example]
    data.github_repository.example: Refreshing state...

    Apply complete! Resources: 1 added, 0 changed, 0 destroyed.

    Outputs:

    full_repo_web_path = https://github.com/ORGatization/example
    repo_description = Example codebase repo
    ssh_clone_url = git@github.com:ORGatization/example.git
    ```
    As you can see from above, the result of the Terraform run is that we had created repository, with proper description, and it cna be cloned by SSH, fo example, using the 
    URL git@github.com:ORGatization/example.git
- When you've done with checking (for example you can visit GitHub Web-page of repo, to be absolutely sure that all went well), please do not forget to free resources (in this case - delete the repo) by running : 
    ```
    terraform destroy
    ```
    And confirm with `yes`, your output should look like this:
    ```
    data.github_repository.example: Refreshing state...
    github_repository.example: Refreshing state... [id=example]

    An execution plan has been generated and is shown below.
    Resource actions are indicated with the following symbols:
    - destroy

    Terraform will perform the following actions:

    # github_repository.example will be destroyed
    - resource "github_repository" "example" {
        - allow_merge_commit = true -> null
        - allow_rebase_merge = true -> null
        - allow_squash_merge = true -> null
        - archived           = false -> null
        - default_branch     = "master" -> null
        - description        = "Example codebase repo" -> null
        - etag               = "W/\"e43ac76ebdee7b9c422357d2c4a76898\"" -> null
        - full_name          = "ORGatization/example" -> null
        - git_clone_url      = "git://github.com/ORGatization/example.git" -> null
        - has_downloads      = false -> null
        - has_issues         = false -> null
        - has_projects       = false -> null
        - has_wiki           = false -> null
        - html_url           = "https://github.com/ORGatization/example" -> null
        - http_clone_url     = "https://github.com/ORGatization/example.git" -> null
        - id                 = "example" -> null
        - name               = "example" -> null
        - private            = false -> null
        - ssh_clone_url      = "git@github.com:ORGatization/example.git" -> null
        - svn_url            = "https://github.com/ORGatization/example" -> null
        }

    Plan: 0 to add, 0 to change, 1 to destroy.

    Do you really want to destroy all resources?
    Terraform will destroy all your managed infrastructure, as shown above.
    There is no undo. Only 'yes' will be accepted to confirm.

    Enter a value: yes

    github_repository.example: Destroying... [id=example]
    github_repository.example: Destruction complete after 0s

    Destroy complete! Resources: 1 destroyed.    
    ```
    This concludes the "How to use" section.


# To do

- [ ] update readme

# Done
- [x] initial README
- [x] introduction section
- [x] prepare environment (create tokens and etc)
- [x] create demo code
- [x] test code


# Technologies

1. **To download the content of this repository** you will need **git command-line tools**(recommended) or **Git UI Client**. To install official command-line Git tools please [find here instructions](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) for various operating systems. 
2. **For managing infrastructure** we using Terraform - open-source infrastructure as a code software tool created by HashiCorp. It enables users to define and provision a data center infrastructure using a high-level configuration language known as Hashicorp Configuration Language, or optionally JSON. More you encouraged to [learn here](https://www.terraform.io). 
3. **This project for virtualization** relies on **AWS EC2** - Amazon Elastic Compute Cloud (Amazon EC2 for short) - a web service that provides secure, resizable compute capacity in the cloud. It is designed to make web-scale cloud computing easier for developers. You can read in details and create a free try-out account if you don't have one here :  [Amazon EC2 main page](https://aws.amazon.com/ec2/)
