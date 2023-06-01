---
alias: []
tags: []
---

# Docker
----
Stop all running containers

```bash
docker stop $(docker ps -a -q)
```
Remove all running containers

```bash
docker rm $(docker ps -a -q)
```

Remove all unused images
```bash
docker image prune -a
```

Remove all unused networks

```bash
docker network prune
```

Remove all unused volumes

```bash
docker volume prune
```
