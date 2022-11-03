# docker_wordpress

### Installation de Docker 

Pour installer Docker, il faut suivre les étapes suivantes :

1. Intaller Docker :
     
     <a href="https://docs.docker.com/installation/ubuntulinux/" target="_blank">installation</a>
     

### Installation de Docker Compose 

Pour installer Docker Compose, il faut suivre les étapes suivantes :

1. Saisir la commande suivante dans le terminal.

        curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

2. Changer les autorisations :

		$ chmod +x /usr/local/bin/docker-compose
    
3. Tester si l'installation s'est bien passée.

        $ docker-compose --version

### Modification du fichier docker-compose.yml 🖊

1. Créer un repertoire wordpress :

        $ mkdir wordpress

2. Créer un fichier docker-compose.yml: 

        $ nano docker-compose.yml

3. Coller le texte suivant:

        version: '2'
        
        services:
           db:
             image: mysql:5.7
             volumes:
               - db_data:/var/lib/mysql
             restart: always
             environment:
               MYSQL_ROOT_PASSWORD: somewordpress
               MYSQL_DATABASE: wordpress
               MYSQL_USER: wordpress
               MYSQL_PASSWORD: wordpress
        
           wordpress:
             depends_on:
               - db
             image: wordpress:latest
             ports:
               - "8000:80"
             restart: always
             environment:
               WORDPRESS_DB_HOST: db:3306
               WORDPRESS_DB_USER: wordpress
               WORDPRESS_DB_PASSWORD: wordpress
        volumes:
            db_data:
            
### Executez le conteneur 🖊  

1. Executez la commande suivante : 

        $ docker-compose up -d
        
