<div align="center">

# 🐉 Kali Linux Docker GUI

[![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/)
[![Kali Linux](https://img.shields.io/badge/Kali_Linux-557C94?style=for-the-badge&logo=kali-linux&logoColor=white)](https://www.kali.org/)
[![KasmVNC](https://img.shields.io/badge/KasmVNC-FF6B35?style=for-the-badge&logo=vnc&logoColor=white)](https://kasmweb.com/kasmvnc)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)

**🇫🇷 Français** | [🇬🇧 English](#-english-version)

</div>

---

> [!WARNING]
> **DISCLAIMER** — Le fichier `docker-compose.yml` a été généré via **Claude Sonnet 4.6** (Anthropic).
> Ce projet est destiné à un usage éducatif et légal uniquement. Toute utilisation malveillante est strictement interdite.

---

## 📋 Prérequis

- [Docker Desktop](https://www.docker.com/products/docker-desktop/) installé et lancé
- Un navigateur **Chrome ou Edge** (recommandé pour le copier-coller seamless)

---

## 🚀 Installation

### 1. Télécharger le dossier `kali-gui` depuis GitHub et extraire le dossier

### 2. Ouvrir un terminal et accéder au dossier `kali-gui`

```bash
cd /chemin/vers/kali-gui
```

### 3. Configurer le mot de passe dans le fichier `.env`

```bash
# Éditer le fichier .env
VNC_PW=Changeme!   # ← remplacer par ton mot de passe
```

### 4. Créer le dossier partagé

```bash
mkdir -p shared
```

---

## ▶️ Lancer le conteneur

```bash
# Démarrer en arrière-plan
docker compose up -d
```

Puis ouvrir dans le navigateur :

```
https://localhost:6901
```

> [!NOTE]
> Accepter l'avertissement de certificat auto-signé dans le navigateur.

Le bureau Kali Linux (XFCE) doit apparaître après authentification :

```
Utilisateur : kasm_user
Mot de passe : (valeur de VNC_PW dans .env)
```

---

## 📋 Copier-Coller

| Navigateur | Comportement |
|------------|-------------|
| **Chrome / Edge** | Seamless — fonctionne directement comme en local |
| **Firefox** | Cliquer sur l'icône presse-papier 📋 en haut à gauche de l'interface |

---

## ⌨️ Commandes essentielles

### Gestion du conteneur

| Commande | Description |
|----------|-------------|
| `docker compose up -d` | Démarrer le conteneur |
| `docker compose down` | Arrêter le conteneur |
| `docker compose down -v` | Arrêter le conteneur et supprimer les volumes |
| `docker rm -f kali-gui` | Supprimer le conteneur de force |
| `docker rm kali-gui` | Supprimer le conteneur (arrêté uniquement) |

### Accès shell direct (sans GUI)

| Commande | Description |
|----------|-------------|
| `docker exec -it kali-gui bash` | Ouvrir un shell dans le conteneur |
| `docker logs kali-gui` | Voir les logs du conteneur |
| `exit` | Quitter le shell |

---

## 🛠️ Post-déploiement

```bash
# Ouvrir un shell dans le conteneur
docker exec -it kali-gui bash

# Mettre à jour les paquets
apt update && apt upgrade -y

# Installer les 10 outils essentiels Kali
apt install -y kali-tools-top10

# Ou des outils spécifiques
apt install -y nmap metasploit-framework burpsuite wireshark
```

---

## 📁 Structure du projet

```
kali_gui/
├── docker-compose.yml   # Configuration Docker
├── .env                 # Mot de passe VNC (ne pas commiter)
├── .gitignore           # Exclut .env et shared/
├── shared/              # Dossier partagé hôte ↔ conteneur
└── README.md
```

---
---

## 🇬🇧 English Version

<div align="center">

**[🇫🇷 Français](#-prérequis)** | 🇬🇧 English

</div>

---

> [!WARNING]
> **DISCLAIMER** — The `docker-compose.yml` file was generated using **Claude Sonnet 4.6** (Anthropic).
> This project is intended for educational and legal use only. Any malicious use is strictly prohibited.

---

## 📋 Requirements

- [Docker Desktop](https://www.docker.com/products/docker-desktop/) installed and running
- A **Chrome or Edge** browser (recommended for seamless clipboard support)

---

## 🚀 Installation

### 1. Download the `kali-gui` folder from GitHub and extract it

### 2. Open a terminal and navigate to the `kali-gui` folder

```bash
cd /path/to/kali-gui
```

### 3. Set your password in the `.env` file

```bash
# Edit the .env file
VNC_PW=Changeme!   # ← replace with your password
```

### 4. Create the shared folder

```bash
mkdir -p shared
```

---

## ▶️ Start the container

```bash
# Start in background
docker compose up -d
```

Then open your browser at:

```
https://localhost:6901
```

> [!NOTE]
> Accept the self-signed certificate warning in your browser.

The Kali Linux desktop (XFCE) will appear after authentication:

```
Username : kasm_user
Password : (value of VNC_PW in .env)
```

---

## 📋 Copy-Paste

| Browser | Behavior |
|---------|----------|
| **Chrome / Edge** | Seamless — works directly like a local desktop |
| **Firefox** | Click the clipboard icon 📋 in the top-left of the interface |

---

## ⌨️ Essential commands

### Container management

| Command | Description |
|---------|-------------|
| `docker compose up -d` | Start the container |
| `docker compose down` | Stop the container |
| `docker compose down -v` | Stop the container and delete volumes |
| `docker rm -f kali-gui` | Force delete the container |
| `docker rm kali-gui` | Delete the container (stopped only) |

### Direct shell access (without GUI)

| Command | Description |
|---------|-------------|
| `docker exec -it kali-gui bash` | Open a shell inside the container |
| `docker logs kali-gui` | View container logs |
| `exit` | Exit the shell |

---

## 🛠️ Post-deployment

```bash
# Open a shell inside the container
docker exec -it kali-gui bash

# Update packages
apt update && apt upgrade -y

# Install Kali's top 10 essential tools
apt install -y kali-tools-top10

# Or install specific tools
apt install -y nmap metasploit-framework burpsuite wireshark
```

---

## 📁 Project structure

```
kali_gui/
├── docker-compose.yml   # Docker configuration
├── .env                 # VNC password (do not commit)
├── .gitignore           # Excludes .env and shared/
├── shared/              # Shared folder host ↔ container
└── README.md
```

---

<div align="center">

Made with ❤️ — Powered by [Kali Linux](https://www.kali.org/) & [Docker](https://www.docker.com/)

</div>
