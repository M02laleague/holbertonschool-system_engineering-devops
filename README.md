# Web Infrastructure Design

Ce projet consiste à concevoir des architectures web pour des sites internet, en passant d'une infrastructure simple à une infrastructure évolutive, sécurisée et surveillée.

## **Objectifs**
- Comprendre les concepts fondamentaux des infrastructures web.
- Identifier et corriger les points de défaillance unique (*SPOF*).
- Apprendre à sécuriser et surveiller une infrastructure.
- Concevoir une infrastructure capable de gérer une charge croissante.

---

## **Tâches**

### **0. Simple Web Stack**
- **Description** : Infrastructure de base avec un seul serveur.
- **Composants** :
  - 1 serveur avec un serveur web (Nginx), un serveur d'application, une base de données (MySQL).
  - Un domaine `www.foobar.com` configuré avec un enregistrement DNS (A record).
- **Problèmes identifiés** :
  - Point de défaillance unique (SPOF).
  - Temps d'arrêt lors de la maintenance.
  - Incapacité de gérer une charge importante.
- **Fichier** : [0-simple_web_stack](./0-simple_web_stack)

---

### **1. Distributed Web Infrastructure**
- **Description** : Infrastructure distribuée avec plusieurs serveurs et un équilibrage de charge.
- **Composants** :
  - 1 Load Balancer (HAProxy).
  - 2 serveurs web (Nginx).
  - 2 serveurs d'application.
  - Cluster de bases de données (Primary-Replica).
- **Problèmes identifiés** :
  - Points de défaillance unique restants (load balancer, base primaire).
  - Aucune sécurité (pare-feu, HTTPS).
  - Pas de surveillance (monitoring).
- **Fichier** : [1-distributed_web_infrastructure](./1-distributed_web_infrastructure)

---

### **2. Secured and Monitored Web Infrastructure**
- **Description** : Ajout de fonctionnalités de sécurité et de surveillance.
- **Composants** :
  - 3 Pare-feux pour protéger les couches réseau, applicative et base de données.
  - 1 Certificat SSL/TLS pour activer HTTPS.
  - 3 clients de monitoring pour collecter les métriques.
- **Problèmes identifiés** :
  - SSL terminé au niveau de l'équilibreur de charge.
  - Une seule base primaire reste un SPOF pour les écritures.
- **Fichier** : [2-secured_and_monitored_web_infrastructure](./2-secured_and_monitored_web_infrastructure)

---

### **3. Scale Up**
- **Description** : Séparation des composants sur des machines dédiées pour une meilleure évolutivité.
- **Composants** :
  - 2 Load Balancers en cluster (HAProxy).
  - Serveurs web et serveurs d'application distincts.
  - Cluster de bases de données (Primary-Replica).
- **Problèmes identifiés** :
  - Complexité accrue due à la gestion des composants supplémentaires.
  - SPOF dans les couches qui ne sont pas redondantes.
- **Fichier** : [3-scale_up](./3-scale_up)

---

## **Concepts clés**

### **1. Composants de base**
- **Serveur** : Machine physique ou virtuelle hébergeant des services web.
- **Serveur Web (Nginx)** : Sert les contenus statiques (HTML, CSS, JS) et redirige les requêtes vers le serveur d'application.
- **Serveur d'application** : Exécute la logique métier (PHP, Python, etc.).
- **Base de données** : Stocke les données de l'application.

### **2. DNS et Enregistrements**
- **DNS (Domain Name System)** : Traduction des noms de domaine en adresses IP.
- **A Record** : Associe un domaine à une adresse IPv4.
- **CNAME Record** : Crée un alias vers un autre domaine.

### **3. Sécurité et Monitoring**
- **Pare-feu** : Protège les serveurs contre les accès non autorisés.
- **SSL/TLS** : Chiffre les communications entre le client et le serveur.
- **Monitoring** : Collecte des données sur les performances des composants.

---

## **Comment utiliser ce projet**
1. Clonez le dépôt GitHub :
   ```bash
   git clone https://github.com/M02laleague/holbertonschool-system_engineering-devops.git
   cd holbertonschool-system_engineering-devops/web_infrastructure_design
