# ansible-role-app-web

![Ansible Galaxy](https://img.shields.io/badge/Ansible--Galaxy-sofl4me.app_web-blue?style=flat-square&logo=ansible)

## Description

Ce rôle Ansible installe et déploie une application Node.js (quiz-ansible) avec [PM2](https://pm2.keymetrics.io/) sur des systèmes Ubuntu ou Rocky Linux.

Il permet :

- L'installation de Node.js via les scripts officiels de NodeSource
- Le clonage du dépôt Git contenant l'application
- L'installation des dépendances `npm`
- Le lancement de l'application avec `pm2`
- Une compatibilité multiplateforme Ubuntu / Rocky

---

## Prérequis

- Ansible >= 2.10
- Accès root (sudo) sur les machines cibles
- Git installé sur la machine de contrôle
- L'application `quiz-ansible` doit être publiquement accessible sur GitHub

---

## Plateformes supportées

- Ubuntu 20.04 / 22.04
- Rocky Linux 8 / 9

---

## Rôle inclus

- Mise à jour des paquets
- Suppression de `curl-minimal` (Rocky uniquement)
- Installation des paquets requis
- Téléchargement et exécution du script Node.js (via NodeSource)
- Installation de Node.js, npm, et PM2
- Clonage et installation de l'application `quiz-ansible`
- Compilation et lancement avec PM2

---

## Variables

Les variables par défaut sont situées dans `defaults/main.yml`.

| Variable                        | Description                                               | Valeur par défaut                                      |
|--------------------------------|-----------------------------------------------------------|--------------------------------------------------------|
| `node_setup_script_url_ubuntu` | URL du script Node.js pour Ubuntu                        | `"https://deb.nodesource.com/setup_23.x"`             |
| `node_setup_script_url_rocky`  | URL du script Node.js pour Rocky Linux                   | `"https://rpm.nodesource.com/setup_23.x"`             |
| `app_directory`                | Répertoire d'installation de l'application               | `"/opt/quiz-ansible"`                                 |

---

## Exemple d'utilisation

```yaml
- name: Déployer l'application quiz-ansible
  hosts: all
  become: true

  roles:
    - role: sofl4me.app_web





---------------------------------------------

roles/
└── ansible-role-app-web/
    ├── defaults/
    │   └── main.yml
    ├── tasks/
    │   ├── main.yml
    │   ├── majpack.yml
    │   ├── installnode.yml
    │   ├── installnmp.yml
    │   ├── installpm2.yml
    │   ├── dlexu.yml / dlexr.yml
    │   └── ...
    └── meta/
        └── main.yml


----------------------------------------


Sofl4me
Projet réalisé dans le cadre d’un exercice DevOps utilisant Ansible Galaxy.