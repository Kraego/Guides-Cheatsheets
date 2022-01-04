# How to handle Certbot with apache (on debian)

Scenario: Using apache as reverse proxy for bitwarden, nextcloud, ... on debian.

1. Create multiplexing Rule under:
```/etc/apache2/sites-enabled``` (without ssl stuff)
2. Restart apache:
```
sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 start
```
4. Generate lets'encrypt cert
```sudo certbot certonly --cert-name service.myDomain.eu -d service.myDomain.eu```
5. Run certbot to create apache entries in multiplexing rule file.
6. Restart apache again:
```
sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 start
```
