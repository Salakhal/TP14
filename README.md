# TP 14 : CRUD avec DAO Générique

## Exercice 1 : CRUD Complet avec DAO Générique

 ## Objectif du TP
Mettre en place une architecture en couches pour gérer des entités métier à l’aide d’un **DAO générique**, permettant d’effectuer toutes les opérations **CRUD** (Create, Read, Update, Delete).

 ##  La Structure du projet
 ```
src/
└─ ma/projet/
   ├─ bean/
   │   ├ Identifiable.java
   │   ├ Profile.java
   │   └ Utilisateur.java
   │
   ├─ dao/
   │   ├ Dao.java
   │   └ ListDao.java
   │
   ├─ service/
   │   ├ ProfileService.java
   │   └ UserService.java
   │
   └─ TestApp.java

```


---

##  Description des couches

###  1. Couche **Bean (Modèle)**
Contient les entités principales :
- **Profile** : représente un rôle (ex : Manager, Chef de projet).
- **Utilisateur** : représente un utilisateur lié à un profil.
- **Identifiable** : interface commune avec la méthode `getId()`.

Chaque entité gère son propre identifiant **auto-incrémenté** via un compteur statique.

---

###  2. Couche **DAO (Data Access Object)**
Responsable de la **gestion des données**.  
L’interface `Dao<T>` définit les opérations génériques suivantes :

```java
void create(T obj);
T update(T obj);
boolean delete(int id);
T findById(int id);
List<T> findAll();

```
## Exemple de sortie :

 ```
Profils : [Profile{id=1, code='MN', description='Manager'}, Profile{id=2, code='CP', description='Chef de projet'}]
Users   : [Utilisateur{id=1, login='youssef', password='pwd1', profile=MN}, Utilisateur{id=2, login='fatima', password='pwd2', profile=CP}, Utilisateur{id=3, login='omar', password='pwd3', profile=MN}]

Managers :
Utilisateur{id=3, login='omar', password='pwd3', profile=MN}

```

<img width="1873" height="188" alt="image" src="https://github.com/user-attachments/assets/8b6ad699-074d-4400-b595-5ca7e18c3506" />

