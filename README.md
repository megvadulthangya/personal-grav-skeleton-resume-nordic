
````markdown
# 👨‍💻 Gábor Gyöngyösi - IT Systems Integrator CV

![Stack](https://img.shields.io/badge/Tech-Grav%20%7C%20Docker%20%7C%20Nord-88C0D0) ![Build](https://img.shields.io/badge/build-passing-brightgreen)

This repository contains the source code for my professional resume website. It is built on **Grav CMS**, utilizing a custom-forked **Nord Theme**, and deployed via **Docker** containers.

👉 **Live Demo:** [cv.gshoots.hu](https://cv.gshoots.hu)
*(Note: The resume content itself is currently in Hungarian.)*

## 🚀 Tech Stack

This project demonstrates not just content presentation, but also **DevOps** and **Self-Hosting** competencies.

* **Engine:** [Grav CMS](https://getgrav.org) (Flat-file CMS)
* **Theme:** Custom Fork of Resume Theme (Nordic Color Palette)
* **Infrastructure:** Self-Hosted (Docker & Docker Compose)
* **Configuration:** YAML-based data management

## 🎨 Key Features

* **Nord Design:** Eye-friendly, dark "Nordic" color palette.
* **Gravatar Integration:** Dynamic profile picture generation via MD5 hash.
* **Smart Contacts:** Clickable phone (`tel:`), email (`mailto:`), and social links with proper targets.
* **Responsive:** Mobile-first approach based on the Foundation framework.

## 🛠️ Installation & Development

The project consists of two parts:
1.  **Skeleton (This repo):** Contains content (`pages`), configuration (`config`), and business logic.
2.  **Theme ([grav-theme-resume](https://github.com/megvadulthangya/grav-theme-resume)):** Contains Twig templates and CSS assets.

### Local Setup (Docker)

```bash
# Clone the repository
git clone [https://github.com/megvadulthangya/grav-skeleton-resume-site.git](https://github.com/megvadulthangya/grav-skeleton-resume-site.git)

# Start the container
docker-compose up -d
````

## 📜 Credits

  * Based on the [Resume Theme](https://github.com/getgrav/grav-theme-resume) by Fernando Báez.
  * Customized, containerized, and maintained by **Gábor Gyöngyösi**.

-----

*Copyright © 2025 Gábor Gyöngyösi*

````
