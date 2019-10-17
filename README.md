# packer-ansible-terraform
This project is an example of creating image of cloud server on scaleway.io provider with packer and ansible, and creating cloud server from this image with terraform 

Prerequisites
-------------

packer, ansible and terraform installed

Deployment
----------

### 1.
First of all, create environment variables with API keys for packer and terraform:
```bash
# for packer
export SCALEWAY_ORGANIZATION=<your organization id>
export SCALEWAY_API_TOKEN=<your scaleway api token>
# for terraform
export SCW_DEFAULT_ORGANIZATION_ID=<your organization id>
export SCW_ACCESS_KEY=<your scaleway api token>
export SCW_SECRET_KEY=<your scaleway secret key>
```
### 2.
Then run commands:
```bash
git clone https://github.com/digitalstudium/packer-ansible-terraform.git
cd packer-ansible-terraform/ansible
ansible-galaxy -r install playbooks/docker-and-compose/requirements.yml
```
These commands install example ansible role (the role installs docker and dopcker compose in image)

### 3.
Then go to packer directory and build image:
```bash
cd ../packers/centos-docker-and-compose/
packer build packer.json
```
This command build image from centos-7 and installs docker and docker-compose to this image using ansible.

### 4.
After image is bult (you could see it in your scaleway console) you can create cloud server from this image using terraform.
Run commands:
```bash
cd ../../terraform/centos-docker-and-compose/
terraform init
terraform plan
terraform apply
```

Troubleshooting
-------

You could create an issue for this repository


License
-------

GPLv3

Author Information
------------------

Costel Shootkin, costel@digitalstudium.com
