# linux

## environment variables

export MYVAL="Hello world"

echo ${MYVAL}


## systemctl

systemctl start postgresql

systemctl restart postgresql

// so that postgresql starts automatically after reboot
systemctl enable postgresql

### list all services
systemctl list-unit-files


## curl

curl -i http://localhost:8080/v1/hello -H "Authorization: Bearer yoursupersecret"


## ssh scp

SSH SCP to copy files to server
SSHPASS to help escape ssh password prompt

[GitLab Build and Deploy to a Server via SSH](https://codeburst.io/gitlab-build-and-push-to-a-server-via-ssh-6d27ca1bf7b4)

Deploying to SSH Server

We are going to be using sshpass to perform our secured copy (scp) since we can’t perform ssh directly on CI since it will request for password, which we can’t respond to. 

With sshpass we can set our password via SSHPASS environment variable and it will auto respond to anything ending with assword you can change this based on the way it requests for password entry.

apt-get update -qq && apt-get install -y -qq sshpass

export SSHPASS=$USER_PASS

sshpass -e scp -o stricthostkeychecking=no -r directory-to-copy user@host:path-to-copy-files-to


