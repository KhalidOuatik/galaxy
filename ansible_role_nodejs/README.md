# Exercice 32 : Rôle Ansible portable pour déploiement Node.js (quiz-ansible)

**Consigne :**
Créer un rôle Ansible complet et portable permettant de déployer une application Node.js (quiz-ansible) depuis un dépôt GitHub, sur tout système Linux conteneurisé de type Debian/Ubuntu ou RedHat/Rocky Linux. Vous publierez ensuite ce rôle sur Ansible Galaxy.

**Test du rôle :**
Testez votre rôle en créant un playbook nommé `ansible-role-[nom_au_choix].yaml`.

**Inspiration :**
Inspirez-vous du script bash suivant pour créer le rôle Ansible complet et portable :

```bash
dnf update -y && \
dnf install -y git && \
curl -fsSL https://rpm.nodesource.com/setup_23.x | bash - && \
dnf install -y nodejs && \
git clone https://github.com/franklin-tutorials/quiz-ansible.git && \
cd quiz-ansible && \
npm install && \
npm run build && \
npm install -g serve && \
serve -s dist
```

**Démarche suivie pour réaliser ce rôle :**
- Création d'un rôle Ansible structuré (`tasks/`, `defaults/`, etc.)
- Détection automatique de la famille d'OS (Debian/Ubuntu ou RedHat/Rocky)
- Installation conditionnelle des dépendances système (git, curl, nodejs)
- Utilisation de modules Ansible natifs (`package`, `git`, `shell`, etc.)
- Clonage du dépôt quiz-ansible et installation des dépendances Node.js
- Build de l'application et installation de `serve` en global
- Lancement de l'application en tâche de fond sur le port 3000
- Tests sur plusieurs clients Docker Ubuntu et Rocky pour garantir la portabilité
- Correction des problèmes de persistance du process dans Docker
- Documentation et adaptation pour publication sur Ansible Galaxy

Ce rôle permet de déployer automatiquement l'application quiz-ansible sur tout environnement Linux compatible, en appliquant les bonnes pratiques Ansible vues en cours.
