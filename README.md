# Compilateur LESS -> CSS

### 1 - Lancer le projet React

<code> npx create-react-app monProjet</code>

### 2 - Installer npm

<code>npm install</code>

### 3 - Installer less et le compiler

<code>npm i less less-watch-compiler</code>

### 4 - Dans le fichier package.json

<strong>Créer "devDependencies"</strong>. 
```json
"devDependencies": {},
```

<strong>Dans "dependencies" deplacer less et less-watch-compiler dans "devDependencies"</strong>

```json
"dependencies": {
"@testing-library/jest-dom": "^5.11.4",
"@testing-library/react": "^11.1.0",
"@testing-library/user-event": "^12.1.10",
"react": "^17.0.1",
"react-dom": "^17.0.1",
"react-scripts": "4.0.0",
"web-vitals": "^0.2.4",
"less": "^3.12.2",
"less-watch-compiler": "^1.14.6",
},
```

<strong>On retrouve cette configuration</strong>

```json
"dependencies": {
"@testing-library/jest-dom": "^5.11.4",
"@testing-library/react": "^11.1.0",
"@testing-library/user-event": "^12.1.10",
"react": "^17.0.1",
"react-dom": "^17.0.1",
"react-scripts": "4.0.0",
"web-vitals": "^0.2.4"
},
"devDependencies": {
"less": "^3.12.2",
"less-watch-compiler": "^1.14.6"
},
```

### 5 - less-watcher.config.json

<strong>Créer un fichier </strong> less-watcher.config.json à la racine du projet et insérer le json suivant :

```json
{
    "watchFolder": "src/",
    "outputFolder": "src/",
    "sourceMap": true,
    "runOnce": false,
    "enableJs": true
}
```

Ici, nous disons à less-watch-compiler de surveiller tous les fichiers dans 'src' et ses sous-répertoires pour les changements et si un fichier est modifié, sortez le fichier CSS compilé dans le même répertoire.

### 6 - Dans devDependencies

<strong>Ajouter</strong>

```json
"concurrently": "^4.1.0"
```

<strong>On retrouve cette configuration</strong>

```json
"devDependencies": {
"less": "^3.12.2",
"less-watch-compiler": "^1.14.6",
"concurrently": "^4.1.0"
},
```

### 7 - Dans scripts

<strong>Ajouter</strong>

```json
"dev-start": "concurrently --kill-others \"less-watch-compiler --config less-watcher.config.json\" \"react-scripts start\""
```

<strong>On retrouve cette configuration</strong>

```json
"scripts": {
"start": "react-scripts start",
"dev-start": "concurrently --kill-others \"less-watch-compiler --config less-watcher.config.json\"  \"react-scripts start\"",
"build": "react-scripts build",
"test": "react-scripts test",
"eject": "react-scripts eject"
},
```

### 8 - Pour finir

<strong>Changez votre fichier "App.css" en "App.less"</strong> et commencez à coder en CSS dans votre fichier App.less  
<strong>Lancer dans le terminale</strong>
<code>npm run dev-start</code>

Maintenant, codez en LESS dans votre fichier App.less, un fichier App.css se génèrera automatiquement.
Profitez-bien !

#### source :

[https://www.folio3.com/using-less-in-react-without-ejecting](https://www.folio3.com/using-less-in-react-without-ejecting)
