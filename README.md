Plateforme hypermédia participative de suivi du littoral
 
Ce projet a pour objectif de créer une plateforme web hypermédia inspirée du programme CoastSnap, permettant le suivi participatif du littoralbà partir de **photos géolocalisées** envoyées par les utilisateurs.

Les citoyens peuvent déposer des **images** prises depuis des points fixes sur la côte. Ces photos sont associées à des **métadonnées** (date, lieu, auteur, coordonnées GPS) et sont **enregistrées dans une base de données**.  
Elles sont ensuite **affichées sur une carte interactive**  permettant d’observer visuellement l’évolution des sites côtiers dans le temps.

Le projet illustre une approche **hypermédia**, car il relie différents types de médias (texte, image, carte, données) et permet une **navigation non linéaire et interactive** entre les informations.



##  Objectifs du projet
- Développer une application web permettant la **collecte participative de photos** du littoral.  
- Créer une **base de données** pour stocker les utilisateurs, les images et leurs métadonnées selon le secteur , site .  
- Mettre en place une **carte interactive** pour visualiser les observations citoyennes.  
- Valoriser les **données multimédias** grâce à une représentation **RDF/Turtle** (`sosa:Observation`, `schema:ImageObject`).  
- Promouvoir la **science citoyenne** et la **sensibilisation environnementale** via les technologies du web.  



##  Public cible
- **Citoyens et touristes** souhaitant participer à l’observation du littoral.  
- **Étudiants et enseignants** utilisant la plateforme pour des projets pédagogiques.  
- **Chercheurs et collectivités locales** intéressés par l’évolution du trait de côte.  
- **Associations environnementales** œuvrant pour la protection des zones côtières.


##  Technologies utilisées
- **PHP / MySQL** : gestion des utilisateurs, stockage et traitement des données.  
- **JavaScript ** : interactions et affichage dynamique.    
- **JSON / RDF ** : échanges de données et représentation sémantique.  
- **HTML5 / CSS3 ** : structure, design et documentation.  
- **Mermaid** : création du diagramme entité–relation (ER).  

##  Données et multimédia
- **Images** : photos des côtes prises par les utilisateurs.  
- **Métadonnées** : auteur, date, heure, coordonnées GPS, commentaire, site observé.  
- **Carte interactive (Leaflet + OSM)** : affichage géographique des observations.  
- **Formats de données** : JSON (échange client/serveur) et RDF/Turtle (structuration sémantique).  
- **Médias combinés** : texte, image, géolocalisation et données.  

Ces éléments multimédias sont interconnectés et consultables par navigation interactive, démontrant la **dimension hypermédia** du projet.


##  Diagramme entité–relation

```mermaid
erDiagram
  USER {
    int id
    varchar nom
    varchar prenom
    varchar email
    datetime created_at "date d'entrée"
  }

  SECTOR {
    int id
    varchar code
    varchar name
  }

  PHOTO {
    int id
    int user_id
    int sector_id
    varchar file_path
    varchar location_name
    decimal latitude
    decimal longitude
    datetime date_taken
    datetime uploaded_at
  }

  OBSERVATION {
    int id
    int photo_id
    decimal hauteur_eau "hauteur d'eau en mètres"
    varchar unite
    text commentaire
    datetime created_at
  }

  USER ||--o{ PHOTO : "envoie"
  SECTOR ||--o{ PHOTO : "localise"
  PHOTO ||--o{ OBSERVATION : "associe une mesure"









