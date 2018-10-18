# Prerequisite:

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
2.  Clone it with following :
```
git clone git@github.com:chavo1/kitchen-ec2-test.git
```
3. Install and init kitchen-ec2 driver with following:
```
kitchen init --driver=kitchen-ec2 --create-gemfile
bundle install
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
-For more [nginx inspec audit](https://www.inspec.io/docs/reference/resources/nginx/)

5. Destroy the EC2 instance:
```
kitchen destroy
```
