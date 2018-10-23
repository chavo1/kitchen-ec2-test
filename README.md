# This repo contain a project that test AWS AMI for installed nginx

## Requirements

[Export your AWS](https://docs.aws.amazon.com/cli/latest/userguide/cli-environment.html) "Access" and "Secret" keys as follow:
```
export AWS_ACCESS_KEY_ID=<MYACCESSKEYID>
export AWS_SECRET_ACCESS_KEY=<MYSECRETACCESSKEY>
```

The values of <u>**AMI image**</u> and <u>**Security group**</u> are hardcoded in "kitchen.yml" file and you should change it with your own.

- For the test is needed an [AWS key pair](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html), which are imported to or genarated in [AWS](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html). Under the transport section is a private part of this pair which is located on your machine:

```
aws_ssh_key_id: id_rsa

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


1.  Clone the repo:

```
git clone https://github.com/chavo1/kitchen-ec2-test.git
```
2. Install needed gems with following:
```
gem install kitchen-inspec
gem install kitchen-ec2
```
3. Than you can test it with following commands:

```
kitchen list
kitchen converge
kitchen verify
```

 - For more [nginx inspec audit](https://www.inspec.io/docs/reference/resources/nginx/)

4. Destroy the EC2 instance:
```
kitchen destroy
```
