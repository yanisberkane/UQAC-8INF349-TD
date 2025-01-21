# Travaux Dirigés - Technologies Web avancées (UQAC - Hiver 2025)

## Installer Python sur Windows

### Étape 1 : Télécharger Python
1. Rendez-vous sur le [site officiel de Python](https://www.python.org/).
2. Cliquez sur le bouton **Download** pour télécharger la dernière version de Python compatible avec votre système.

### Étape 2 : Installation de Python
1. Lancez le fichier téléchargé.
2. Dans le wizard d'installation :
   - **Cochez les cases suivantes avant de cliquer sur "Install Now"**
![Screenshot 2025-01-20 145716](https://github.com/user-attachments/assets/b720f594-5bdc-49e0-8a80-82deb043360c)
3. Une fois l'installation terminée, vérifiez que Python est bien installé en ouvrant un terminal PowerShell et en tapant :
   ```powershell
   python --version
   ```

## Créer un projet Python simple sur VSCode

### Étape 1 : Préparer le dossier de projet
1. Créez un dossier pour votre projet, par exemple `PROJECT_DIR`.
2. Dans ce dossier, créez un fichier `app.py`. Ce fichier contiendra votre code Python.

### Étape 2 : Installer VSCode
1. Téléchargez et installez Visual Studio Code depuis [le site officiel](https://code.visualstudio.com/).
2. Ouvrez le dossier `PROJECT_DIR` dans VSCode.

### Étape 3 : Créer un environnement virtuel
1. Ouvrez un terminal PowerShell dans VSCode (menu **View > Terminal**).
2. Créez un environnement virtuel dans le dossier `.env` du projet :
   ```powershell
   python -m venv .env
   ```
3. Activez l'environnement virtuel :
   ```powershell
   .\.env\Scripts\activate.ps1
   ```

### Résolution de l'erreur : Scripts désactivés
Si vous obtenez l'erreur suivante :
```plaintext
Script "cannot be loaded because running scripts is disabled on this system."
```
Procédez comme suit :
1. Ouvrez un terminal PowerShell en **mode administrateur**.
2. Exécutez la commande suivante :
   ```powershell
   Set-ExecutionPolicy RemoteSigned
   ```
3. Confirmez le changement de politique d'exécution en tapant `Y` ou `A`.
4. Fermez le terminal administrateur et relancez votre terminal PowerShell dans VSCode.
5. Activez à nouveau l'environnement virtuel :
   ```powershell
   .\.env\Scripts\activate.ps1
   ```

### Étape 4 : Lancer votre projet
1. Ajoutez le code suivant dans `app.py` :
   ```python
   print("Hello, Python!")
   ```
2. Dans le terminal, exécutez votre script :
   ```powershell
   python app.py
   ```
3. Vous devriez voir le message suivant dans la console :
   ```plaintext
   Hello, Python!
   ```

## Installer Flask et Créer une Application Flask Simple

### Étape 1 : Installer Flask
Après avoir activé votre environnement virtuel dans PowerShell avec :
```powershell
.\.env\Scripts\activate.ps1
```
Installez Flask via `pip` :
```powershell
pip install flask
```
Vérifiez que Flask est correctement installé :
```powershell
pip show flask
```
Cela affichera les informations sur Flask, y compris la version installée.

### Étape 2 : Ajouter un Code Exemple
Créez ou modifiez le fichier `app.py` dans votre dossier de projet avec le code suivant :
```python
from flask import Flask

app = Flask(__name__)

@app.route("/")
def hello_world():
    return "<p>Hello, World!</p>"
```

### Étape 3 : Lancer l'Application Flask
Pour démarrer l'application Flask, exécutez la commande suivante dans le terminal :
```powershell
flask run --port=5000
```
Une fois l'application lancée, ouvrez un navigateur web et accédez à l'URL :
```
http://127.0.0.1:5000/
```

### Pourquoi l'URL est "localhost" 
- **`localhost` (ou `127.0.0.1`)** : Cela représente votre machine locale. Flask utilise par défaut `localhost` comme hôte, ce qui signifie que l'application est accessible uniquement depuis votre propre machine pour des raisons de sécurité.
- **La route `/`** : Dans Flask, une route est un chemin d'accès associé à une fonction. Ici, `/` correspond à la racine de l'application. Lorsque vous visitez `http://127.0.0.1:5000/`, Flask exécute la fonction `hello_world` et renvoie la réponse HTML "Hello, World!".

### Flags Utiles avec la Commande `flask run`
- **`--host`** : Permet de spécifier l'adresse IP sur laquelle l'application doit être accessible. Par exemple :
  ```powershell
  flask run --host=0.0.0.0
  ```
  Cela rendra l'application accessible depuis d'autres appareils sur le même réseau.

- **`--port`** : Spécifie le port sur lequel l'application doit écouter. Par défaut, Flask utilise le port 5000, mais vous pouvez le changer :
  ```powershell
  flask run --port=8080
  ```

- **`--debug`** : Active le mode débogage, qui permet de recharger automatiquement l'application en cas de modifications du code. Cela fournit également une console interactive en cas d'erreur. Exemple :
  ```powershell
  flask run --debug
  ```
  **Note** : Ce mode est très utile en développement mais ne doit pas être utilisé en production pour des raisons de sécurité.

### Conseils pour Débuter
1. Toujours utiliser un environnement virtuel pour éviter les conflits de dépendances.
2. Activer le mode `--debug` pendant le développement pour accélérer votre workflow.
3. Structurer votre application Flask dès le départ pour faciliter l'ajout de nouvelles fonctionnalités.
