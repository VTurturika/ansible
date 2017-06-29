# Ansible example app

## Architecture
* `nginx` + `php7.0-fpm`
* `postfix`
* [php backend](https://github.com/VTurturika/ansible-app-backend.git) with very simple frontend (send request params to specified email)
* `mailhog` for testing and development
* two environments: `staging` and `production`

## Requirements
* For control machine unix-like system with `python2.7` will be enough
* For working machines debian based distro with `python2.7` and `pip2` will be enough (tested on ubuntu server 16.04)

## Using

1. Clone repository:
````
git clone https://github.com/VTurturika/ansible && cd ansible
````

2. Set ip of your remote hosts in files `production` and `staging`. (Be careful! ip temporary harcoded to playbook)

3. Change username in `app.yml`

3. For deploy `production` enviromnent use
````
ansible-playbook -i production app.yml
````

4. For deploy `staging` enviromnent use
````
ansible-playbook -i staging app.yml
````

5. Also, for `staging` environment you may explicit start and stop `mailhog`
````
ansible-playbook -i staging app.yml -e mailhog=start
ansible-playbook -i staging app.yml -e mailhog=stop
````

## Notes

* If your remote host requires sudo password use `--ask-become-pass`
* By default `mailhog` web UI using 8025 port
* Backend also available [here](https://github.com/VTurturika/ansible-app-backend)
