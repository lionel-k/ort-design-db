# Design de base de données

## Setup

Pour concevoir les schémas de base de données, nous utiliserons [WWW SQL Designer](https://ondras.zarovi.cz/sql/demo//).

## Exercice 1: Création d'une base de données d'une application de sondage

### 1.1 Nous allons construire un sytème basique avec une seule table `polls` qui contient les informations suivantes:

- `id` (int) - identifiant unique de l'enregistrement
- `title` (string) - titre du sondage
- `description` (string) - description du sondage
- `created_at` (datetime) - date de création du sondage
- `updated_at` (datetime) - date de mise à jour du sondage

Un sondage peut avoir plusieurs questions, mais une question ne peut appartenir qu'à un seul sondage.

### 1.2 Ajoutons des utilisateurs à notre application. Nous allons créer une table `users` qui contient les informations suivantes:

- `id` (int) - identifiant unique de l'enregistrement
- `name` (string) - nom de l'utilisateur
- `email` (string) - email de l'utilisateur
- `created_at` (datetime) - date de création de l'utilisateur
- `updated_at` (datetime) - date de mise à jour de l'utilisateur

Un sondage appartient à un utilisateur. Un utilisateur peut créer plusieurs sondages.

### 1.3 Ajoutons des questions à notre application. Nous allons créer une table `questions` qui contient les informations suivantes:

- `id` (int) - identifiant unique de l'enregistrement
- `title` (string) - titre de la question
- `description` (string) - description de la question
- `created_at` (datetime) - date de création de la question
- `updated_at` (datetime) - date de mise à jour de la question

Une question appartient à un sondage. Un sondage peut avoir plusieurs questions. Une question peut avoir plusieurs réponses.

### 1.4 Ajoutons des réponses à notre application. Nous allons créer une table `answers` qui contient les informations suivantes:

- `id` (int) - identifiant unique de l'enregistrement
- `title` (string) - titre de la réponse
- `description` (string) - description de la réponse
- `created_at` (datetime) - date de création de la réponse
- `updated_at` (datetime) - date de mise à jour de la réponse

Une réponse appartient à une question. Une question peut avoir plusieurs réponses. Une réponse peut avoir plusieurs votes.

### 1.5 Ajoutons des votes à notre application. Nous allons créer une table `votes` qui contient les informations suivantes:

- `id` (int) - identifiant unique de l'enregistrement
- `created_at` (datetime) - date de création du vote
- `updated_at` (datetime) - date de mise à jour du vote

Un vote appartient à une réponse. Une réponse peut avoir plusieurs votes. Un vote appartient à un utilisateur. Un utilisateur peut avoir plusieurs votes.

### 1.6 Créons les relations entre les tables

- Un sondage appartient à un utilisateur
- Un sondage peut avoir plusieurs questions
- Une question peut avoir plusieurs réponses
- Une réponse peut avoir plusieurs votes
- Un vote appartient à une réponse
- Un vote appartient à un utilisateur

### 1.7. Quand un utilisateur répond à une question, il ne peut choisir qu’une seule réponse. Comment pouvez-vous implémenter cela dans votre base de données?

Ex: Pour un sondage: "Les capitales du monde", à la question: "Quelle est la capitale de la France ?", nous avons les réponses: "Paris", "Bruxelles", "Amsterdam". Nous voulons faire sorte qu'un utilisateur qu'une seule réponse à la question.

## Exercice 2: Création d'une base de données d'une application de gestion de tâches comme Trello

### 2.1 Nous allons construire un sytème basique avec une seule table `boards` qui contient les informations suivantes:

- `id` (int) - identifiant unique de l'enregistrement
- `title` (string) - titre du tableau
- `description` (string) - description du tableau
- `created_at` (datetime) - date de création du tableau
- `updated_at` (datetime) - date de mise à jour du tableau

### 2.2 Ajoutons des utilisateurs à notre application. Nous allons créer une table `users` qui contient les informations suivantes:

- `id` (int) - identifiant unique de l'enregistrement
- `name` (string) - nom de l'utilisateur
- `email` (string) - email de l'utilisateur
- `created_at` (datetime) - date de création de l'utilisateur
- `updated_at` (datetime) - date de mise à jour de l'utilisateur

Un tableau appartient à un utilisateur. Un utilisateur peut créer plusieurs tableaux.

### 2.3 Ajoutons des listes à notre application. Nous allons créer une table `lists` qui contient les informations suivantes:

- `id` (int) - identifiant unique de l'enregistrement
- `title` (string) - titre de la liste
- `description` (string) - description de la liste
- `created_at` (datetime) - date de création de la liste
- `updated_at` (datetime) - date de mise à jour de la liste

Une liste appartient à un tableau. Un tableau peut avoir plusieurs listes. Une liste peut avoir plusieurs tâches. Une tâche ne peut appartenir qu'à une seule liste. Un utilisateur peut créer plusieurs listes. Une liste appartient à un utilisateur. Un utilisateur peut créer plusieurs listes.

### 2.4 Ajoutons des tâches à notre application. Une tâche peut être liée à une autre tâche. Par exemple, une tâche peut être une sous-tâche d'une autre tâche. Nous allons créer une table `tasks` qui contient les informations suivantes.

- `id` (int) - identifiant unique de l'enregistrement
- `title` (string) - titre de la tâche
- `description` (string) - description de la tâche
- `created_at` (datetime) - date de création de la tâche
- `updated_at` (datetime) - date de mise à jour de la tâche

Une tâche appartient à une liste. Une liste peut avoir plusieurs tâches. Une tâche peut avoir plusieurs utilisateurs. Un utilisateur peut avoir plusieurs tâches. Une tâche peut avoir plusieurs commentaires. Un commentaire ne peut appartenir qu'à une seule tâche. Une tâche peut avoir plusieurs pièces jointes. Une pièce jointe ne peut appartenir qu'à une seule tâche.

### 2.5 Ajoutons des commentaires à notre application. Nous allons créer une table `comments` qui contient les informations suivantes:

- `id` (int) - identifiant unique de l'enregistrement
- `content` (string) - contenu du commentaire
- `created_at` (datetime) - date de création du commentaire
- `updated_at` (datetime) - date de mise à jour du commentaire

Un commentaire appartient à un utilisateur. Un utilisateur peut créer plusieurs commentaires. Un commentaire appartient à une tâche. Une tâche peut avoir plusieurs commentaires.

### 2.6 Ajoutons des pièces jointes à notre application. Nous allons créer une table `attachments` qui contient les informations suivantes:

- `id` (int) - identifiant unique de l'enregistrement
- `name` (string) - nom de la pièce jointe
- `path` (string) - chemin de la pièce jointe
- `created_at` (datetime) - date de création de la pièce jointe
- `updated_at` (datetime) - date de mise à jour de la pièce jointe

Une pièce jointe appartient à un utilisateur. Un utilisateur peut créer plusieurs pièces jointes. Une pièce jointe appartient à une tâche. Une tâche peut avoir plusieurs pièces jointes.

## 2.7. Créons les relations entre les tables de notre base de données

- Un tableau appartient à un utilisateur
- Un utilisateur peut créer plusieurs tableaux
- Une liste appartient à un tableau
- Un tableau peut avoir plusieurs listes
- Une liste peut avoir plusieurs tâches
- Une tâche ne peut appartenir qu'à une seule liste
- Un utilisateur peut créer plusieurs listes
- Une liste appartient à un utilisateur
- Une tâche appartient à une liste
- Une tâche peut avoir plusieurs utilisateurs
- Un utilisateur peut avoir plusieurs tâches
- Une tâche peut avoir plusieurs commentaires
- Un commentaire ne peut appartenir qu'à une seule tâche
- Une tâche peut avoir plusieurs pièces jointes
- Une pièce jointe ne peut appartenir qu'à une seule tâche
- Un commentaire appartient à un utilisateur
- Un utilisateur peut créer plusieurs commentaires
- Un commentaire appartient à une tâche
- Une pièce jointe appartient à un utilisateur
- Un utilisateur peut créer plusieurs pièces jointes
- Une pièce jointe appartient à une tâche
- Une tâche peut avoir des sous-tâches (tâches liées)

## Exercice 3 : Création d'une base de données d'une application de gestion d'une bibliothèque

## 3.1. Cas d'utilisation

- Un lecteur peut emprunter plusieurs livres
- Un livre peut être emprunté par plusieurs lecteurs
- Un livre peut avoir plusieurs auteurs
- Un auteur peut avoir plusieurs livres
- Un livre peut avoir plusieurs catégories
- Une catégorie peut avoir plusieurs livres
- Les adhérents ont un nom, un prénom et une date de naissance. Ces informations sont consultables par les gestionnaires des emprunts, mais ils ne peuvent les modifier ou les supprimer.
- La bibliothèque comprend un ensemble de documents et un ensemble d’adhérents.
- Au niveau de la bibliothèque, les adhérents sont inscrits ou désinscrits sur une simple demande. Il est possible de retrouver la date d'inscription et la date de désinscription.
- De nouveaux documents sont ajoutés régulièrement à la bibliothèque.
- Ces documents sont soit des journaux, soit des volumes.
- Les volumes sont soit des dictionnaires, soit des livres, soit des BD.
- Les documents sont caractérisés par un titre, une date d'achat.
- Les volumes ont en plus un auteur. Les BD ont en plus une désignation du public (enfant, junior, adulte) destinataire.
- Les journaux ont, outre les caractéristiques des documents, une date de parution.
- Seuls les livres sont empruntables.
- Les adhérents peuvent emprunter des livres (et uniquement des livres) et on doit pouvoir savoir à tout moment quels sont les livres empruntés par un adhérent.
- La date de restitution d’un livre emprunté est fixée au moment du prêt. Cette date peut être prolongée sur demande.
- Un livre emprunté peut être prolongé une seule fois.
- Un bibliothécaire peut emprunter un livre.
- Il est possible de savoir quel bibliothécaire a authorisé un emprunt.
