# Système de Vote Électronique Sécurisé

Ce projet implémente un système de vote électronique utilisant le chiffrement homomorphe de Paillier. Il comprend un serveur, un client de vote et une interface administrateur.

Réalisé en Collaboration avec d'autres étudiants de la Licence Informatique et Vidéoludisme de Paris 8

## Prérequis

- Python 3.8 ou supérieur
- pip (gestionnaire de paquets Python)

## Installation

1. Clonez le répertoire du projet :
```bash
git clone https://code.up8.edu/rchaffray/projet_securite.git
cd projet_securite
```

2. Installez les dépendances requises :
```bash
pip install pycryptodome customtkinter
```

## Configuration de la base de données

1. Initialisez la base de données avec les utilisateurs par défaut :
```bash
python bdd.py
```

Cela créera une base de données SQLite avec les utilisateurs suivants :
- Admin (mot de passe : ADMIN)
- celyan (mot de passe : celyan)
- julien (mot de passe : julien)
- romaric (mot de passe : romaric)
- lia (mot de passe : lia)
- sami (mot de passe : sami)
- aleksandar (mot de passe : aleksandar)

## Lancement du système

1. Démarrez le serveur :
```bash
python serveur.py
```
- Une fenêtre de configuration s'ouvrira
- Par défaut, l'hôte est '127.0.0.1' et le port est '8000'
- Cliquez sur "Lancer" pour démarrer le serveur

2. Lancez l'interface administrateur :
```bash
python admin.py
```
- Connectez-vous avec les identifiants admin
- L'administrateur peut ajouter/supprimer des électeurs et gérer le vote

3. Lancez le client de vote :
```bash
python client_protocole.py
```
- Connectez-vous avec l'un des comptes utilisateur
- Attendez que l'administrateur démarre le vote

## Processus de vote

1. L'administrateur :
   - Se connecte à l'interface admin
   - Entre son mot de passe admin
   - Clique sur "Commencer vote" pour démarrer l'élection
   - Peut consulter la liste des électeurs
   - Termine le vote avec "Arrêter le vote"

2. Les électeurs :
   - Se connectent avec leurs identifiants
   - Attendent le début du vote
   - Choisissent entre le candidat Rouge ou Bleu
   - Reçoivent une confirmation de leur vote
   - Voient les résultats à la fin du scrutin

## Structure des fichiers

- `serveur.py` : Serveur principal
- `admin.py` : Interface administrateur
- `client_protocole.py` : Client de vote
- `bdd.py` : Gestion de la base de données
- `paillier.py` : Implémentation du chiffrement
- `malicieu.py` : Client de test pour la sécurité

## Notes de sécurité

- Les mots de passe sont hashés avec SHA-256
- Les votes sont chiffrés avec l'algorithme de Paillier
- Seul l'administrateur peut voir les résultats déchiffrés
- Un utilisateur ne peut voter qu'une seule fois

## Dépannage

1. Si le serveur ne démarre pas :
   - Vérifiez qu'aucun autre processus n'utilise le port
   - Assurez-vous que la base de données existe

2. Si la connexion échoue :
   - Vérifiez que le serveur est en cours d'exécution
   - Confirmez que les identifiants sont corrects
   - Assurez-vous que l'adresse IP et le port sont corrects

3. En cas d'erreur de base de données :
   - Supprimez le fichier database.db
   - Réexécutez bdd.py pour réinitialiser la base de données
