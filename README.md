
![image](https://github.com/user-attachments/assets/fde0d0a5-b100-4bd6-92fc-12f21ab5ab0e)


# Mise en Place d’un Système de Ticketing Open-Source :

---

**Zammad** est une solution open-source de gestion de support client, permettant de centraliser et de traiter efficacement les demandes des utilisateurs. Accessible via une interface web moderne, elle intègre divers canaux de communication tels que l’email, le chat, le téléphone et les réseaux sociaux. Zammad offre des fonctionnalités puissantes pour suivre, prioriser et résoudre les tickets, tout en améliorant la collaboration au sein des équipes de support. Sa flexibilité et sa nature open-source en font un outil idéal pour les petites et grandes entreprises.

---

### **1) Configuration du Système**

Avant de commencer l’installation, il est important de s’assurer que la machine répond aux exigences minimales de Zammad :
- **RAM** : 2 Go
- **CPU** : 2 vCPUs
- **Espace disque** : 100 Go

---

### **2) On va Créer le Répertoire et Cloner le Dépôt GitHub**

On a bien démarré en créant un répertoire  projet, et ensuite en clonant le dépôt officiel de Zammad via GitHub :

```bash
mkdir ZAMMAD
cd ZAMMAD
git clone https://github.com/zammad/zammad-docker-compose.git
```

Une fois dans le répertoire, il est recommandé de vérifier les fichiers disponibles avec un `ls` .

---

### **3) Configuration des Variables d'Environnement**

Dans cette étape, il faut modifier les variables d'environnement pour configurer la base de données .


```bash
POSTGRES_PASS=xxxxxxxxxxxxxxxx
```

---

### **4) Modifier le Fichier `docker-compose.yml`**

Dans le fichier `docker-compose.yml`, On peux ajuster des configurations comme le fuseau horaire :

```bash
TZ: "${TZ:-Europe/Paris}"
```


Après modification, n'oublie pas de sauvegarder les modifications.

---

### **5) Pull des Images Docker**

Ensuite, il est nécessaire de télécharger les images Docker qui vont constituer l'environnement Zammad :

```bash
docker compose pull
```

Cela va récupérer toutes les images nécessaires pour ton environnement.

---

### **6) Démarrage de Docker Compose**

On peut maintenant démarrer les containers Docker avec la commande suivante :

```bash
docker compose up
```

Cela va lancer tous les services nécessaires à Zammad, y compris la base de données et les services associés.

---

### **7) Accès à l'Interface Web**

Une fois que le système Docker est en cours d'exécution, On peut accéder à l’interface web de Zammad en ouvrant un navigateur et en te rendant à l'URL appropriée.

---

### **8) Gestion des Rôles**

Zammad propose trois types de rôles principaux :

1. **Admin** : L’administrateur a un accès complet à toutes les fonctionnalités, permettant de configurer, gérer et administrer l’outil.
2. **Agent** : Un agent de support peut répondre aux tickets, mais n'a pas nécessairement accès à la configuration globale du système.
3. **Utilisateur final** : L'utilisateur qui soumet un ticket via les différents canaux (email, chat, etc.).

On peut configurer ces rôles en fonction des utilisateurs qu'on va ajouter dans ton environnement Zammad.

---
Voir la documentation pdf admin-docs-zammad-org.pdf pour personnaliser l'outils.
---

Ce déploiement est réalisé en local par Ousmane KA, dans les mêmes conditions reproductibles en environnement de production.
