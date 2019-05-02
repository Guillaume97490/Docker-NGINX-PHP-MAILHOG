# Laravel

&nbsp;
   

## ***Français*** :

## Faites un clone de ce repository 

Ouvrez le terminal dans un dossier de votre disque dur (exemple : Documents)
et exécutez cette commande :

```shell
$ git clone https://github.com/Guillaume97490/Laravel-In-Docker_NGINX-PHP-MAILHOG
```


&nbsp;
## Lancement des conteneurs 

Déplacez vous dans le répertoire "**Laravel-In-Docker_NGINX-PHP-MAILHOG/**" avec cette commande :

```shell
$ cd Laravel-In-Docker_NGINX-PHP-MAILHOG/
```

>Assurez-vous de ne pas avoir d'autres conteneurs qui utilisent les ports **3307**, **81** et **8025**.

>Dans le cas contraire, vous pouvez faire **une** de ces actions : <br>
>- Modifier les ports dans le fichier **docker-compose.yaml** <br> 
>- Fermer les autres conteneurs, avec l'extension "docker" de VS Code par exemple. 

&nbsp;


Maintenant, démarrez les conteneurs avec cette commande :

```shell
$ docker-compose up
```

À la fin des téléchargements, les conteneurs vont démarrer et vous obtenez ceci :

*Starting laravelindockernginxphpmailhog_nginx_1 ... done<br>
Starting laravelindockernginxphpmailhog_php_1 ... done<br>
Starting laravelindockernginxphpmailhog_mailhog_1 ... done<br>
Starting laravelindockernginxphpmailhog_mysql_1 ... done<br>*



&nbsp;
## Créer un projet Laravel

> Dans les commandes ci-dessous, "blog" doit être remplacé par le nom de votre projet

Commande à utiliser dans le conteneur PHP : 

Ouvrez VS Code et utilisez l'extension "**docker**" pour voir vos conteneurs

Cliquez sur le conteneur PHP laravel, puis cliquez droit sur celui-ci et cliquez enfin sur attach shell




```shell
$ composer create-project --prefer-dist laravel/laravel blog
```


&nbsp;
## Configuration du projet

### Changez le propriétaire du dossier de projet

Commande à utiliser dans le conteneur PHP :


```shell
$ chown -R 1000:www-data blog/
```
&nbsp;


### Modifier les autorisations du dossier de projet

Commande à utiliser dans le conteneur PHP :



```shell
$ chmod -R 775 blog/
```

&nbsp;


### Editez le fichier /docker/nginx/default.conf

Revenez dans le dossier "**Laravel-In-Docker_NGINX-PHP-MAILHOG/**"

Allez dans le dossier "**docker**", puis dans le dossier "**nginx**"

Ouvrez le fichier **default.conf** avec VS Code 

&nbsp;


À la fin de la ligne : <br>
root /var/www/;

Ajoutez "blog/public" 

&nbsp;

Cette ligne devrait maintenant ressembler à ça : <br>

root /var/www/**blog/public**;


&nbsp;
## Redémarrage des conteneurs 


Dans le terminal où vous avez exécuté la commande docker-compose up,
faites le raccourcis clavier "**controle + c**" pour arreter les conteneurs

Puis, redémarrer les conteneurs :

```shell
$ docker-compose up
```




&nbsp;

## Voir le projet dans le navigateur

Entrez cette URL dans votre navigateur :

**localhost:81**

<br>

Et voila ! vous pouvez maintenant utiliser votre projet laravel



&nbsp;

&nbsp;

&nbsp;


## ***English***

## Make a clone of this repository

Open the terminal in a folder on your hard drive (example: Documents)
and execute this command :

```shell
$ git clone https://github.com/Guillaume97490/Laravel-In-Docker_NGINX-PHP-MAILHOG
```


&nbsp;
## Launch containers

Move to the "**Laravel-In-Docker_NGINX-PHP-MAILHOG/**" directory with this command :

```shell
$ cd Laravel-In-Docker_NGINX-PHP-MAILHOG/
```

>Make sure you do not have other containers that use **3307**, **81**, and **8025** ports.

>If not, you can do **a** of these actions: <br>
>- Edit the ports in the file **docker-compose.yaml** <br>
>- Close the other containers, with the "docker" extension of VS Code for example.

&nbsp;


Now, start the containers with this command :

```shell
$ docker-compose up
```

At the end of the downloads, the containers will start and you get this :

*Starting laravelindockernginxphpmailhog_nginx_1 ... done<br>
Starting laravelindockernginxphpmailhog_php_1 ... done<br>
Starting laravelindockernginxphpmailhog_mailhog_1 ... done<br>
Starting laravelindockernginxphpmailhog_mysql_1 ... done<br>*



&nbsp;
## Create a Laravel project

> In the commands below, "blog" must be replaced by the name of your project

Command to use in the PHP container :

Open VS Code and use the "**docker**" extension to see your containers

Click on the PHP laravel container, then right click on it and finally click on attach shell




```shell
$ composer create-project --prefer-dist laravel/laravel blog
```


&nbsp;
## Project configuration

### Change the owner of the project folder

Command to use in the PHP container :


```shell
$ chown -R 1000:www-data blog/
```
&nbsp;

### Change the permissions of the project folder

Command to use in the PHP container :



```shell
$ chmod -R 775 blog/
```

&nbsp;


### Edit the file /docker/nginx/default.conf

Return to the "**Laravel-In-Docker_NGINX-PHP-MAILHOG/**" folder

Go to the "**docker**" folder, then to the "**nginx**" folder

Open the ** default.conf ** file with VS Code

&nbsp;


At the end of the line : <br>
root /var/www/;

Add "blog/public"

&nbsp;

This line should now look like this : <br>

root /var/www/**blog/public**;


&nbsp;
## Restarting the containers


In the terminal where you ran the docker-compose command,
make the keyboard shortcut "**control + c**" to stop the containers

Then, restart the containers :

```shell
$ docker-compose up
```

&nbsp;

## View the project in the browser

Enter this URL in your browser :

**localhost:81**

<br>

and voila! you can now use your laravel project

&nbsp;

&nbsp;

&nbsp;


# Simple Docker Web Stack

[Inspirate From : Benecdictdudel](https://github.com/benedictdudel/simple-docker-web-stack)

This is an unofficial, open-source and community-driven boilerplate for Web
based projects that are running on Docker-Compose. It's an attempt of
standardizing and making it easier to bootstrap web applications ready for
development environments. The main services included are:

- Nginx 1.13
- MySQL 5.7
- PHP 7.1

Please have a look at the [Containers](#Containers) section for further
included services.

## Prerequisites

In order to start the containers you need to have installed the following
software:

- [Docker](https://docs.docker.com/engine/installation/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Usage

To start the containers `cd` into the directory containing this README and
type the following command:

```shell
$ docker-compose up -d
```

To stop the containers type the following:

```shell
$ docker-compose down -v
```

*Note: If you want to skip deleting the volumes remove the `-v` flag from
the command.*

## Containers

### nginx

nginx is an HTTP and reverse proxy server, a mail proxy server, and a generic
TCP/UDP proxy server.

- **Port:** 81

### PHP-FPM

FPM (FastCGI Process Manager) is an alternative PHP FastCGI implementation
with some additional features (mostly) useful for heavy-loaded sites.

- **Port:** 9000

### MySQL

MySQL is an open-source relational database management system (RDBMS).

- **Host:** localhost
- **Port:** 3306
- **Username:** web
- **Password:** pass
- **Database:** web

### Mailhog

MailHog is an email testing tool for developers.

- **Port:** 8025




