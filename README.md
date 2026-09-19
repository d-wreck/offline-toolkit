# Offline Toolkit
Just a collection of useful containers I use day-to-day.
## [Cyberchef](https://github.com/gchq/CyberChef)
Swiss army knife I started using during my SecOps days. Favorites:
- From Base64
- URL Defang
- DNS over HTTPS; Still works even though the base container is network isolated. Container serves the static HTML/JSS/CSS files to your browser and then the recipe executes in your browser's JavaScript engine (not in the container).
- Find / Replace
## [IT-Tools](https://github.com/CorentinTh/it-tools)
Bunch of useful tools. Favorites:
- Outlook Safelink decoder; super useful in Microsoft environments
- Crontab generator; good for testing cron schedules, wih a handy cheat sheet and examples too.
- Regex Tester + Cheatsheet

## [Draw.io](https://www.drawio.com/docs/security/diagrams-docker-app/)
Great for quick diagrams locally

## Container Setup

Setup containers

```podman compose up -d```

Testing a container network is isolated

```podman exec cyberchef curl -m 5 -v https://google.com```

Access the containers via browser (adjust ports based on your yml file)
```
http://localhost:8080
http://localhost:9090
```

Periodically run updates of the images to get the latest
```
podman compose pull
podman compose up -d
```

Remove containers
```
podman compose down
```

### Enabling Auto Start Service for containers on system boot (optional)

1. First SSH into the podman machine
`podman machine ssh`
2. Enable restart service (choose 1):
    - Rootless Mode (Default for Podman):
    `sudo systemctl --global enable podman-restart.service`
    - Rootful Mode:
    `sudo systemctl enable podman-restart.service`