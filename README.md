# 👨‍💻 megvadulthangya - IT Systems Integrator CV

![Stack](https://img.shields.io/badge/Tech-Grav%20%7C%20Docker%20%7C%20LinuxServer-88C0D0) ![Build](https://img.shields.io/badge/build-passing-brightgreen)

This repository contains the source code (skeleton) for my professional resume website. It is built on **Grav CMS**, utilizing a custom-forked **Nord Theme**, and deployed via **Docker**.

👉 **Live Demo:** [cv.gshoots.hu](https://cv.gshoots.hu)
*(Note: The resume content itself is currently in Hungarian.)*

## 🚀 Tech Stack

This project demonstrates **DevOps** and **Self-Hosting** competencies by separating code, configuration, and infrastructure.

* **Engine:** [Grav CMS](https://getgrav.org) (Flat-file CMS)
* **Image:** [LinuxServer.io Grav](https://docs.linuxserver.io/images/docker-grav/)
* **Theme:** Custom Fork of Resume Theme (Nordic Color Palette)
* **Infrastructure:** Docker Compose

## 🎨 Key Features

* **Nord Design:** Eye-friendly, dark "Nordic" color palette.
* **Gravatar Integration:** Dynamic profile picture generation via MD5 hash.
* **Smart Contacts:** Clickable phone (`tel:`), email (`mailto:`), and social links.
* **Responsive:** Mobile-first approach based on the Foundation framework.

## 🛠️ Installation & Setup

To replicate this setup, you need to inject the content and theme into a standard Grav installation.

### 1. Clone Repositories

First, clone the content (skeleton) and the design (theme) to your local machine:

```bash
# 1. Clone the Skeleton (Content & Config)
git clone [https://github.com/megvadulthangya/grav-skeleton-resume-site.git](https://github.com/megvadulthangya/grav-skeleton-resume-site.git)

# 2. Clone the Theme (Design)
git clone [https://github.com/megvadulthangya/grav-theme-resume.git](https://github.com/megvadulthangya/grav-theme-resume.git)
````

### 2\. Copy Files to Grav

Assuming you have a running Grav instance (or a mounted volume), copy the files to the standard `user` directory structure:

  * **Theme:** Copy the `grav-theme-resume` folder into `user/themes/resume`.
  * **Content:** Copy the `pages` folder from the skeleton into `user/pages`.
  * **Config:** Copy the `config` folder from the skeleton into `user/config`.

### 3\. Docker Quick Start

Use this standard `docker-compose.yml` to spin up the environment. Ensure your volume mounts point to the data where you copied the files above.

```yaml
services:
  grav:
    image: lscr.io/linuxserver/grav:latest
    container_name: grav
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Etc/UTC
    volumes:
      - ./grav-data:/config  # Maps to the configuration directory
      - ./grav-app:/app      # Maps to the application root
    ports:
      - 80:80
    restart: unless-stopped
```

## 📂 Repository Structure

  * `/config`: Site configuration (system.yaml, site.yaml, security.yaml).
  * `/pages`: The actual content of the CV (Markdown files).

## 📜 Credits

  * Based on the [Resume Theme](https://github.com/getgrav/grav-theme-resume) by Fernando Báez.
  * Customized, containerized, and maintained by **megvadulthangya**.

-----

*Copyright © 2025 megvadulthangya*
