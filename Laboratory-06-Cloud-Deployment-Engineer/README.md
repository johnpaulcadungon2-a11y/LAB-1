# Laboratory 06: The Cloud Deployment Engineer

**Course Activity:** Midterm Laboratory Exam, Mission 6
**Environment:** KillerCoda Ubuntu Playground
**Tools:** Docker, Docker Compose, nano, GitHub

---

## Mission Overview

CloudNova Technologies asked me to build a proof-of-concept private cloud storage service for a university. I deployed **Nextcloud** (web tier) and **MariaDB** (database tier) as a two-tier stack. Instead of typing a separate command for each container, I described the entire setup in a `docker-compose.yml` file and started it with one command, which is a practical example of **Infrastructure as Code (IaC)**.

## Objectives

- [x] Explain multi-tier application architecture
- [x] Understand the structure and purpose of `docker-compose.yml`
- [x] Create configuration files with the nano editor
- [x] Deploy a multi-container app with Docker Compose
- [x] Document the work in Markdown
- [x] Grow my GitHub Cloud Computing Portfolio

## Commands Executed

| # | Command | What it did |
|---|---|---|
| 1 | `mkdir nextcloud-deployment` | Created the project folder |
| 2 | `cd nextcloud-deployment` | Moved into the folder |
| 3 | `nano docker-compose.yml` | Opened the editor to write the Compose file |
| 4 | `cat docker-compose.yml` | Checked that the file was saved correctly |
| 5 | `docker-compose up -d` | Pulled images and started both containers in the background |
| 6 | `docker-compose ps` | Confirmed both containers were running |
| 7 | `docker-compose down` | Stopped and removed the containers and network |

## Evidence

**Deployment and running containers**
![compose-deployment](screenshots/compose-deployment.png)

**Nextcloud setup page (port 8080)**
![nextcloud-web](screenshots/nextcloud-web.png)

**Teardown**
![compose-teardown](screenshots/compose-teardown.png)

## Skills Learned

- Reading and writing YAML with correct spacing
- Using nano to create and save files in Linux
- Launching and removing a full stack with Docker Compose
- Connecting containers by service name and environment variables
- Mapping a container port to the host and opening it in a browser
- Writing technical documentation in Markdown and organizing it in GitHub

## Repository Contents

| File | Description |
|---|---|
| [multi-tier-architecture.md](multi-tier-architecture.md) | Two-tier architecture explained |
| [docker-compose-guide.md](docker-compose-guide.md) | Walkthrough of the Compose file |
| [reflection.md](reflection.md) | Personal mission reflection |
| `screenshots/` | Deployment, web, and teardown evidence |
