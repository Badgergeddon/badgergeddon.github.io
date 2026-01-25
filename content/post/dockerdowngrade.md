---
title: "Emergency Docker Downgrade"
description: "Emergency Docker Downgrade"
date: 2026-01-25
tags: [docker,howto]
categories: [software,docker]
---

Docker update screws up [Casaos](https://casaos.zimaspace.com/) or some other application on your server and you need a quick Docker Downgrade?

I had the same issue and just downgraded docker back to 28.5.2 and it instantly fixed the issue.

Here are the steps if you need them for ubuntu:

1. Stop Docker

```shell
sudo systemctl stop docker
```

2. Install the specific Docker version

```shell
sudo apt install docker-ce=5:28.5.2-1~ubuntu.24.04~noble \
                 docker-ce-cli=5:28.5.2-1~ubuntu.24.04~noble \
                 containerd.io
```

3. Prevent Ubuntu from automatically upgrading Docker:

```shell
sudo apt-mark hold docker-ce docker-ce-cli
```

4. Start Docker again

```shell
sudo systemctl start docker
sudo systemctl enable docker
```

5. Verify the version

```shell
docker --version
```

You should see:

Docker version 28.5.2, build ...

Once this issue has been fixed you can run the following to update docker back

```shell
sudo apt-mark unhold docker-ce docker-ce-cli
```