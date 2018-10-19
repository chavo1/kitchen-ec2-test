
# This is kitchen test that will test an AMI under Your AWS account.
If you have AMI with [nginx](https://www.nginx.com/) you can continue with prerequisite if no [here](https://github.com/chavo1/ami-nginx) in other repo is an explanation how to build you own.

##Prerequisite:

Be sure you have [AWS key pair](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html). 
In the example in "kitchen.yml" file under driver section:

```
aws_ssh_key_id: id_rsa
```
Is a key which is imported to or genarated in [AWS](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html). Under the transport section is a private part of this pair which is located on your machine:
```
ssh_key: "~/.ssh/id_rsa"
```
Be sure you have installed "rbenv", if not follow below:
```
brew install rbenv
rbenv install 2.3.1
rbenv local 2.3.1
rbenv versions //to check if version is 2.3.1
```
add the following to your ~/.bash_profile:

```
eval "$(rbenv init -)"
true
export PATH="$HOME/.rbenv/bin:$PATH"
```

source ~/.bash_profile

**Usage example:**

This will create EC2 instance from AWS AMI  with "ubuntu-xenial-14.04" and "nginx".

1.  Fork the copy of chavo1/kitchen-ec2-test
2.  Download a ZIP with following link:
```
https://github.com/chavo1/kitchen-ec2-test/archive/master.zip
```
 - Or open it with GitHub Desktop:
```
https://github.com/chavo1/kitchen-ec2-test.git
```
3. Install needed gems with following:
```
gem install kitchen-inspec
gem install kitchen-ec2
```
4. Than you can test it with following commands:

```
kitchen list
kitchen converge
kitchen verify
```
The result should be as follow:

```
 System Package nginx
     ✔  should be installed
  File /etc/nginx/sites-available/default
     ✔  should exist
  Port 80
     ✔  should be listening
  Nginx Environment
     ✔  support_info should match /TLS/
  Nginx Environment
     ✔  version should eq "1.10.3"
```

 - For more [nginx inspec audit](https://www.inspec.io/docs/reference/resources/nginx/)

5. Destroy the EC2 instance:
```
kitchen destroy
```
