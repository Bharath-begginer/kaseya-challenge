# Solution

## Create Jenkins and Windows instance

```bash
$ terraform init
$ terraform apply
```

Above will an ubuntu instance in aws and install jenkins and ansible in it. It will also create Windows server with username 'Administrator' and password 'Testpwd123**!' (can be overwritten by passing terraform variable winpassword) in aws.

## Setup jenkins job

1. SSH into the jenkins instance with key from terraform output with ubuntu username.
2. Get admin password from /var/lib/jenkins/secrets/initialAdminPassword.
3. Access jenkins with IP address of jenkins instance at port 80
4. Login with admin password
5. Install suggested plugins and set up new user.
6. Create a new jenkins pipeline job and select pipeline from scm and provide github url as https://github.com/Bharath-begginer/kaseya-challenge.git.
7. Run and test the job with correct parameters and confirm playbook is executed properly.
