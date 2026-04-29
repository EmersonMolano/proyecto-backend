# proyecto-backend

API Spring Boot conectada a PostgreSQL por red Docker compartida.

## Archivo principal

- `docker-compose.backend.yml`

## Requisito previo

Debe estar levantada la capa DB/Liquibase (crea la red `api_app-network` y las tablas).

## Cómo ejecutar

Desde la raíz del proyecto (`API/API`):

```bash
docker compose -f proyecto-backend/docker-compose.backend.yml up -d --build
```

## Variables importantes

- `SPRING_DATASOURCE_URL=jdbc:postgresql://db:5432/tareas_db`
- `SPRING_DATASOURCE_USERNAME=postgres`
- `SPRING_DATASOURCE_PASSWORD=postgres`

## Verificación rápida

```bash
docker ps -a
docker logs backend_app --tail 120
```

Pruebas HTTP:

- `http://localhost:8080/swagger-ui.html`
- `http://localhost:8080/api/usuarios`

## Troubleshooting

Si el contenedor cae con `Schema-validation: missing table [tarea]`, la causa está en migraciones no aplicadas. Reejecuta primero la capa `proyecto-liquibase`.
