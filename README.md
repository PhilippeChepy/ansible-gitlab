# Installing GitLab + Docker registry

In order to use this repository:

* You need ansible installed. On OS-X ansible can be installed with :
```sh
$ brew install ansible
```

* You need an email address for gitlab and let's encrypt.
* You also need a server with one (sub)domain for gitlab, and one (sub)domain for docker registry.

In `inventory`, replace "(target_ip_address)" with your server ip address.
In `roles/gitlab/defaults/main.yml`, fill `gitlab_smtp_user_name` and `gitlab_smtp_password` with email account credentials, specifically used by gitlab for notifications.

In `roles/nginx-front/defaults/main.yml`, set :
* `nginx_git_domain_name` with your git domain name (for example: `git.mydomain.com`)
* `nginx_git_domain_contact_email` with an email address used for Let's Encrypt notifications (for example: `contact@git.mydomain.com`)

* `nginx_registry_domain_name` with your registry domain name (for example: `registry.mydomain.com`)
* `nginx_registry_domain_contact_email` with an email address used for Let's Encrypt notifications (for example: `contact@registry.mydomain.com`)

Once these prerequisities are met, you can launch the playbook from the root of this repository : 
```sh
$ git clone https://github.com/PhilippeChepy/ansible-gitlab.git
$ cd ansible-gitlab
$ ansible-playbook -i inventory main.yml
```
