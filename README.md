# Установка

- В composer.json в require-dev прописываем:
  `"eggheads/eggheads-code-style": "dev-master"`
- Не забываем указывать там же:
  `"minimum-stability": "dev"`
- Подключаем репозиторий:

```json
{
    "type": "vcs",
    "url": "git://github.com/vovantune/eggheads-code-style"
}
```

# Настройка Php code sniffer

- Создаём в корне проекта файл phpcs.xml.dist вида:

```xml
<?xml version="1.0" encoding="UTF-8"?>

<ruleset xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:noNamespaceSchemaLocation="vendor/squizlabs/php_codesniffer/phpcs.xsd">

    <arg name="basepath" value="."/>
    <arg name="cache" value=".phpcs-cache"/>
    <arg name="colors"/>
    <arg name="extensions" value="php,ctp"/>
    <arg name="parallel" value="75"/>

    <rule ref="vendor/eggheads/eggheads-code-style/rules/phpcs-rules.xml"/>

    <file>src/</file>
    <file>tests/</file>
</ruleset>
```

- Запуск сниффера:
  `vendor/bin/phpcs --colors -p src/ tests/`
- Автоисправление:
  `vendor/bin/phpcbf --colors -p src/ tests/`
