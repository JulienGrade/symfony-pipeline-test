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

class ExampleTest extends TestCase
{
    public function testExample(): void
    {
        $this->assertTrue(true);
    }
}
```

4. Lance le test en local :
```bash
php bin/phpunit
```
✅ Si le test réussit → Le message "OK" doit s'afficher.

---

## ✅ **3. Configuration de la pipeline GitHub Actions**
1. Crée le dossier de workflow :
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
2. Lance manuellement la pipeline (ou fais un push) → ✅ Les tests doivent passer !

---

## ✅ **5. Problèmes courants et solutions**
| Erreur | Solution |
|--------|----------|
| `phpunit: not found` | Vérifie que PHPUnit est installé correctement avec Composer |
| `Tests échoués` | Vérifie le code du test dans `tests/` |
| `No such file or directory` | Vérifie que le chemin des fichiers de test est correct |

---

## 🌟 **Prochaine étape**
- Ajoute des tests supplémentaires.
- Intègre une couverture de code (exemple : Codecov).

✅ C'est terminé ! 🎉
