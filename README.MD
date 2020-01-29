# Example use docker
### Install docker, docker compose, google chrome, phpstorm

### Manual install
##### Install docker command with use get-docker.sh (script docker.com)

	sudo apt install curl -y
	curl -fsSL https://get.docker.com -o get-docker.sh
	sudo sh get-docker.sh
	sudo rm get-docker.sh
	sudo usermod -aG docker $USER
	after bash command you must reload OS

##### Install docker compose
	sudo curl -L "https://github.com/docker/compose/releases/download/1.24.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
	sudo chmod +x /usr/local/bin/docker-compose

##### Install phpstorm with use snap
	sudo snap install phpstorm --classic 

##### Install google chrome
	wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
	sudo sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list'
	sudo apt-get update -y
	sudo apt-get install google-chrome-stable -y

### Auto install
	use ./bin/installall
	
# Beautiful view branch for terminal
### Add this code to ~/.bashrc
	parse_git_branch() {
	     git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ [\1]/'
	}
	export PS1="\u@\h \[\033[32m\]\w\[\033[33m\]\$(parse_git_branch)\[\033[00m\] $ "
