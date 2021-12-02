# nap-api-demo

## Introduction
NGINX App Protect combines the proven effectiveness of F5's advanced WAF technology with the agility and performance of NGINX Plus. Read more [here](https://www.nginx.com/products/nginx-app-protect/web-application-firewall)

The purpose of this repo is to provoide and easy setup for learning and demonstration NGINX NAP to protect against API endpoints

You may also want to check out [NGINX NAP Demo](https://github.com/mcheo-nginx/nap-demo) and [NGINX NAP DoS Demo](https://github.com/mcheo-nginx/nap-dos-demo) separately.
<br/>


# Setup

0. Build NAP Docker image</br>
Follow the instruction in the official doc to build a local docker container app-protect image. https://docs.nginx.com/nginx-app-protect/admin-guide/install/#docker-deployment


1. Clone the repo
```
git clone https://github.com/mcheo-nginx/nap-api-demo.git
cd nap-api-demo
```

Assuming you already have NGINX App Protect built as docker container in your machine.


2. Step up the stacks
```
docker-compose -f docker-compose.yml up -d
```

The stack consists of 3 containers:
- NGINX App Protect instance
- Backend app server (httpbin)
- Elasticsearch for NAP dashboard


3. Complete Elasticsearch setup</br>
Use browser to visit http://localhost:5601, once the page loads successfully which means startup has completed, execute the following steps:
```
sh import_kibana_dashboard.sh
```
<br/>


# Testing
Use the browser to visit http://localhost:8000 for protected API and http://localhost:8001 for unprotected API.

There are some samples NAP policies in /etc/nginx/policies/, update the nginx.conf to point to the right policy before nginx -s reload.


<br/>

# Dashboard
Visit http://localhost:5601 and click into Discover or Dashboard to see the traffics/violations.

Please refer here for extra [reference](https://devcentral.f5.com/s/articles/Dashboards-for-NGINX-App-Protect)

<br/>
