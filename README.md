# OpenShift-GitlabDeployment
Created for Arctiq Interview

Installed on AWS

Uses Terraform and ansible to install Openshift 3.9 on AWS. Then

>Edited version  Dave Kerr's awesome code at: https://github.com/dwmkerr/terraform-aws-openshift

The code works by running the terraform init terraform get and terraform apply to
form the initial infastruture and output the variables such as hostname which will later be used by the ansible installter
to create the openshift cluster.

The Basic structure is as follows:
```
Terraform creates infastructure-->bash script install of ansible and scp iventory.cfg-->ansible runs ansible-openshift installer--> Manually setup the gitlab server.
```

The code has been edited to create 1 bastion server (to ssh in and run the ansible playbook)
1 Master server and 1 Node

The server can be run as a single master node, and the invetory can be edited to configure that way.

# The Basics


GitLab requires to be run as privileged

```
oc edit scc restricted
  runAsUser:
  type: RunAsAny
```


List DNS entries


# Requirements
AWS account with key generated

AWS CLI

brew (If on a mac)




# Steps:
```
brew install terraform

brew install awscli

brew install git

git clone https://github.com/Joel-Cripps/OpenShift-GitlabDeployment.git

make infrastructure #Runs the terraform init,get and apply
```
Installs Openshift 3.9




# Resources/References
Gitlab Openshift Installation Instructions:

https://about.gitlab.com/2016/06/28/get-started-with-openshift-origin-3-and-gitlab/

https://docs.gitlab.com/omnibus/development/openshift/#install-gitlab

Openshift-Ansible installer:
https://github.com/openshift/openshift-ansible

OpenShift Documentation:
https://docs.openshift.com/container-platform/3.5/install_config/install/advanced_install.html

Terraform Documentation:
https://www.terraform.io/intro/getting-started/install.html

