# cli-linux
1. wget https://dl.eff.org/certbot-auto	
2. chmod a+x ./certbot-auto	
3. ./certbot-auto certonly --standalone --email EMAIL_ADDRESS_HERE -d DOMAIN_HERE	
4. /home/certbot-auto certonly --webroot -w /home/ebuda.vn/ -d ebuda.vn	
5. certbot renew --pre-hook "service nginx stop" --post-hook "service nginx start"
