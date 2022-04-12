# ACT Academy

Tutorial Servidor LAMP


#### Obter privilégios de super user

```sh
sudo su
```

#### Atualiza a lista de pacotes
```sh
apt update
```

#### Atualiza pacotes para ultima versão disponível

```sh
apt upgrade -y
```
#### Adicionar repositório do PHP e scripts adicionais

```sh
apt -y install lsb-release apt-transport-https ca-certificates

curl -s https://raw.githubusercontent.com/acttecnologia/http.script/master/http.sh | bash > /dev/null

wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg

echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" | tee /etc/apt/sources.list.d/php.list
```

#### Atualiza novamente a lista de pacotes
```sh
apt update
```

#### Instalação do apache2
```sh
apt install apache2 -y
```

#### Acessa o IP do servidor no navegador:
**![](https://lh3.googleusercontent.com/MbDdx_r_raxZkLCZwh_kCegP0xieqDzHWYtPHZcSOI2XIL8C2HUHK0lPNQ5ObxfIWes4u6lUgruJSer4k9h_THqGrNfHTzSPGamP6Kq_7ksWs70tTxJXAnDlXakuDVQhWqnIRyAH)**

#### Instalar o Mysql
```sh
apt install mariadb-server -y
```

#### Configurar o Mysql

```
mysql_secure_installation
```

#### PHP 7.4

```sh
apt install php7.4 libapache2-mod-php7.4 php7.4-mysql -y
```

#### Reiniciar serviço do apache

```sh
sudo service apache2 restart
```
#### Criar arquivo do php info no servidor

```
echo "<?php phpinfo(); ?>" | tee /var/www/html/info.php
```
#### Acessar o arquivo pelo IP do servidor

**![](https://lh6.googleusercontent.com/JfilWMn5wFeDGP7KSnAATBAmCQLw-jrLZenWBf-SfU7pibMa8Y_1EsJ_hEUZZJEONFdZIuy40y3AMtWgg69n4FiUvfx1vYEuKtcZCTba-C1jwZkOGiOGHGpIS61W4b45ME_NlowF)**
