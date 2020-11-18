# Usage

This setup comes up with the [Traefik](https://github.com/containous/traefik) v2.3 reverse proxy to access the Portainer instance via a virtual host, has support for SSL certificates using Let's Encrypt and automatic redirection from http to https.

The default configuration will make Portainer frontend available via the `portainer.yourdomain.com` domain. If you wish to change this, update the `traefik.http.routers.frontend.rule=Host(`portainer.yourdomain.com`)` label for the Portainer service in the `docker-compose.yml` file.

## Edge agent

The edge agent was created as a way to manage an edge compute environment where devices typically lack the networking capability to run the traditional Portainer agent.

Portainer communicates with the edge agent over port 8000; through this port the edge agent can poll the Portainer instance, connect to Portainer, see when it is needed & initiate a tunnel or receive config updates.

This example configuration uses Traefik to route the edge agent connections on HTTPS:443 and TCP:8000 to Portainer service.

If you're going to use Edge agents. When you set up the endpoint from Portainer Configuration, you need to change the Portainer Server URL setting to match with the label specified for Edge. In this sample, the URLs specified for the Edge service is `edge.yourdomain.com` and needs to be set in for these routers in the docker-compose.yml:

```
      - "traefik.http.routers.frontend.rule=Host(`portainer.yourdomain.com`)"
      - "traefik.tcp.routers.edgeagent.rule=Host(`edge.yourdomain.com`)"
```
   

![Edge](/traefik/edge.png)

Deploy this stack on any Docker node:

```
docker-compose up -d
```

And then access Portainer by hitting [http://portainer.yourdomain.com](http://portainer.yourdomain.com) with a web browser.

**NOTE**: Your machine must be able to resolve `portainer.yourdomain.com` (or your own domain if you updated it).
