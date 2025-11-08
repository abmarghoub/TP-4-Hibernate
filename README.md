#  TP 4 : Hibernate

---

## Réalisé par

**Abla MARGHOUB**

## Encadré par

**Pr. Mohamed LACHGAR**

## Module

**Techniques de Programmation Avancée**

## Établissement

**École Normale Supérieure - Université Cadi Ayyad**

---
## 1. Objectifs du TP
L’objectif de ce TP est de configurer et développer une application Java basée sur Hibernate et MySQL afin de gérer la persistance des entités dans une base de données relationnelle.  
L’application met en œuvre :
- Le mapping objet-relationnel via JPA/Hibernate.  
- La gestion des entités Salle et Machine.  
- L’utilisation des **services DAO** pour effectuer les opérations CRUD.  
- La validation des fonctionnalités à l’aide de **tests unitaires JUnit**.

---

## 2. Architecture technique

### 2.1 Stack technologique
| Composant | Technologie utilisée |
|------------|----------------------|
| Langage | Java |
| ORM | Hibernate (JPA) |
| Base de données | MySQL |
| Gestionnaire de dépendances | Maven |
| Framework de test | JUnit |
| IDE conseillé | IntelliJ IDEA / Eclipse |

###  2.2 Structure du TP
<img width="432" height="833" alt="0" src="https://github.com/user-attachments/assets/3645df28-4906-457f-b006-5caf5765c34c" />

##  3. Base de données

###  3.1 Configuration de la base de données
La configuration Hibernate (dans `hibernate.cfg.xml`) permet de connecter l’application à une base MySQL locale.

<img width="710" height="743" alt="image" src="https://github.com/user-attachments/assets/f7ecd6eb-feac-4ac5-a415-09382b1e29db" />

### 3.2 Entités principales

<img width="439" height="242" alt="6" src="https://github.com/user-attachments/assets/e74a308d-36c0-4ad5-b68e-b9330dd1ca71" />

#### Classe Salle

<img width="547" height="405" alt="4" src="https://github.com/user-attachments/assets/f683b353-5b04-490f-a859-e80df9279702" />

#### Classe Machine

<img width="545" height="441" alt="5" src="https://github.com/user-attachments/assets/270dcd51-c344-4f61-8012-bc241b7a33a2" />

## 4. Description des interfaces et classes

| Élément                                   | Type              | Description                                                                                   |
| ----------------------------------------- | ----------------- | --------------------------------------------------------------------------------------------- |
| **IDao<T>**                               | Interface         | Définit les opérations CRUD génériques : `create`, `delete`, `update`, `findById`, `findAll`. |
| **Salle**                                 | Entité JPA        | Représente une salle contenant plusieurs machines.                                            |
| **Machine**                               | Entité JPA        | Représente une machine avec une date d’achat et une référence.                                |
| **SalleService**                          | Classe Service    | Implémente les opérations CRUD pour `Salle`.                                                  |
| **MachineService**                        | Classe Service    | Implémente les opérations CRUD et la recherche par date pour `Machine`.                       |
| **HibernateUtil**                         | Classe utilitaire | Gère la création et la configuration de la `SessionFactory`.                                  |
| **Test.java**                             | Classe de test    | Permet de tester la création et l’affichage des entités.                                      |
| **SalleServiceTest / MachineServiceTest** | Test JUnit        | Valident le bon fonctionnement des opérations CRUD.                                           |

 ## 5. Fonctionnement global

**Initialisation de la SessionFactory**
La classe HibernateUtil lit le fichier hibernate.cfg.xml et configure la connexion à MySQL.

**Création des entités**
Les classes Salle et Machine sont mappées en tables dans la base de données à l’aide des annotations JPA.

**Persistance des données**
Les services (SalleService, MachineService) utilisent des sessions Hibernate pour exécuter les opérations CRUD :
- save() pour insérer,
- update() pour modifier,
- delete() pour supprimer,
- get() ou createQuery() pour récupérer.

**Tests unitaires**
Les classes de test (SalleServiceTest, MachineServiceTest) vérifient :
- la création d’entités,
- la mise à jour,
- la suppression,
- la recherche simple et entre deux dates (pour Machine).

## 6. Résultats attendus
**Classe de test (Test.java)**
<img width="765" height="764" alt="1" src="https://github.com/user-attachments/assets/d237858c-e8df-4c3c-b55c-4db3968ba63d" />

**Classe de test (MachineServiceTest.java)**

<img width="721" height="764" alt="2" src="https://github.com/user-attachments/assets/504d7be3-e95d-4af2-af6a-eae1b1b48f1e" />

**Classe de test (SalleServiceTest.java)**

<img width="770" height="737" alt="3" src="https://github.com/user-attachments/assets/4d727f02-52e8-4974-aee9-7f0f1f88ca21" />
