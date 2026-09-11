# PRD — Postiz (self-hosted, fork DITAP)

> Describe el **producto/uso**. Para reglas de ingeniería del fork ver `CLAUDE.md`.

## 1. Qué es

Instancia **self-hosted de Postiz**, herramienta open source de programación y
publicación de contenido en redes sociales (28+ canales), con calendario, analítica,
gestión de equipo y librería de medios. Este repo es un **fork** de
`gitroomhq/postiz-app` (upstream) mantenido en `JRM-Global/postiz-app` (origin).

## 2. Para quién

Uso interno de DITAP — probablemente como capa de distribución/publicación para
**DITAP Media** (`saas/ditap-media/`, brazo de contenido/producción audiovisual del
grupo). No es un producto que DITAP venda: es herramienta de operación.

## 3. Funcionalidad (heredada del proyecto Postiz)

- Programación de posts a 28+ canales/redes sociales
- Vista de calendario de contenido
- Analítica de publicaciones
- Gestión de equipo
- Librería de medios
- Agentes de IA integrados (CopilotKit, LangChain/LangGraph, Mastra) para asistencia
  en la generación/gestión de contenido

## 4. Arquitectura (monorepo pnpm)

- `apps/backend` — API (NestJS)
- `apps/orchestrator` — jobs en background con Temporal (NestJS): workflows y activities
- `apps/frontend` — frontend (Vite + React)
- `libraries` — servicios compartidos entre backend, orchestrator y frontend
- Backend sigue capas estrictas: Controller → Service → Repository (a veces Controller
  → Manager → Service → Repository), sin atajos

## 5. Stack técnico

NestJS, Vite + React, Tailwind 3 (tokens propios en `colors.scss`/`global.scss` — las
clases `--color-custom*` están deprecadas), Prisma, Temporal, Docker Compose para dev.

## 6. Qué NO es

No es un producto propio de DITAP en el sentido de IP diferenciada: es un fork de un
proyecto open source (AGPL 3.0) que se mantiene actualizado contra upstream. Cualquier
feature genérica de Postiz debería evaluarse primero como contribución upstream antes
de divergir innecesariamente; lo que sí es específico de DITAP son configuraciones,
credenciales y el uso operativo interno.

## 7. Estado

Desplegado y en uso (Dockerfile.dev y docker-compose.yaml presentes para dev/self-host).
