# This repo contain Terraform code to spin up an Amazon Web Services (AWS) EC2 instance using Inspec and Kitchen-Terraform

### Following [this](https://newcontext-oss.github.io/kitchen-terraform/tutorials/amazon_provider_ec2.html) article

## Requirements
- [Terraform](https://www.terraform.io/) should be installed
- An AWS Account
- [Bundler](https://bundler.io/) should be installed
- The default security group on your account must allow SSH access from your IP address.
- Be sure you have installed "rbenv", if not - just install it:
```
brew install rbenv
rbenv install 2.6.5
rbenv local 2.6.5
rbenv versions //to check if version is 2.6.5
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
bundle install
```
3. Than you can test it with following commands:

```
bundle exec kitchen converge
bundle exec kitchen verify
```
- Here is the output:
```
Finished in 0.00143 seconds (files took 10.48 seconds to load)
0 examples, 0 failures
```
4. Destroy the EC2 instance:
```
bundle exec kitchen destroy
```
