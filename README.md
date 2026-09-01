# Sistema de Gestión de Proyectos Colaborativo con Kanban en Tiempo Real

Aplicación web para gestionar proyectos mediante tableros Kanban, con actualización
en tiempo real entre los usuarios conectados a un mismo proyecto.

## Tecnologías

**Frontend**
- Next.js (App Router) + React + TypeScript
- Tailwind CSS + shadcn/ui
- Zustand (estado global)
- TanStack Query (manejo de datos del servidor)
- Socket.io-client (comunicación en tiempo real)

**Backend**
- Node.js + Express + TypeScript
- Prisma ORM (v7)
- Socket.io (WebSockets)
- JWT + bcrypt (autenticación)

**Base de datos e infraestructura**
- PostgreSQL 16
- Redis 7
- Docker Compose (entorno de desarrollo)

## Requisitos previos

- [Node.js](https://nodejs.org/) (LTS)
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Git](https://git-scm.com/)

## Instalación

1. Clonar el repositorio:
```bash
   git clone https://github.com/EstrellaPrado/kanban-realtime.git
   cd kanban-realtime
```

2. Levantar la base de datos y Redis con Docker:
```bash
   docker compose up -d
```

3. Configurar el backend:
```bash
   cd backend
   npm install
```
   Crear un archivo `.env` dentro de `backend/` con:
   
   DATABASE_URL="postgresql://kanban_user:kanban_pass@localhost:5432/kanban_db"
   
   Aplicar las migraciones:
```bash
   npx prisma migrate dev
```
   Encender el servidor:
```bash
   npm run dev
```

4. Configurar el frontend (en otra terminal):
```bash
   cd frontend
   npm install
   npm run dev
```

5. Abrir [http://localhost:3000](http://localhost:3000) en el navegador.

## Estructura del proyecto

kanban-realtime/
├── backend/ # API en Express + Prisma
│ ├── prisma/ # Esquema y migraciones de la base de datos
│ └── src/ # Código fuente del servidor
├── frontend/ # Aplicación en Next.js
│ ├── app/ # Rutas y páginas
│ └── components/ # Componentes de interfaz (shadcn/ui)
└── docker-compose.yml


## Funcionalidades principales

- Registro, inicio de sesión y recuperación de contraseña
- Creación y gestión de proyectos
- Tablero Kanban con cuatro columnas (Pendiente, En Progreso, Revisión, Completado)
- Comentarios y colaboración en tiempo real (WebSockets)
- Importación y exportación de tareas desde/hacia Excel
- Dashboard con estadísticas del proyecto
