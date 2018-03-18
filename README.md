# Easy setup for private Docker repository with Let's Encrypt SSL, Steps:
Make sure you have a domain name, ssh access.


### this works well under a DigitalOcean's ubuntu with Docker and docker-compose installed
use my DigitalOcean referal: :) 

https://m.do.co/c/66153854bc56


## Steps

1. in `docker-compose.yml` set the **REGISTRY_USER, REGISTRY_PASSWORD and DOMAIN** on the nginx args. (tip. avoid `=` on values)
2. on `ssl_gen` set **DOMAIN** value with your domain.
2. `docker-compose up -d`
3. `chmod +x *.sh`
4. `./ssl_gen.sh`  
4. if it succeeds > `docker-compose restart`

## after it succeeds:
1. from your local machine (or another) add your repo url to the `insecure-registries` (instructions: https://docs.docker.com/registry/insecure/)
2. docker login my-repo-url.com give your user name/pass
3. it should say `Login Succeeded`

# automatic cron setup
this will schedule every 15 days a renewal of the ssl cert. with Let's Encrypt.
1. `crontab -u $USER -e`
2. `0 0 */15 * *  /path/to/registry_files/ssl_renew.sh`

### need to install Docker in your VPS machine?
https://docs.docker.com/install/linux/docker-ce/ubuntu/

https://docs.docker.com/compose/install/

#
### Be sure to donate to **letsencrypt.org** !


