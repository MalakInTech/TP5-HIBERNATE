# Gestion des Réservations Avancées

Ce projet est une application Java développée avec **Maven**, utilisant **JPA (Hibernate)** pour la gestion de la persistance des données et **H2** comme base de données en mémoire.

Il permet d’implémenter :

- Recherche de salles disponibles par créneau
- Recherche multi-critères dynamique
- Pagination des résultats

---

# 📌 Objectif du TP

À travers ce projet, j’ai appris à :

- Créer un projet Maven et gérer ses dépendances
- Implémenter des requêtes JPQL avancées
- Utiliser la Criteria API pour des recherches dynamiques
- Mettre en place un système de pagination
- Structurer une application en couches (Repository → Service)
- Configurer et manipuler une base de données **H2 en mémoire**

---

# 🛠️ Technologies utilisées

- Java 8
- Maven
- JPA 2.2
- Hibernate 5
- H2 Database
- Hibernate Validator
- SLF4J pour les logs
- JUnit pour les tests

---

# ⚙️ Étapes principales de réalisation

## 1️⃣ Création du projet Maven

Création d’un projet Maven pour gérer automatiquement les dépendances nécessaires (Hibernate, H2, Validator, etc.) et structurer correctement l’application.

---

## 2️⃣ Configuration de Hibernate et H2

Création du fichier `persistence.xml` dans le dossier `META-INF` pour configurer la base de données H2 en mémoire.

---

## 3️⃣ Création des entités

### 👤 Utilisateur

- id
- nom
- prenom
- email
- Relation OneToMany avec Reservation

### 🏢 Salle

- id
- nom
- capacite
- description
- batiment
- etage
- Relation OneToMany avec Reservation
- Relation ManyToMany avec Equipement

### 📅 Reservation

- id
- dateDebut
- dateFin
- motif
- ManyToOne vers Utilisateur
- ManyToOne vers Salle

### 🖥️ Equipement

- id
- nom
- description
- Relation ManyToMany avec Salle

---

## 4️⃣ Implémentation du Repository

Création de `SalleRepository` avec :

- findAvailableRooms(...)
- findByCriteria(...)
- findAllPaginated(...)
- count()
- CRUD

Utilisation de :

- JPQL pour les salles disponibles
- Criteria API pour la recherche multi-critères
- setFirstResult / setMaxResults pour la pagination

---

## 5️⃣ Création de la couche Service

Création de `SalleService` :

- Gestion des transactions
- Appel des méthodes du repository
- Encapsulation de la logique métier

---

## 6️⃣ Création de la classe principale App.java

- Initialisation des données
- Test de la recherche par créneau
- Test de la recherche multi-critères
- Test de la pagination
- Affichage des résultats dans la console

---

# 📸 Screenshots de la console

### 1️⃣ Création des tables

<img width="681" height="648" alt="Capture d&#39;écran 2026-02-24 133439" src="https://github.com/user-attachments/assets/576675d7-13c2-4f61-b43d-902d67ab386a" />
<img width="572" height="502" alt="Capture d&#39;écran 2026-02-24 133450" src="https://github.com/user-attachments/assets/de34a94f-126a-4108-9860-3194c058e014" />
<img width="676" height="553" alt="Capture d&#39;écran 2026-02-24 133500" src="https://github.com/user-attachments/assets/4cf617ed-6b7a-4639-913b-6c1b5ef6f352" />
<img width="817" height="616" alt="Capture d&#39;écran 2026-02-24 133712" src="https://github.com/user-attachments/assets/2fc89bd1-854b-44a3-8d4a-33303a798e2f" />
<img width="599" height="171" alt="Capture d&#39;écran 2026-02-24 133723" src="https://github.com/user-attachments/assets/594f0fb7-7946-4712-9aa5-172a2d9e9b54" />
<img width="645" height="583" alt="Capture d&#39;écran 2026-02-24 133734" src="https://github.com/user-attachments/assets/7a95b11a-7112-4665-baa7-44f521ca96b1" />
<img width="852" height="594" alt="Capture d&#39;écran 2026-02-24 133744" src="https://github.com/user-attachments/assets/35171d4f-3a03-450a-9f2c-d68f05b0347d" />
<img width="841" height="585" alt="Capture d&#39;écran 2026-02-24 133757" src="https://github.com/user-attachments/assets/e10eae4f-e889-486b-a815-2e0d9814454a" />
<img width="825" height="578" alt="Capture d&#39;écran 2026-02-24 133815" src="https://github.com/user-attachments/assets/be645f6d-c3c8-4456-b587-dce56ab76f15" />
<img width="815" height="576" alt="Capture d&#39;écran 2026-02-24 133826" src="https://github.com/user-attachments/assets/3e5c71b6-48ae-469a-a539-d33791e8ebaa" />
<img width="726" height="586" alt="Capture d&#39;écran 2026-02-24 133843" src="https://github.com/user-attachments/assets/e7749e59-5b46-4a37-bee0-cffdf1f62b49" />
<img width="663" height="432" alt="Capture d&#39;écran 2026-02-24 134003" src="https://github.com/user-attachments/assets/19b4ea6e-5ac1-4cc4-8d2d-cbfdf8d3fa15" />

### 2️⃣ Test recherche salles disponibles par créneau

<img width="908" height="606" alt="Capture d&#39;écran 2026-02-24 134314" src="https://github.com/user-attachments/assets/46f2fcec-9f46-413d-bd88-c19d28727406" />
<img width="986" height="707" alt="Capture d&#39;écran 2026-02-24 134332" src="https://github.com/user-attachments/assets/a49fbd47-5081-4a01-b931-de6c9599aa52" />
<img width="387" height="164" alt="Capture d&#39;écran 2026-02-24 134339" src="https://github.com/user-attachments/assets/db67841e-7fc1-4ada-a365-bc8e16651627" />

### 3️⃣ Test recherche multi-critères

<img width="645" height="483" alt="Capture d&#39;écran 2026-02-24 134513" src="https://github.com/user-attachments/assets/07a818b4-c080-4fec-9885-e618d1edeaa6" />
<img width="735" height="438" alt="Capture d&#39;écran 2026-02-24 134523" src="https://github.com/user-attachments/assets/c7187745-51a2-4707-b426-e6a96d408f90" />
<img width="737" height="468" alt="Capture d&#39;écran 2026-02-24 134533" src="https://github.com/user-attachments/assets/50b98d41-948b-44ad-a814-abfc7d7320ae" />

### 4️⃣ Test pagination

<img width="740" height="663" alt="Capture d&#39;écran 2026-02-24 140243" src="https://github.com/user-attachments/assets/00c82e22-c20f-43ee-861c-551dd1c6cb33" />
<img width="710" height="440" alt="Capture d&#39;écran 2026-02-24 140252" src="https://github.com/user-attachments/assets/f36d960e-9332-426d-aa3d-65d7aa24ceb3" />
<img width="676" height="404" alt="Capture d&#39;écran 2026-02-24 140303" src="https://github.com/user-attachments/assets/9fe29171-9204-4470-af7f-ae4345282514" />
<img width="634" height="623" alt="Capture d&#39;écran 2026-02-24 140314" src="https://github.com/user-attachments/assets/8cbf08c3-d334-4b8b-a47d-09a7b8963b2b" />
<img width="461" height="215" alt="Capture d&#39;écran 2026-02-24 140323" src="https://github.com/user-attachments/assets/bb10f356-c7ee-469f-8f09-9ea97b2aa49f" />

---

# 👩‍💻 Auteur

- Nom : Malak El Mallouky
- Filière : SIR  

