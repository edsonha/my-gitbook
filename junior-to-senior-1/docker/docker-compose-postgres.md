# Docker Compose - Postgres

```text
services:
  # Backend API
  smart-brain-api:
    container_name: backend
    build: ./
    command: npm start
    working_dir: /usr/src/smart-brain-api
    environment:
      POSTGRES_USER: dockerbot
      POSTGRES_PASSWORD: secret
      POSTGRES_DB: smart-brain-docker
      POSTGRES_HOST: postgres
    links:
      - postgres
    ports:
      - "3000:3000"
    volumes:
      - ./:/usr/src/smart-brain-api
  # Postgres
  postgres:
    environment:
      POSTGRES_USER: dockerbot
      POSTGRES_PASSWORD: secret
      POSTGRES_DB: smart-brain-docker
      POSTGRES_HOST: postgres
    build: ./postgres
    ports:
      - "1234:5432"en
```

Environment is the process.env to create and connect database in docker environment. POSTGRES\_HOST has to be the same name with the service name. \(POSTGRES\_URI is not working\)

Links is to connect the API with other services like postgres and redis

Build is to build from Dockerfile in the ./postgres folder \(the opposite of image: postgres &lt;= building from image from DockerHub\)

Ports is to establish port connection \(use other than 5432 if it is being used\)

```text
FROM postgres:10.4

ADD /tables/ /docker-entrypoint-initdb.d/tables/
ADD deploy_schemas.sql /docker-entrypoint-initdb.d/
```

From is to download the postgres version.

Get the sql file from /tables/ folder and map it to the container folder, /docker-entrypoint-initdb.d/tables/

Run deploy\_schemas.sql into the main container folder

```text
// Example of SQL file. Good practice to use TRANSACTION so that the file execute
// fully or none at all if there is an error.

BEGIN TRANSACTION;

CREATE TABLE users (
  id serial PRIMARY KEY,
  name VARCHAR(100),
  email text UNIQUE NOT NULL,
  entries BIGINT DEFAULT 0,
  joined TIMESTAMP NOT NULL
);

COMMIT;
```

```text
// Example of deploy_schemas.sql. Basically it run the following sql files.

\i '/docker-entrypoint-initdb.d/tables/users.sql'
\i '/docker-entrypoint-initdb.d/tables/login.sql'
```

