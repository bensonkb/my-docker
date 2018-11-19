

FIRST START

1. Install docker:
	1.1 Add GPG key official docker repository:
		sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
	1.2 Add docker repository:
		sudo apt-add-repository 'deb https://apt.dockerproject.org/repo ubuntu-xenial main'
	1.3 Update:
		sudo apt-get update
	1.4 Check docker repository:
		apt-cache policy docker-engine
	1.5 Install docker:
		sudo apt-get install -y docker-engine
	1.6 Check docker status:
		sudo systemctl status docker
2. Install docker-compose:
	2.1 Install docker-compose:
		sudo curl -L https://github.com/docker/compose/releases/download/1.16.1/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
	2.2 Set permissions:
		sudo chmod +x /usr/local/bin/docker-compose
	2.3 Check docker-compose version:
		docker-compose -v
3. Clone directory 'docker-influencing-php5.6' into /var/www/:
	sudo cp -r 'from where' 'to where'
4. Set permissions on directory:
	sudo chmod -R 777 /var/www/docker-influencing-php5.6/
5. Add user in docker group:
	5.1 Add user:
		sudo usermod -aG docker $USER 
	NOTE! $USER - current user name with root permissions
	5.2 Reboot the computer and follow the next steps:
		sudo reboot 
6. Enter to the docker-project directory:
	cd /var/www/docker-influencing-php5.6/
7. Start application:
	7.1 Start composing:
		docker-compose up --build
	NOTE! If you will launch this command with flag -d, you will not be able to track the state of the frontend-builder
	NOTE! Compose will be completed when you'll seen "Tested 484 tests, 484 passes, 0 failures: PASS" 
	7.2 Open the second new terminal, enter to dev-sphinx container by ssh and start sphinx service:
		ctrl+alt+T
		docker exec -it dev-sphinx /bin/bash
		service sphinxsearch start
		exit
8. Check containers status:
	8.1 Lists all docker containers:
		docker ps 
	NOTE! All 11 containers must be 'up'
	8.2  If status 'Exit' check logs:
		docker logs 'container-name'
9. Open projects in browser:
	influencing:8080 and portal.influencing:8080
10. Stop application:
	docker-compose stop

!!! WARNING !!! 
	- DON'T CLOSE the terminal where the composite is running
	- if you'll seen red strings while composing KEEP CALM AND ENJOY ;)

SUBSEQUENT STARTS

1. Restart docker service:
	systemctl restart docker
2. Enter to the docker-project directory:
	cd /var/www/docker-influencing-php5.6/
3.1 Start application:
        docker-compose up --build
        NOTE! Compose will be completed when you'll seen "Tested 484 tests, 484 passes, 0 failures: PASS"
3.2 Open the second new terminal, enter to dev-sphinx container by ssh and start sphinx service:
        ctrl+alt+T
        docker exec -it dev-sphinx /bin/bash
        service sphinxsearch start
        exit
4. Open projects in browser:
        influencing:8080 and portal.influencing:8080
5. Stop application:
        docker-compose stop

Additional commands:
 - docker images (Lists all images)
 - docker exec -it 'container-name' /bin/bash (Enter to the container by ssh)

--------------------------------------------------------------------------------------------------------------------
### Structure

├── projects
│   ├── influencing
│   └── portal.influencing
├── databases
│   ├── mysql
│   └── mongo
├── fpm
│   ├── cli
│   │   └── php.ini
│   ├── fpm
│   │   └── php.ini
│   ├── Dockerfile
│   └── supervisord.conf
├── frontend
│   └── Dockerfile
├── nginx
│   ├── Dockerfile
│   ├── influencing.conf
│   ├── portal.influencing.conf
│   ├── i.influencing.conf
│   └── nginx.conf
├── phpmyadmin
│   └── config.user.inc.php
├── realtime
│   ├── config
│   │    ├── config.js
│   │    └── config.js.dist
│   ├── docs
│   │    ├── development
│   │    └── realtime-chats.service
│   ├── logs
│   ├── node_modules
│   ├── Dockerfile
│   ├── index.html
│   ├── package.json
│   └── server.js
├── sphinxsearch
│   ├── data
│   ├── Dockerfile
│   ├── sphinxsearch
│   ├── indexandsearch.sh
│   ├── searchd.sh
│   └── sphinx.conf
├── docker-compose.yml
└── readme.txt

- `projects` is the projects directory.
- `realtime` is the realtime-project directory. 

-------------------------------------------------------------------------------------------------------------------
