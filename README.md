# Kubernetes

Installation steps
-------------------
1. apt update && apt upgrade -y && apt install build-essential -y
2. sudo apt-get update && sudo apt-get install -y apt-transport-https
3. curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
4. echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
5. sudo apt-get update
6. sudo apt-get install -y kubectl
7. curl -LO https://github.com/kubernetes/kops/releases/download/$(curl -s https://api.github.com/repos/kubernetes/kops/releases/latest | grep tag_name | cut -d '"' -f 4)/kops-linux-amd64
8. chmod +x kops-linux-amd64
9. mv kops-linux-amd64 /usr/local/bin/kops

Cluster configuration
---------------------

1. sudo apt install s3cmd

2. sudo apt install awscli

3. s3cmd --configure
      Access Key: xxxxxx
      Secret Key: xxxxxx
      Default Region: xxxxx
      S3 Endpoint: s3.amazonaws.com
      DNS-style bucket+hostname:port template for accessing a bucket: %(bucket)s.s3.amazonaws.com
      Encryption password:
      Path to GPG program: /usr/bin/gpg
      
4. aws configure
      AWS Access Key ID [None]: xxxxxxx
      AWS Secret Access Key [None]: xxxxxxx
      Default region name [None]: xxxxx
      Default output format [None]: 
      
6. s3cmd mb s3://xxxxxxxx

7. vi .bashrc and add these lines at the end
      export REGION=xxxxxx
      export KOPS_STATE_STORE=s3://xxxxxx
      export NAME=xxxxxxxxx.com
