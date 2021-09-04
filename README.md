
# LAMP Stack deployment using ansible playbook

Deploy Gitea, your light weight git server on Debian System with ansible playbook

## Getting Started

### Inventory

* Copy sample invetory file `example.inventory.ini` to `inventory.ini` using `cp example.inventory.ini.j2 inventory.ini`
* Change `ansible_host` value with host IP
* Add ssh username to `ansible_user`

### Variables

Copy sample variable file located in vars directory 
`example.vars.yml` to `vars.yml` using `cp example.vars.yml vars.yml`
##  Ansible Installation

Install ansible with the following

### Install python3 & pip3 

```bash
sudo apt install python3 python3-pip -y`
```

### Install ansible

```bash
python3 -m pip install ansible
```

### install required modules

```bash
ansible-galaxy collection install -r requirements.yml
```
## Deployment

To deploy LAMP stack on debian system run

```bash
  ansible-playbook main.yml
```
Append `-K` if ansible users needs sudo password to elevate sudo privileges

### Configuration

After succesful Deployment visit `IP:3000` and fill out the details

### Database Settings:

We are using SQLite

* Database Type: SQLite3
* Path: Use an absolute path, `/var/lib/gitea/data/gitea.db`
* Application General Settings:

* Site Title: Enter your organization name.
* Repository Root Path: Leave the default `var/lib/gitea/data/gitea-repositories`.
* Git LFS Root Path: Leave the default `/var/lib/gitea/data/lfs`.
* Run As Username: `git`
* SSH Server Domain: Enter your domain or server IP address.
* SSH Port: `22`, change it if SSH is listening on other Port
* Gitea HTTP Listen Port: `3000`
* Gitea Base URL: Use http and your domain or server IP address e.g. `http://127.0.0.1`
* Log Path: Leave the default `/var/lib/gitea/log`

To complete the installation click on install and it'll redirect to the login page.

## Post Deployment

/etc/gitea is temporary set with write rights for user `git` so that Web installer could write configuration file.
After installation is done, it is recommended to set rights to read-only using:

```bash
ansible-playbook post_install.yml
```
Append `-K` if ansible users needs sudo password to elevate sudo privileges

## License

[MIT](https://choosealicense.com/licenses/mit/)

  
## Authors

- [@kdpuvvadi](https://www.github.com/kdpuvvadi)

  
## 🔗 Links
[![twitter](https://img.shields.io/badge/twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white)](https://twitter.com/kdpuvvadi)
