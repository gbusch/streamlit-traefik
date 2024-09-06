# Streamlit and Traefik

Starts Traefik and a Streamlit Dashboard in Docker.

Traefik get's an SSL certificate from let's encrypt.

The dashboard is reachable under https://<<YOUR DOMAIN>>/dashboard (the path prefix can be changed in `traefik.yml`) without any weird ports and with a proper certificate (first request was a default-Traefik certificate, but in the background a proper let's encrypt certificate was requested).

Other streamlit or other services can be added to docker-compose and then be routed by Traefik.

Steps for configuration:
* Copy `traefik/traefik.yml.example` to `traefik/traefik.yml`.
* Replace <<YOUR EMAIL>> and <<YOUR DOMAIN>> accordingly.
* If you want basic out, uncomment the respective lines and create a `.htpasswd-users` file with `htpasswd -c .htpasswd-users <<FIRST USER>>`. However I was not happy, since streamlit always requested to enter the password twice. Maybe auth is better handled within streamlit itself.

References: 
* https://github.com/joeychrys/streamlit_deployment
* https://doc.traefik.io/traefik/https/acme/
* https://letsencrypt.org/docs/rate-limits/
* https://crt.sh
