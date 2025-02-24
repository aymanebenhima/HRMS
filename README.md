### **Conception et développement pour un HRMS** 

#### **Contexte du Projet**  
L'objectif est de développer un module **HRMS (Human Resource Management System)** pour permettre aux entreprises de gérer efficacement leurs employés, départements, et hiérarchies. Le développement sera réalisé sous **Laravel 11** en suivant les bonnes pratiques et en utilisant des packages adaptés pour simplifier la gestion des rôles, des documents, des présences, et des notifications.

#### **Technologies et Outils**  
- **Framework** : Laravel 11 💻  
- **Base de données** : MySQL / PostgreSQL 🗄️  
- **Frontend** : Blade + Tailwind CSS 🎨  
- **Authentification** : Laravel Breeze / Jetstream 🔑  
- **Packages recommandés** :
  - **Spatie Laravel Permissions** : Gestion des rôles et permissions des utilisateurs 🛡️  
  - **Yajra Datatables** : Gestion avancée des tableaux de données (optionnel) 📊  
  - **Laravel Excel** : Importation/exportation de données 📥  
  - **Livewire** : Composants dynamiques sans rechargement de page 🔄  
  - **Laravel Media Library** : Gestion des fichiers et documents 📂  
  - **Laravel Notifications** : Alertes et notifications pour événements RH 🔔
  - **Laravel Excel :** Importation/exportation de données 📥

---

### **Brief Part I : Gestion des Utilisateurs et Entreprises, Gestion des Employés, Départements et Hiérarchie**  
**Durée estimée : 5 jours** ⏳

#### **Objectifs**  
1. **Gestion des utilisateurs et des entreprises** : Permettre à chaque entreprise de créer un compte et de gérer ses utilisateurs.  
2. **Gestion des employés avec rôles multiples** : Associer des rôles variés aux utilisateurs pour une gestion flexible.  
3. **Gestion des départements et hiérarchie** : Structurer les employés dans des départements et définir les relations hiérarchiques.

#### **Détails Techniques**

1. **Gestion des Utilisateurs et Entreprises**  
   - **Création d'un compte entreprise** : Une entreprise peut s’inscrire, se connecter et gérer ses employés 🏢.  
   - **Authentification** : Implémenter un système de connexion sécurisé (via **Laravel Breeze** ou **Jetstream**) pour les administrateurs et managers 🔐.  
   - **Gestion des rôles et permissions** : Utiliser **Spatie Laravel Permissions** pour gérer les rôles comme **Admin**, **Manager**, **Employé**. Chaque rôle aura des permissions spécifiques 👥.  
   - **Gestion des profils utilisateurs** : Permettre aux utilisateurs de compléter et modifier leur profil (photo, email, téléphone, etc.) 👤.

2. **Gestion des Employés**  
   - **Création et mise à jour des profils des employés** : Les administrateurs peuvent ajouter, modifier, ou supprimer les employés dans le système, avec des informations comme le nom, prénom, date de naissance, et coordonnées 📋.  
   - **Suivi de carrière** : Implémenter des fonctionnalités pour suivre les évolutions professionnelles des employés, telles que les augmentations de salaire, promotions, et formations 🎓.  
   - **Gestion des contrats** : Ajouter des types de contrats (CDI, CDD, Stage, Freelance) et stocker les documents associés via **Laravel Media Library** 📂.

3. **Gestion des Départements et Hiérarchie**  
   - **Création de départements** : Permettre de créer et gérer les départements d'une entreprise 🌐.  
   - **Hiérarchie des employés** : Associer les employés à un département et définir des relations hiérarchiques entre eux 👔.  
   - **Affichage dynamique** : Utiliser un organigramme pour visualiser la hiérarchie des employés, avec possibilité d’interactions (drag-and-drop, etc.) 🏗️.

#### **Technologies et outils**  
- **Laravel 11**, **Spatie Laravel Permissions**, **Laravel Media Library**, **Yajra Datatables** (optionnel), **Tailwind CSS**, **Livewire**

---
### **Détails des Entités et Fonctionnalités Requises pour un HRMS**

#### **1. Gestion des Utilisateurs et des Entreprises**  
##### **Entités**
- **Entreprise** 🏢 : Une entité représentant l'entreprise.
  - **Attributs** : Nom de l’entreprise, secteur d’activité, adresse, logo, email de contact, numéro de téléphone, date d'inscription.
  - **Relation** : Une entreprise peut avoir plusieurs employés et utilisateurs.
  
- **Utilisateur** 👤 : Représente un utilisateur dans le système.
  - **Attributs** : Nom, prénom, email, mot de passe, photo de profil, téléphone, rôle (Admin, Manager, Employé), entreprise_id (clé étrangère), statut (actif/inactif).
  - **Relation** : Un utilisateur appartient à une entreprise et peut avoir un ou plusieurs rôles via **Spatie Laravel Permissions**.

##### **Fonctionnalités**
- **Création d'un compte entreprise** :
  - Une entreprise peut s’inscrire avec des informations de base (nom, email, mot de passe) via un formulaire d'inscription.
  - Validation des données (email, téléphone, etc.).
  
- **Authentification (Laravel Breeze/Jetstream)** :
  - Intégration du système de connexion sécurisé avec **email** et **mot de passe**.
  - Authentification par **sessions**.
  - Possibilité d’enregistrer les utilisateurs via un formulaire.
  
- **Gestion des rôles et permissions** :
  - Chaque utilisateur peut avoir un ou plusieurs rôles via **Spatie Laravel Permissions** : 
    - **Admin** : Peut gérer tous les aspects de l'entreprise.
    - **HR** : Peut gérer tous les employés et les managers.
    - **Manager** : Peut gérer les employés et sa propre département.
    - **Employé** : Accès limité à ses informations et certaines actions.
  
- **Gestion des profils utilisateurs** :
  - Les utilisateurs peuvent mettre à jour leur photo de profil, email, téléphone et autres informations personnelles.
  - Intégration de **Laravel Media Library** pour gérer la photo de profil et d’autres documents associés.

---

#### **2. Gestion des Employés**  
##### **Entités**
- **Employé** 👥 : Représente un employé au sein d'une entreprise.
  - **Attributs** : Nom, prénom, email, téléphone, date de naissance, adresse, date de recrutement, type de contrat, salaire, statut.
  - **Relation** : Un employé appartient à un département et peut avoir des informations associées comme le suivi de carrière et les documents.

##### **Fonctionnalités**
- **Création et mise à jour des profils des employés** :
  - Les administrateurs peuvent ajouter, modifier ou supprimer des employés.
  - Chaque employé aura une fiche avec des informations de base : nom, prénom, email, téléphone, date de naissance, etc.
  
- **Suivi de carrière** 🎓 :
  - Ajouter des fonctionnalités pour suivre les évolutions des employés :
    - **Augmentations salariales** : Historique des augmentations et modifications salariales.
    - **Promotions** : Historique des promotions au sein de l’entreprise.
    - **Formations** : Suivi des formations suivies par l’employé (date, type de formation, certification).
  
- **Gestion des contrats** 📂 :
  - Types de contrats : CDI, CDD, Freelance, Stage, etc.
  - **Documents associés** : Stockage des contrats via **Laravel Media Library**, avec possibilité de télécharger et consulter les contrats, fiches de paie, etc.

---

#### **3. Gestion des Départements et Hiérarchie**  
##### **Entités**
- **Département** 🌐 : Représente un département au sein de l’entreprise.
  - **Attributs** : Nom du département, description, responsable, date de création.
  - **Relation** : Un département peut avoir plusieurs employés associés à lui.

- **Hiérarchie** 👔 : Relation entre les employés pour définir la structure de l'entreprise.
  - **Attributs** : Employé_id, manager_id (clé étrangère), position hiérarchique, date d’ajout dans la hiérarchie.
  - **Relation** : Un employé peut être un manager pour plusieurs autres employés.

##### **Fonctionnalités**
- **Création de départements** :
  - Permettre aux administrateurs de créer, mettre à jour et supprimer des départements.
  - Chaque département peut avoir un responsable et plusieurs employés.

- **Hiérarchie des employés** :
  - Chaque employé sera associé à un ou plusieurs départements.
  - Les administrateurs ou managers peuvent définir la hiérarchie des employés via des relations de gestion (un employé peut être le responsable d’autres employés).
  
- **Affichage dynamique (Organigramme)** 🏗️ :
  - Utilisation de **Livewire** pour créer une interface interactive permettant de visualiser et d’éditer l’organigramme de l'entreprise.
  - Les utilisateurs peuvent réorganiser l’organigramme (drag-and-drop) pour ajuster les relations hiérarchiques.

---

### **Résumé des Fonctions Clés à Développer**
- **Authentification sécurisée** : Système de gestion des utilisateurs avec différents rôles (Admin, HR, Manager, Employé).
- **Gestion des employés** : Ajouter, modifier, supprimer les employés, et suivre leur carrière (promotions, augmentations).
- **Gestion des départements et hiérarchie** : Organiser les employés dans des départements et définir les relations hiérarchiques.
- **Affichage dynamique de l'organigramme** : Visualisation interactive et modifiable de la structure de l'entreprise.

---

### **Bonnes Pratiques et Modalités Pédagogiques**

#### **Bonnes Pratiques :**

- Utiliser des Form Requests pour valider les données utilisateur avant soumission ✅.
- Sécuriser les accès avec des middleware pour restreindre certaines actions 🔒.
- Gérer les relations entre entités via Eloquent ORM pour des requêtes efficaces 🧠.
- Implémenter Soft Delete pour éviter la suppression permanente des employés 🗑️.
- Utiliser des Seeders et Factories pour générer des données de test 💡.

#### **Modalités Pédagogiques :**

- *Travail :* Individuel 👨‍💻
- *Durée estimée :* 5 jours ⏳
- *Objectif :* Développer un module complet de gestion des employés tout en respectant les bonnes pratiques Laravel et l'architecture du système HRMS.
- Date de lancement du brief : 24/02/2025 à 09:15
- Date limite de soumission: 28/02/2025 avant 05:30 PM
