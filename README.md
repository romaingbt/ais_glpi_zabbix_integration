# ais_glpi_zabbix_integration
Projet AIS - Déploiement GLPI sous Docker et interconnexion Zabbix.
# 🛠️ Déploiement de GLPI sous Docker et Interconnexion avec Zabbix

## 📋 Présentation du projet
Ce projet réalisé dans le cadre de ma formation **AIS (Administrateur d'Infrastructures Sécurisées)** consiste à mettre en place une solution centralisée de gestion de parc informatique et de support (ITSM) combinée à de la supervision proactive.

L'objectif est d'automatiser la remontée des alertes de supervision (Zabbix) directement sous forme de tickets d'incidents dans l'outil de gestion de parc (GLPI) via une API.

## 🏗️ Architecture & Environnement technique
* **Moyens utilisés :** Machines virtuelles sous Debian 13 (hébergées sous Proxmox / VMware Workstation).
* **Technologies :** Docker, Docker Compose, MariaDB, GLPI, Zabbix.
* **Contexte d'exercice :** Projet technique / Lab (Réalisé en décembre 2025).

## ⚙️ Étapes de mise en œuvre

1. **Déploiement de GLPI avec Docker Compose :**
   * Création d'un fichier `docker-compose.yml` isolant le service applicatif GLPI et sa base de données MariaDB.
   * Utilisation de volumes persistants pour conserver les configurations, fichiers et plugins.

2. **Sécurisation et Inventaire :**
   * Création d'un compte de service dédié (`zabbix`) pour cloisonner les accès et limiter les privilèges.
   * Installation des agents GLPI sur les machines clientes et intégration pour la remontée automatique du matériel et des logiciels.

3. **Interconnexion Zabbix ➡️ GLPI :**
   * Activation de l'API REST dans GLPI et génération d'un token d'accès sécurisé.
   * Configuration d'un type de média personnalisé de type "Webhook" dans Zabbix pour faire le pont.
   * Résultat : Lorsqu'un équipement tombe ou qu'un seuil critique est atteint, Zabbix génère automatiquement un ticket d'incident qualifié dans GLPI.

---
📁 *Retrouvez le fichier de configuration `docker-compose.yml` associé dans ce même dépôt.*
