# Swagger UI для Genealogy API

Этот каталог содержит простую страницу Swagger UI, которая загружает `docs/04_api_contract.openapi.yaml`.

## Запуск через локальный статический сервер

1. Откройте терминал.
2. Перейдите в каталог `docs` проекта:

```bash
cd /d/my-work/docs
```

3. Запустите простой HTTP-сервер.

### Вариант A: Python

```bash
python -m http.server 8081
```

### Вариант B: Node.js

```bash
npx http-server -p 8081
```

4. Откройте в браузере:

```text
http://localhost:8081/swagger-ui/index.html
```

## Запуск через Docker

Если у вас установлен Docker, можно запустить готовый Swagger UI:

```bash
docker run --rm -p 8081:8080 -v /d/my-work/docs:/usr/share/nginx/html -e SWAGGER_JSON=/usr/share/nginx/html/04_api_contract.openapi.yaml swaggerapi/swagger-ui
```

> Если путь `/d/my-work/docs` не работает, попробуйте указать его в формате Docker для Windows (`//d/my-work/docs`), или используйте тот путь, который доступен в вашей Docker-среде.

Откройте в браузере:

```text
http://localhost:8081
```

## Что делает эта страница

Файл `index.html` подключает Swagger UI из CDN и загружает YAML-схему из `../04_api_contract.openapi.yaml`.

Если структура файлов изменится, обновите путь `url` в `docs/swagger-ui/index.html`.
