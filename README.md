Mailer project on base [Nano Ninja Docker Boilerplate](https://github.com/nanoninja/docker-nginx-php-mysql)

## Use Docker commands
### Run
```
docker-compose up -d
```

### Stop
```
docker-compose down -v
```

### Composer install
```
docker run --rm -v $(pwd)/web:/app composer install
```

### Create the database & tables
```
docker-compose exec php php ./bin/console doctrine:database:create
docker-compose exec php php ./bin/console doctrine:migrations:migrate
docker-compose exec php php ./bin/console doctrine:fixtures:load
```

### Cache clear
```
docker-compose exec php php ./bin/console cache:clear
```
### Cache warm
```
docker-compose exec php php ./bin/console cache:warmup
```

### Connecting MySQL from [PDO](http://php.net/manual/en/book.pdo.php)

```php
<?php
    try {
        $dsn = 'mysql:host=mysql;dbname=test;charset=utf8;port=3306';
        $pdo = new PDO($dsn, 'dev', 'dev');
    } catch (PDOException $e) {
        echo $e->getMessage();
    }
?>
```

### XDebug
For a better integration of Docker to PHPStorm, use the [documentation](https://github.com/nanoninja/docker-nginx-php-mysql/blob/master/doc/phpstorm-macosx.md).
___

## Other commands

All other commands and features at [Nano Ninja github](https://github.com/nanoninja/docker-nginx-php-mysql)