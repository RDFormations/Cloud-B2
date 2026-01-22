# Exercice : Azure Functions

## Objectif

Créer une API serverless avec Azure Functions pour gérer une liste de tâches (TODO list).

## Prérequis

- Compte Azure (ou Azure Functions Core Tools pour test local)
- Node.js 18+ ou Python 3.9+
- VS Code avec l'extension Azure Functions

## Exercice 1 : HTTP Trigger - Créer une fonction GET

Créer une fonction qui retourne la liste des tâches.

**Endpoint attendu :** `GET /api/tasks`

**Réponse attendue :**
```json
{
  "tasks": [
    { "id": 1, "title": "Apprendre Azure Functions", "completed": false },
    { "id": 2, "title": "Déployer en production", "completed": false }
  ]
}
```

## Exercice 2 : HTTP Trigger - Créer une fonction POST

Créer une fonction qui ajoute une nouvelle tâche.

**Endpoint attendu :** `POST /api/tasks`

**Body de la requête :**
```json
{
  "title": "Nouvelle tâche"
}
```

**Réponse attendue :**
```json
{
  "id": 3,
  "title": "Nouvelle tâche",
  "completed": false
}
```

## Exercice 3 : HTTP Trigger avec paramètre

Créer une fonction qui marque une tâche comme complétée.

**Endpoint attendu :** `PUT /api/tasks/{id}/complete`

**Réponse attendue :**
```json
{
  "id": 1,
  "title": "Apprendre Azure Functions",
  "completed": true
}
```

## Exercice 4 : Timer Trigger

Créer une fonction qui s'exécute toutes les heures pour logger les statistiques des tâches.

**Configuration CRON :** `0 0 * * * *`

**Log attendu :**
```
[2024-01-15 10:00:00] Stats: 3 tâches totales, 1 complétée, 2 en cours
```

## Exercice 5 : Queue Trigger

Créer une fonction déclenchée par un message dans une queue Azure Storage.

**Scénario :** Quand une tâche est créée, envoyer un message dans la queue pour notifier (simulation).


## Structure du projet attendue

```
azure-functions-todo/
├── src/
│   └── functions/
│       ├── getTasks.js
│       ├── createTask.js
│       ├── completeTask.js
│       ├── statsTimer.js
│       └── notificationQueue.js
├── host.json
├── local.settings.json
└── package.json
```

## Critères de validation

- [ ] Les fonctions HTTP retournent les bons codes de statut (200, 201, 404)
- [ ] La validation des entrées est implémentée
- [ ] Les erreurs sont gérées proprement
- [ ] Le code est propre et documenté
