# 🧠 Symfony CLI Cheat Sheet (PHP 8.4 / Symfony 7.x)

A quick reference for commonly used Symfony and Doctrine CLI commands.

---

## ⚙️ Project Setup

| Purpose | Command |
|----------|----------|
| Create new Symfony project (website skeleton) | `composer create-project symfony/website-skeleton my_project` |
| Create minimal API project | `composer create-project symfony/skeleton my_api_project` |
| Start local web server | `symfony serve -d` |
| Stop web server | `symfony server:stop` |
| Check environment & versions | `symfony check:requirements` |
| Clear cache | `php bin/console cache:clear` |
| Install dependencies | `composer install` |
| Update dependencies | `composer update` |
| Run migrations and clear cache | `php bin/console doctrine:migrations:migrate --no-interaction && php bin/console cache:clear` |

---

## 🧱 Doctrine (Database ORM)

| Purpose | Command |
|----------|----------|
| Create database | `php bin/console doctrine:database:create` |
| Drop database | `php bin/console doctrine:database:drop --force` |
| Generate migration file | `php bin/console make:migration` |
| Run migrations | `php bin/console doctrine:migrations:migrate` |
| Rollback last migration | `php bin/console doctrine:migrations:rollback` |
| Show migration status | `php bin/console doctrine:migrations:status` |
| Update DB schema directly (no migration) | `php bin/console doctrine:schema:update --force` |
| Validate mapping | `php bin/console doctrine:schema:validate` |
| Run raw SQL query | `php bin/console dbal:run-sql "SELECT * FROM travel_package"` |

---

## 📦 Entities & Repositories

| Purpose | Command |
|----------|----------|
| Create new entity | `php bin/console make:entity` |
| Add field to entity | (same command) `php bin/console make:entity` |
| Create repository | Automatically generated when entity is created |
| Regenerate getters/setters | `php bin/console make:entity --regenerate` |

---

## 🧩 Controllers, DTOs, Services

| Purpose | Command |
|----------|----------|
| Create a new controller | `php bin/console make:controller Api/BookingController` |
| Create a service class | manually in `src/Service/` or use: `php bin/console make:service BookingService` |
| Create a DTO (Data Transfer Object) | manually in `src/Dto/`, e.g. `src/Dto/CreateBookingDto.php` |
| Dump route list | `php bin/console debug:router` |
| Check container services | `php bin/console debug:container` |
| Check registered parameters | `php bin/console debug:container --parameters` |
| Debug environment variables | `php bin/console debug:dotenv` |

---

## 🧪 Validation & Fixtures

| Purpose | Command |
|----------|----------|
| Validate database schema | `php bin/console doctrine:schema:validate` |
| Load fixtures (if using doctrine-fixtures) | `php bin/console doctrine:fixtures:load` |
| Clear cache after fixtures | `php bin/console cache:clear` |

---

## 🧰 Debugging

| Purpose | Command |
|----------|----------|
| Debug routes | `php bin/console debug:router` |
| Debug container services | `php bin/console debug:container` |
| Debug environment | `php bin/console debug:dotenv` |
| Debug event listeners | `php bin/console debug:event-dispatcher` |
| List all commands | `php bin/console list` |

---

## 🧑‍💻 User & Security (Optional)

| Purpose | Command |
|----------|----------|
| Create new User entity with security | `php bin/console make:user` |
| Configure security | `php bin/console make:security:form-login` |
| Hash a password | `php bin/console security:hash-password` |

---

## 🧮 Testing & Linting

| Purpose | Command |
|----------|----------|
| Run PHPUnit tests | `php bin/phpunit` |
| Lint Twig templates | `php bin/console lint:twig templates/` |
| Lint YAML config | `php bin/console lint:yaml config/` |
| Lint Doctrine mapping | `php bin/console doctrine:schema:validate` |
| Static analysis (PHPStan) | `vendor/bin/phpstan analyse src` |

---

## 📦 Cache, Logs & Environment

| Purpose | Command |
|----------|----------|
| Clear cache | `php bin/console cache:clear` |
| Warm up cache | `php bin/console cache:warmup` |
| Show current environment | `echo $APP_ENV` |
| View logs | `tail -f var/log/dev.log` |

---

## 🐳 Docker Integration

| Purpose | Command |
|----------|----------|
| Build containers | `docker compose build` |
| Start containers | `docker compose up -d` |
| Stop containers | `docker compose down` |
| View logs | `docker compose logs -f php` |
| Run Symfony command inside PHP container | `docker compose exec php php bin/console cache:clear` |
| Access container shell | `docker compose exec php bash` |

---

## ⚡ Developer Shortcuts

| Shortcut | Command |
|-----------|----------|
| Create a CRUD resource (entity + controller + form) | `php bin/console make:crud` |
| Create migration & apply | `php bin/console make:migration && php bin/console doctrine:migrations:migrate` |
| Reset DB & reload fixtures | `php bin/console doctrine:database:drop --force && php bin/console doctrine:database:create && php bin/console doctrine:migrations:migrate && php bin/console doctrine:fixtures:load` |

---

## 🧾 Composer Helpers

| Purpose | Command |
|----------|----------|
| Require a package | `composer require symfony/validator` |
| Remove a package | `composer remove symfony/validator` |
| Check outdated packages | `composer outdated` |
| Autoload dump (after adding classes) | `composer dump-autoload` |

---

## 🚀 Example Development Flow

```bash
# 1. Create entity and migration
php bin/console make:entity TravelPackage
php bin/console make:migration
php bin/console doctrine:migrations:migrate

# 2. Create controller
php bin/console make:controller Api/TravelPackageController

# 3. Create DTO manually
# src/Dto/TravelPackageDto.php

# 4. Create service manually
# src/Service/TravelPackageService.php

# 5. Run the Symfony server
symfony serve -d

# 6. Verify routes
php bin/console debug:router
