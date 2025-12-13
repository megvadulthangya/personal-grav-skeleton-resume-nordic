# 👨‍💻 megvadulthangya - IT Systems Integrator CV

![Stack](https://img.shields.io/badge/Tech-Grav%20%7C%20Docker%20%7C%20LinuxServer-88C0D0) ![Build](https://img.shields.io/badge/build-passing-brightgreen)

This repository contains the source code (skeleton) for my professional resume website. It is built on **Grav CMS**, utilizing a custom-forked **Nord Theme**, and deployed via **Docker** using bind mounts.

👉 **Live Demo:** [cv.gshoots.hu](https://cv.gshoots.hu)

## 🚀 Tech Stack

* **Engine:** [Grav CMS](https://getgrav.org)
* **Image:** [LinuxServer.io Grav](https://docs.linuxserver.io/images/docker-grav/)
* **Theme:** Custom Fork of Resume Theme (Nordic Color Palette)
* **Infrastructure:** Docker Compose with Bind Mounts

## ⚡ Quick Start (Copy-Paste)

This guide assumes you want to run the site from `/docker/grav-resume`.
Just follow these exact steps to get it running.

### 1. Create the Docker Compose File
Create a `docker-compose.yml` file in your project folder with the following **exact content**:

```yaml
services:
  grav:
    image: lscr.io/linuxserver/grav:latest
    container_name: grav-resume
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Etc/UTC
    volumes:
      # HOST PATH : CONTAINER PATH
      - /docker/grav-resume/config:/config
      - /docker/grav-resume/app:/app
    ports:
      - 80:80
    restart: unless-stopped
````

### 2\. Deploy Content (Run in Terminal)

Run these commands to create the directories, clone the source, and inject the files into the Docker bind mount.

```bash
# 1. Create the base directory structure for the bind mount
sudo mkdir -p /docker/grav-resume/app/www/user/themes
sudo mkdir -p /docker/grav-resume/app/www/user/pages
sudo mkdir -p /docker/grav-resume/config

# 2. Clone the repositories to a temporary location
git clone [https://github.com/megvadulthangya/grav-skeleton-resume-site.git](https://github.com/megvadulthangya/grav-skeleton-resume-site.git) /tmp/skeleton
git clone [https://github.com/megvadulthangya/grav-theme-resume.git](https://github.com/megvadulthangya/grav-theme-resume.git) /tmp/theme

# 3. Copy THEME to the bind mount
sudo cp -r /tmp/theme /docker/grav-resume/app/www/user/themes/resume

# 4. Copy CONTENT (Pages) to the bind mount
# (Removes default pages first to avoid conflicts)
sudo rm -rf /docker/grav-resume/app/www/user/pages/*
sudo cp -r /tmp/skeleton/pages/* /docker/grav-resume/app/www/user/pages/

# 5. Copy CONFIG to the bind mount
sudo cp -r /tmp/skeleton/config/* /docker/grav-resume/app/www/user/config/

# 6. Cleanup
rm -rf /tmp/skeleton /tmp/theme
```

### 3\. Start the Server

```bash
docker-compose up -d
```

Your site is now live at `http://localhost`.

-----

*📝 **Note:** The configuration above uses `/docker/grav-resume` as the host directory. If you prefer a different location, simply update the paths in the `docker-compose.yml` volumes section and the bash commands accordingly.*

## 📂 Repository Structure

  * `/config`: Site configuration (system.yaml, site.yaml, security.yaml).
  * `/pages`: The actual content of the CV (Markdown files).

## 📜 Credits

  * Based on the [Resume Theme](https://github.com/getgrav/grav-theme-resume) by Fernando Báez.
  * Customized, containerized, and maintained by **megvadulthangya**.

-----

*Copyright © 2025 megvadulthangya*
