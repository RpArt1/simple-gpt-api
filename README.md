# simple-gpt-api
#### api responsible for very basic integration with open ai and with long term memory tools like regular database
#### without vector databases


test locall endpoint: http://127.0.0.1:8000/aidevs-4.4 with curl with json body {"question": "This is question"} 

```
curl -X POST "http://localhost:8000//aidevs-4.4/" -H  "accept: application/json" -H  "Content-Type: application/json" -d "{\"question\":\"This is question\"}"
```

#### run in background
```
cd /app/simple-gpt-api && nohup uvicorn main:app --reload &
```
# copy to digital ocean
scp -i ~/.ssh/personal/digocean -r simple-gpt-api root@68.183.213.161:/app

## domain 
- create digitalocean droplet add ssh to log in - install requirements 
- copy app to droplet ( scp later to be automized)
- install nginx and add configuration 
- buy domain at porkbun ( configure its dns to your public ip -> remove existing rules and add yours 
    -  source  https://kb.porkbun.com/article/54-pointing-your-domain-to-hosting-with-a-records )
- modify nginx so server is pointing to domain name not ip 
- done 

## TLS 

source: https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-20-04

- install requ
- obtain cert: 
    ```
     sudo certbot --nginx -d aipoldev.cfd -d www.aipoldev.cfd
    ```
- nginx config is automatically re-rwitten 
- test nginx config ( mitght need to fix indent ) 
```
sudo nginx -t 
```
- restart service
```
sudo systemctl restart nginx.service
```


# Dockerise python app in digitalocean

## install doker 
source https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04


## github actions plan 

1. on push to main detect if changes were made in *.py files 
2. if so build container 
https://stackoverflow.com/questions/60477061/github-actions-how-to-deploy-to-remote-server-using-ssh