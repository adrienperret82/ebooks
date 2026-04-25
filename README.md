# ebooks
Personal ebooks list
# Drive Ebook Explorer

Explorez et organisez votre collection d'ebooks directement depuis Google Drive avec cette interface interactive et visuelle.

## Générer une version chiffrée
```bash
staticrypt secret/index.html -p PASSWORD -o index.html && cp encrypted/index.html ./
```

## 🚀 Fonctionnalités

- **Interface Moderne** : Thème sombre élégant avec des animations fluides et des icônes contextuelles.
- **Analyse Visuelle** : Visualisez votre bibliothèque avec des graphiques interactifs (Chart.js).
  - Distribution thématique
  - Top des auteurs
- **Filtrage Intuitif** : Cliquez sur une catégorie ou un auteur dans les graphiques pour filtrer instantanément le catalogue complet.
- **Recherche Avancée** : Filtrez par titre, auteur, ou série avec suggestions en temps réel.
- **Métadonnées Enrichies** : Chaque livre affiche un résumé complet, la série, le numéro du volume, et des indicateurs de statut (lu/à lire/en cours).
- **Statistiques Détaillées** : Vue d'ensemble de votre collection (nombre total d'ouvrages, catégories, auteurs, etc.).
- **Responsive Design** : Parfait sur mobile, tablette et ordinateur.
- **Mode Défilement Lisse** : Navigation agréable avec `scroll-behavior: smooth`.
- **Gestion des Erreurs** : Messages clairs si Google Drive n'est pas connecté ou si la structure des dossiers n'est pas conforme.

## 📦 Installation et Utilisation

### Prérequis
- Un compte Google
- Google Drive configuré avec la structure de dossiers décrite ci-dessous
- Google Apps Script avec accès aux fichiers Drive

### Structure des dossiers Google Drive
Pour que l'application fonctionne correctement, votre Google Drive doit être organisé comme suit :

```
/Ebooks
│
├── /Séries
│   ├── /Série 1
│   │   ├── Volume 1 - Titre.epub
│   │   ├── Volume 2 - Titre.epub
│   │   └── ...
│   └── /Série 2
│       └── ...
│
└── /Romans
    ├── Auteur - Titre 1.epub
    ├── Auteur - Titre 2.epub
    └── ...
```

**Règles importantes** :
- Le dossier racine doit s'appeler `Ebooks`
- Les séries doivent être dans le dossier `Séries`
- Les romans indépendants doivent être dans le dossier `Romans`
- Les noms de fichiers doivent respecter le format : `Auteur - Titre.epub` ou `Volume X - Titre.epub` pour les séries

### Étapes d'installation

1. **Accéder au Projet**
   - Ouvrez le dossier du projet
   - Ouvrez `index.html` dans votre éditeur de code préféré

2. **Configurer Google Apps Script**
   - Allez dans `Projets Google Apps Script`
   - Créez un nouveau projet ou ouvrez l'existant
   - Copiez le contenu de `Code.gs` dans le script
   - Copiez le contenu de `appsscript.json` dans `appsscript.json`

3. **Déployer l'Application**
   - Dans l'éditeur Google Apps Script, allez dans `Déploiement` > `Nouveau déploiement`
   - Choisissez `Application web`
   - Configurez les paramètres suivants :
     - **Exécuter en tant que** : `Moi`
     - **Qui a accès** : `Public` (ou `Personnes dans [votre organisation]`, selon votre besoin)
   - Cliquez sur `Déployer`
   - Autorisez les accès nécessaires

4. **Accéder à l'Application**
   - Une fois déployée, cliquez sur l'URL du déploiement
   - Vous pouvez maintenant explorer votre bibliothèque ! ✨

## 🔧 Personnalisation

### Modifier les thématiques
Pour personnaliser les catégories affichées dans les graphiques, modifiez le fichier `appsscript.json` :

```json
{
  "data": {
    "categories": {
      "Science-Fiction": ["Frank Herbert", "Isaac Asimov", "William Gibson", "Neal Stephenson"],
      "Fantasy": ["Tolkien", "Brandon Sanderson", "Ursula K. Le Guin"],
      "Policier / Thriller": ["Stephen King", "Michael Connelly", "Don Winslow"],
      "Histoire / Documentaire": ["Yuval Noah Harari", "Robert Caro"],
      "Biographies / Mémoires": ["Michelle Obama", "Steve Jobs"],
      "Classiques": ["Alexandre Dumas", "Victor Hugo"],
      "Jeunesse / YA": ["Suzanne Collins", "Veronica Roth"]
    },
    "rootFolderId": "YOUR_DRIVE_FOLDER_ID"
  }
}
```

- Ajoutez/supprimez des auteurs dans les listes
- Modifiez les noms des catégories
- Assurez-vous que les noms correspondent aux métadonnées de vos fichiers

### Modifier le dossier racine
Pour utiliser un dossier Drive différent de `/Ebooks`, changez la valeur de `rootFolderId` dans `appsscript.json` :

```json
{
  "data": {
    "categories": {
      "...": [...]
    },
    "rootFolderId": "un-autre-id-de-dossier"
  }
}
```

### Styles personnalisés
Modifiez les variables CSS dans le fichier `index.html` pour adapter le thème :

```html
<style>
    /* Variables de couleur */
    :root {
        --bg-main: #fafaf9;
        --text-main: #292524;
        --accent: #0d9488;
    }

    /* Thème sombre (optionnel) */
    .dark {
        --bg-main: #0a0a0a;
        --text-main: #f5f5f5;
        --accent: #14b8a6;
    }
</style>
```

## 💻 Options de Développement

### Mode Développeur (Debug)
Pour activer les logs de débogage dans la console Apps Script :

1. Dans l'éditeur, allez dans `Paramètres du projet`
2. Cochez `Afficher le journal d'erreurs de Google Apps Script`
3. Exécutez `Code.gs` une fois pour autoriser les accès
4. Vérifiez les logs dans `Exécutions`

## 🤝 Contribuer

Les contributions sont les bienvenues ! N'hésitez pas à :
- Proposer de nouvelles fonctionnalités
- Améliorer le code
- Corriger des bugs
- Ajouter plus de thématiques
- Proposer des améliorations de design

## 📝 Licence

Ce projet est développé à titre personnel. N'hésitez pas à l'utiliser et à le modifier selon vos besoins.

## 📄 Changelog

### Version 1.0.0 (2024-04-25)
- ✅ Déploiement initial de l'application
- ✅ Interface moderne avec thème sombre
- ✅ Visualisation des données avec Chart.js
- ✅ Filtrage interactif par catégories et auteurs
- ✅ Système de recherche
- ✅ Gestion des erreurs et feedback utilisateur
- ✅ Responsive design

## 🐛 Problèmes connus

- [ ] Les métadonnées des fichiers ne sont pas toujours exactes (dépend de la qualité des fichiers EPUB)
- [ ] L'affichage des séries pourrait être amélioré (affichage en arborescence ?)
- [ ] Option pour marquer les livres comme lus/en cours/à lire pourrait être plus visible

## 🍪 Cookies & Vie Privée

Cette application utilise des cookies de session pour maintenir l'état de l'utilisateur (filtres actifs, etc.). En utilisant l'application, vous acceptez l'utilisation de ces cookies.

---

**Créé avec ❤️ pour les amoureux des livres**
