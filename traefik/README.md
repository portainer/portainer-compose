# Usage

This setup comes up with the [traefik](https://github.com/containous/traefik) reverse proxy to access the Portainer instance via a virtual host.

The default configuration will make Portainer available via the `portainer.dev` domain. If you wish to change this, update the `traefik.http.routers.portainer.rule` label for the Portainer service in the `docker-compose.yml` file.

Deploy this stack on any Docker node:

```
docker-compose up -d
```

And then access Portainer by hitting [http://dev.portainer](http://dev.portainer) (or your own domain if you updated it) with a web browser.

**NOTE**: Your machine must be able to resolve `dev.portainer` (or your own domain if you updated it).
