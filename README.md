# 👨‍💻 megvadulthangya - IT Systems Integrator CV

![Stack](https://img.shields.io/badge/Tech-Grav%20%7C%20Docker%20%7C%20LinuxServer-88C0D0) ![Build](https://img.shields.io/badge/build-passing-brightgreen)

This repository contains the source code (skeleton) for my professional resume website. It is built on **Grav CMS**, utilizing a custom-forked **Nord Theme**, and deployed via **Docker** with a custom Nginx configuration.

👉 **Live Demo:** [cv.gshoots.hu](https://cv.gshoots.hu)
*(Note: The resume content itself is currently in Hungarian.)*

## 🚀 Tech Stack

This project demonstrates **DevOps** and **Self-Hosting** competencies by separating code, configuration, and infrastructure.

* **Engine:** [Grav CMS](https://getgrav.org) (Flat-file CMS)
* **Image:** [LinuxServer.io Grav](https://docs.linuxserver.io/images/docker-grav/)
* **Theme:** Custom Fork of Resume Theme (Nordic Color Palette)
* **Web Server:** Nginx (Custom configuration)
* **Infrastructure:** Docker Compose with Bind Mounts

## 🎨 Key Features

* **Nord Design:** Eye-friendly, dark "Nordic" color palette.
* **Gravatar Integration:** Dynamic profile picture generation via MD5 hash.
* **Smart Contacts:** Clickable phone (`tel:`), email (`mailto:`), and social links.
* **Responsive:** Mobile-first approach based on the Foundation framework.

## 🛠️ Infrastructure & Deployment

The project consists of three parts:
1.  **Skeleton (This repo):** Contains content (`pages`), configuration (`config`), and business logic.
2.  **Theme ([grav-theme-resume](https://github.com/megvadulthangya/grav-theme-resume)):** Contains Twig templates and CSS assets.
3.  **Host Server:** Docker environment running the application.

### 🔧 Server Configuration

The system uses **bind mounts** to inject the application code from the host directly into the container. This allows for persistent storage and easy updates without rebuilding images.

```yaml
# docker-compose.yml snippet
services:
  grav:
    image: lscr.io/linuxserver/grav:latest
    container_name: grav
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Etc/UTC
    volumes:
      # Custom Nginx & PHP config persistence
      - /docker/grav/appdata/config:/config
      # Application Logic (Mapped to Host)
      - /docker/grav/app:/app
    ports:
      - 80:80
    restart: unless-stopped
````

### 🔄 Deployment Workflow

The deployment strategy relies on copying updated files from the local Git repositories directly into the **bind-mounted directories** on the host server.

**Workflow Logic:**

1.  **Source Update:** Pull the latest changes from the Git repositories (Skeleton & Theme).
2.  **File Injection:** Copy the updated `pages`, `config`, and `theme` files into the host directory that is mounted to `/app` inside the container.
3.  **Cache Purge:** Manually clear the Grav cache to apply changes immediately without restarting the container.

## 📂 Repository Structure

  * `/config`: Site configuration (system.yaml, site.yaml, security.yaml).
  * `/pages`: The actual content of the CV (Markdown files).
  * `deploy.sh`: Automation script for syncing Git content to the Docker volume.

## 📜 Credits

  * Based on the [Resume Theme](https://github.com/getgrav/grav-theme-resume) by Fernando Báez.
  * Customized, containerized, and maintained by **megvadulthangya**.

-----

*Copyright © 2025 megvadulthangya*
