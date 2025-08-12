# Configurar prisma

Para configurar prisma tenemos que usar los siguiente comandos

```bash
npm i prisma
```

configurar la inicializacion de prisma con el siguiente comando

```bash
npx prisma init
```

## Configurar archivo docker

Se debe configurar el siguiente archivo para poder montar la imagen de docker que corresponde a postgresql

```yaml
version: '3'

services:
  db:
    image: postgres:14.3
    restart: always
    ports:
      - "5432:5432"
    environment:
      POSTGRES_PASSWORD: 'steve'
      POSTGRES_DB: 
    container_name: 'task'
    volumes:
      - ./postgres:/var/lib/postgresql/data
```

con esto podemos usar el siguiente comando para levantar la base 

```bash
docker-compose up -d 
```

## Configurar la conexion de prisma para la imagen de docker

Ahora que tenemos la imagen arriba podemos configurar la conexion con la misma de la siguiente manera

```env
DATABASE_URL="postgresql://postgres:steve@localhost:5432/taskdb?schema=public"
```