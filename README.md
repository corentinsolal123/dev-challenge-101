
# Vue.js - Gestion des Environnements (Développement, Production, Intégration)

Ce projet Vue.js démontre comment configurer et gérer différents environnements (développement, production et intégration) à l'aide de variables d'environnement et de scripts personnalisés.

## Installation

1. Installer Vue CLI
```
npm install -g @vue/cli
```

2. Créer un nouveau projet
```
vue create dev-env-challenge
```

## Structure des fichiers `.env`

Nous utilisons un seul fichier `.env` pour centraliser les variables d'environnement :

### Fichier `.env` (à la racine du projet)

Créer un fichier `.env.xxxxx` par environnement de développement et y ajouter une variable `VUE_APP_ENV_MODE`

```env
# Variable pour le mode développement
VUE_APP_ENV_MODE=Mode de développement

# Variable pour le mode production
VUE_APP_ENV_MODE=Mode de production

# Variable pour le mode intégration
VUE_APP_ENV_MODE=Mode d'intégration
```

### Configuration dans le composant Vue.js

Dans le fichier `App.vue`, nous déterminons dynamiquement quelle variable d'environnement afficher en fonction du mode (`development`, `production` ou `integration`).

```vue
<template>
    <div>
        <h1>{{ message }}</h1>
    </div>
</template>

<script>
export default {
    data() {
        return {
            message: process.env.VUE_APP_ENV_MODE || "Mode non défini",
        }
    },
}
</script>

<style>
body {
    background-color: black;
    color: white;
}
</style>
```

## Gestion des Environnements

### Scripts disponibles

Les scripts suivants sont configurés dans le fichier `package.json` pour lancer l'application dans différents environnements.

```
"scripts": {
        "serve": "vue-cli-service serve",
        "prod": "vue-cli-service serve --mode production",  
        "integ": "vue-cli-service serve --mode integration",  
        "build": "vue-cli-service build",
        "lint": "vue-cli-service lint"
    }
```