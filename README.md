<div align="center">
  <a href="https://blent.ai">
    <img src="https://blent-static-media.s3.eu-west-3.amazonaws.com/images/logo/logo_blent_300x.png" alt="Logo Blent.ai" width="200" />
  </a>

  <h2 align="center">Tarification électrique basée sur la consommation</h2>

  <p align="center">
    Projet Data Engineering - <a href="https://blent.ai">Blent.ai</a>
    <br />
    <a href="https://blent.ai/app/projects" target="_blank"><strong>Explorer tous les projets »</strong></a>
</div>

<div align="center"><img src="https://cdn.static-media.blent.ai/images/projects/badge_lightning.svg" width="120" alt="Badge du projet" /></div>

## À propos du projet

Une entreprise fournisseuse d'énergie souhaite acquérir de nouveaux clients depuis son site Internet.

Pour cela, l'entreprise cherche à proposer un formulaire gratuit en ligne permettant à chaque utilisateur visitant le site Web d'évaluer rapidement et simplement sa consommation.

- La consommation électrique moyenne de la région au cours des 30 derniers jours.
- La consommation moyenne annuelle dans la ville de résidence de l'utilisateur.
- Le tarif réglementé du kWh (actuellement à 0,1558€).
- La superficie du logement (appartement ou maison) en m2.
- Les usages de l’électricité (chauffage, eau chaude, cuisson).
- Le nombre de personnes (minimum 1, maximum 10).
- Les champs du formulaire permettent de calculer le modèle de tarification suivant.
- 
$$\text{Prix}=(0.1558 + \alpha M) x +C$$

Les détails de la formule de tarification se trouvent dans la notice technique (dossier `data/`).

> TODO : Compléter cette partie pour apporter plus d'informations sur le contexte du projet.

## Étapes du projet

- [ ] Sélectionner une base de données cible pour historiser les consommations énergétiques
- [ ] Automatiser le processus de récolte et de transformation de données journalières de la consommation électrique moyenne
- [ ] Déployer le service de calcul sur un serveur ou dans un service serverless
- [ ] Réaliser des tests unitaires et fournir un benchmark sur l'efficacité technique du service de tarification
- [ ] Construire un diagramme d'architecture associé au projet
- [ ] Présenter dans un document une estimation des coûts mensuels et par requête
- [ ] Écrire un guide (fichier README) expliquant les codes du projet et permettant de prendre en main rapidement le projet à partir du dépôt Git

La description des étapes est disponible sur la page associée au projet.

> TODO : Cocher les cases au fur et à mesure de l'avancement.

## Structure du projet

Le dépôt Git contient les éléments suivantes.

- `notebooks/` contient les Notebooks Jupyter du projet.
- `src/` contient les codes sources Python principaux du projet.
- `data/` contient les données du projet.
- `config/` contient les configurations et paramètres du projet.
- `LICENSE.txt` : licence du projet.
- `requirements.txt` : liste des dépendances Python nécessaires.
- `README.md` : fichier d'accueil.

## Premiers pas

Les instructions suivantes permettent d'exécuter le projet sur son PC.

### Pré-requis

Le projet nécessite Python 3 d'installé sur le système.

> TODO : Ne pas hésiter à compléter/adapter cette partie en fonction des dépendances logicielles.

### Installation

1. Cloner le projet Git.
	```
	git clone https://github.com/blent-ai/Projet-Data-Engineering-Pipeline-MongoDB.git
	```
2. Installer les dépendances du fichier `requirements.txt` dans un environnement virtuel.

	**Linux / MacOS**
	```
	python3 -m venv venv/
	source venv/bin/activate
	pip install -r requirements.txt
	```
	**Windows**
	```
	python3 -m venv venv/
	C:\<chemin_dossir>\venv\Scripts\activate.bat
	pip install -r requirements.txt
	```

> TODO :
> - Remplir le fichier `requirements.txt` pour y ajouter les dépendances (Pandas, PyMongo, Airflow, etc).
> - Compléter la procédure d'installation pour l'adapter en fonction des besoins (MongoDB, base SQL).

### Démarrage

> TODO : Expliquer en quelques lignes et avec des exemples de ligne de commande comment l'utilisateur peut entraîner ou utiliser lui-même le modèle. 

## Licence

*Ce projet est proposé par <a href="https://blent.ai">Blent.ai</a>. Les données utilisées pour ce projet peuvent être soumises à des droits d'auteur et de propriété intellectuelle. Blent.ai ne peut être responsable des utilisations faites des données utilisées dans le cadre de ce projet.*

> TODO : Ajouter les licences supplémentaires au projet (autres données, outils propriétaires, etc).
