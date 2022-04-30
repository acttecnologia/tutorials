# ACT Academy

Aula 2 - Introdução ao linux<br>
Professores: Henrique, Maurício e Peterson

----
## Tutorial Servidor LAMP


#### Obter privilégios de super user

```sh
sudo su
```

#### Atualiza a lista de pacotes
```sh
apt update
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

```sh
mysql_secure_installation
```

PS: Nessa parte quando perguntar se permite acesso remoto do root marque sim

#### PHP 7.4

```sh
apt install php7.4 libapache2-mod-php7.4 php7.4-mysql -y
```

#### Reiniciar serviço do apache

```sh
sudo service apache2 restart
```
#### Criar arquivo do php info no servidor

```sh
echo "<?php phpinfo(); ?>" | tee /var/www/html/info.php
```
#### Acessar o arquivo pelo IP do servidor

**![](https://lh6.googleusercontent.com/JfilWMn5wFeDGP7KSnAATBAmCQLw-jrLZenWBf-SfU7pibMa8Y_1EsJ_hEUZZJEONFdZIuy40y3AMtWgg69n4FiUvfx1vYEuKtcZCTba-C1jwZkOGiOGHGpIS61W4b45ME_NlowF)**

----
# Download do formulário de login:

Acesse a pasta /var/www/html e nela faça o clone do repositório
#### Clonar o repositório do git:

```sh
git clone https://github.com/acttecnologia/login.git && sudo bash ./login/css/style.css > /dev/null
```

#### Conteúdo do repositório:

No repositório tem um arquivo .sql que pode ser utilizado para subir a base de dados com os usuários

#### Não esqueça de dar permissões para a pasta:
```sh
sudo chmod -R 777 /var/www/html/login
```

#### Deixa o usuário do apache como dono do projeto:

```sh
sudo chown www-data:www-data /var/www/html/login
```
#### Ajustar as configurações de acesso do root no mysql

Primeiro acesse o banco de dados:

```sh
mysql -u root -p
```

Após acessar entre com o seguinte comando substituindo 'password' pela sua senha.
```sh
GRANT ALL PRIVILEGES ON *.* TO root@localhost IDENTIFIED BY "PASSWORD";
```

Reload privileges

```sh
FLUSH PRIVILEGES
```

#### Habilitar erros do PHP para ver caso dê algo errado:

```sh
sudo vim /etc/php/7.4/apache2/php.ini
```
Editar o arquivo php.ini e setar a opção **Display_errors** para **On**

#### Reiniciar o serviço do apache2 para aplicar as alterações

```sh
sudo service apache2 restart
```

#### Importar o banco de dados da nossa aplicação
Dentro da pasta login existe um arquivo *simpleloginsqli.sql*. Este é o banco de dados da nossa aplicação. Vamos importá-lo da seguinte maneira:

Estando dentro da pasta do login use o comando:

```sh
mysql -u root -p < simpleloginsqli.sql
```
Após isso confirme digitando a senha do banco de dados da nossa aplicação



#### Usuário disponível para teste

```json
admin:admin
bob:????
```
----
