# Cook Book app
# Instrukcja instalacji projektu

- W pliku .env ustawiamy paramtetry dostępowe do bazy danych,
- Jeżeli nie mamy zainstalowanego composera, to w katalogu projektu wykonujemy:
```text
composer install
```
jeżeli mamy to:
```text
composer update
```
- ładujemy migracje i zapełniamy losowymi danymi bazę danych:
```text
php bin/console doctrine:migrations:migrate
php bin/console doctrine:fixtures:load
```
Aby usunąć instniejące migracje i bazy danych, które mogłyby wpłynąć na niepoprawne działanie aplikacji, wykonujemy:
```text
bin/console doctrine:schema:drop --force
bin/console doctrine:query:sql "TRUNCATE TABLE migration_versions"
```
następnie fizycznie usuwamy migracje z folderu i wykonujemy:
```text
bin/console make:migration
bin/console doctrine:migrations:migrate
bin/console doctrine:fixtures:load
```
