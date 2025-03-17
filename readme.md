# 🚀 Guide de configuration d'une pipeline CI Symfony

Ce guide décrit toutes les étapes pour configurer une pipeline CI/CD avec GitHub Actions pour un projet Symfony.

---

## ✅ **1. Création du projet Symfony**
1. Crée un nouveau projet Symfony :
```bash
composer create-project symfony/skeleton my-symfony-project
```
2. Accède au dossier du projet :
```bash
cd my-symfony-project
```

3. Initialise un dépôt Git :
```bash
git init
```

4. Crée un fichier `.gitignore` à la racine du projet si il n'existe pas :
```bash
touch .gitignore
```
**Ajoute le contenu suivant au .gitignore :**
```
/vendor
/var
/.env.local
/.env.*.local
```

5. Crée le premier commit :
```bash
git add .
git commit -m "Initial Symfony project"
```

6. Crée le dépôt GitHub :
```bash
gh repo create my-symfony-project --public --source=. --push
```
Vous pouvez aussi le créer via l'interface github
---

## ✅ **2. Installation de PHPUnit**
1. Installe PHPUnit via Composer :
```bash
composer require --dev phpunit/phpunit
```

2. Crée le dossier des tests :
```bash
mkdir tests
```

3. Crée un fichier de test basique `tests/ExampleTest.php` :
```php
<?php

namespace App\Tests;

use PHPUnit\Framework\TestCase;

class HomepageControllerTest extends TestCase
{
    public function testHomepageWorks(): void
    {
        $client = static::createClient();
        $client->request('GET', '/');

        $this->assertResponseIsSuccessful();
    }
}
```

4. Lance le test en local :
```bash
php bin/phpunit
```
Le test doit échouer étant donné que l'on a pas de route pour la homepage.

---

## ✅ **3. Configuration de la pipeline GitHub Actions**
1. Crée le dossier de workflow un dossier .github et à l'intérieur un dossier workflows:
```bash
mkdir -p .github/workflows
```

2. Crée le fichier `.github/workflows/ci.yml` :
```bash
nano .github/workflows/ci.yml
```

3. **Colle le contenu suivant :**
   ➡️ Voir le fichier `ci.yml`

4. Crée un commit :
```bash
git add .
git commit -m "Setup GitHub Actions pipeline"
git push origin main
```

---

## ✅ **4. Vérification de la pipeline sur GitHub**
1. Va dans le dépôt GitHub → Onglet **Actions**
2. Lance manuellement la pipeline (ou fais un push) → ✅ Les tests doivent échouer !

---

## ✅ **5. Rédiger le code permettant de faire passer le premier test**
| Créer un controller HomepageController et définir une route sur / 
---

## 🌟 **Faire un nouveau commit et un nouveau push **
Cette fois les tests doivent passer au vert

✅ C'est terminé ! 
