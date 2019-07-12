Oráculo BOT Telegram com DOCKER
=========================

### Este BOT possui comandos especificos para algumas tarefas, algoritmos de inteligência artificial [Machine learning] que usa linguagem natural [NLTK] para responder aos administradores ou usuários autorizados previamente. 

### This BOT has specific commands for some tasks, artificial intelligence algorithms [Machine learning] that uses natural language [NLTK] to respond to administrators or previously authorized users. 

#### Está em uso na ferramenta os seguintes aplicações:

	-> Python3 https://www.python.org/
	-> Chatterbot https://chatterbot.readthedocs.io/en/stable/
	-> NLTK https://www.nltk.org/
	-> DOCKER https://www.docker.com/  

OBS: Antes de executar o projeto siga todos os passos abaixo, observando o ambiente que esta executando o DOCKER

# Trocar o token do BOT do Telegram

#### /oraculo/bot.py
	
		TOKEN='868879441:AAE0BXeFe9eW4QOKKA_ZxhijiNdg-FB_jTY'

https://core.telegram.org/bots

#### Coloque o seu ID no BOT
##### caso não coloque o BOT ficará lhe ignorando mandando frases aleatórias  	
	lauro=67993868

#### Comandos para preparar o host DOCKER

##### sdocker é o hostname da máquina
##### Usei o ANSIBLE para realizar a instalação 

	->  ansible -m ping sdocker
	->  ansible -m shell -a "hostnamectl set-hostname sdocker" sdocker
	->  ansible -m shell -a "sed -i --follow-symlinks 's/SELINUX=enforcing/SELINUX=disabled/g' /etc/sysconfig/selinux" sdocker
	->  ansible -m shell -a "setenforce 0" sdocker
	->  ansible -m yum -a "name=* state=latest" sdocker
	->  ansible -m yum -a "name=yum-utils state=latest" sdocker
	->  ansible -m yum -a "name=device-mapper-persistent-data state=latest" sdocker
	->  ansible -m yum -a "name=lvm2 state=latest" sdocker
	->  ansible -m sysctl -a "name=vm.max_map_count value=262144 state=present sysctl_set=yes reload=yes" sdocker
	->  ansible -m get_url -a "url=https://get.docker.com dest=/tmp/get-docker.sh" sdocker
	->  ansible -m shell -a "sh /tmp/get-docker.sh" sdocker
	->  ansible -m systemd -a "name=docker enabled=yes state=restarted" sdocker
	->  ansible -m yum -a "name=docker-compose.noarch state=latest" sdocker
	->  ansible -m yum -a "name=rsync state=latest" sdocker


#### Comandos para preparar levantar o POD

	-> docker build -t bot:003 .
	-> docker run -ti bot:003

# LISTA DE COMANDOS do BOT #

	-> "/help"
	-> "/frases"
	-> "/frases_amor"
	-> "/frases_dev"
	-> "/frases_inteligentes"
	-> "/bop"
	-> "/lero_lero"
	-> "/teste"
	-> "/teste_diretorio"
	-> "/versao"
	-> "/liga"
	-> "/ping"
	-> "/hostname"

![Screenshot](https://raw.githubusercontent.com/laurobmb/oraculo_bot_telegram/master/imagens/bot01.png)

![Screenshot](https://raw.githubusercontent.com/laurobmb/oraculo_bot_telegram/master/imagens/bot02.png) ![Screenshot](https://raw.githubusercontent.com/laurobmb/oraculo_bot_telegram/master/imagens/bot03.png)
