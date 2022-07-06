`su root`

`apt update`
`apt upgrade`

`apt install sudo`

 ### Commande installation docker : https://docs.docker.com/engine/install/debian/#install-using-the-repository


`mkdir /home/mail`

`docker run \
    --net=host \
    -e TZ=Europe/Prague \
    -v /your-data-dir/data:/data \
    --name "mailserver" \
    -h "mail.example.com" \
    -e "HTTP_PORT=8080" \
    -e "HTTPS_PORT=4433" \
    -t analogic/poste.io`

Pour désactiver l'anti virus et l'anti spam :
	`-e "DISABLE_RSPAMD=TRUE"`
	`-e "DISABLE_CLAMAV=TRUE"`


Démarré, arrêter le container :
	`docker start mailserver`
	`docker stop mailserver`


 ### Installation nginx :

`apt update`

`apt install nginx`

`sudo systemctl status nginx`

`sudo systemctl enable nginx`

`sudo nginx -v`



`cd /etc/nginx/sites-available/`
`nano mail`

`Contenue du fichier "Conf nginx"`

`ln -s /etc/nginx/sites-available/mail /etc/nginx/sites-enabled/`

`nginx -s reload`

 ### Installation CertBot :

`apt install snapd`

`sudo snap install core; sudo snap refresh core`

`sudo snap install --classic certbot`

`sudo ln -s /snap/bin/certbot /usr/bin/certbot`

`sudo certbot --nginx`

 ### Tache Cron :

`crontab -e`

`@reboot docker start mailserver`

 ### Si problèmes :

`netstat -nlp | grep 25`

> SOURCE : https://poste.io/
> https://docs.docker.com/engine/install/debian/#install-using-the-repository
> https://certbot.eff.org/


