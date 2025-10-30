# Marestria Admin

Plataforma de administración web profesional para gestionar libros y capítulos con integración directa a GitHub.

## Características

- Crear libros con metadatos completos (título, autor, tags, rating, sinopsis)
- Upload de imágenes de portada con drag & drop
- Editar libros existentes
- Gestionar capítulos (subir, eliminar)
- Commits automáticos al repositorio principal
- Interfaz responsive y moderna
- Autenticación segura

## Stack Tecnológico

- **Frontend**: React 18 + TypeScript + Vite
- **Estilos**: Tailwind CSS
- **Backend**: Netlify Functions
- **Integración**: GitHub API (Octokit)
- **Deploy**: Netlify

## Inicio Rápido

### 1. Instalación

```bash
cd marestria-admin
pnpm install
```

### 2. Configuración Local

Copiar `.env.example` a `.env` y configurar:

```bash
cp .env.example .env
```

Editar `.env` con tus credenciales:

```env
GITHUB_TOKEN=tu_token_de_github
GITHUB_OWNER=tu_usuario
GITHUB_REPO=paokelsheavens-main
GITHUB_BRANCH=main
ADMIN_PASSWORD=tu_password_seguro
JWT_SECRET=tu_jwt_secret_aleatorio
```

### 3. Desarrollo

```bash
# Iniciar servidor de desarrollo
pnpm run dev

# Iniciar Netlify Functions localmente
netlify dev
```

### 4. Build

```bash
pnpm run build
```

### 5. Deploy a Netlify

Ver documentación completa en [docs/CONFIGURACION.md](docs/CONFIGURACION.md)

## Funcionalidades

### CREATE BOOK (Crear Libro)

- Formulario completo para metadatos
- Upload de portada con preview
- Generación automática de slug
- Creación de estructura de carpetas
- Capítulo de ejemplo incluido

### EDIT BOOK (Editar Libro)

- Lista visual de libros
- Modal de edición rápida
- Actualización de metadatos
- Sincronización con books-manager.json

### MANAGE CHAPTERS (Gestionar Capítulos)

- Selector de libro
- Lista de capítulos existentes
- Upload de nuevos capítulos en Markdown
- Eliminación múltiple con confirmación
- Preview de contenido

## Estructura del Proyecto

```
marestria-admin/
├── netlify/
│   └── functions/          # Netlify Functions (Backend)
│       ├── auth.ts
│       ├── create-book.ts
│       ├── edit-book.ts
│       ├── get-books.ts
│       ├── get-chapters.ts
│       ├── upload-chapter.ts
│       ├── delete-chapters.ts
│       └── utils/
│           ├── github.ts
│           └── verify-token.ts
├── src/
│   ├── components/         # Componentes React
│   │   ├── LoginForm.tsx
│   │   ├── Dashboard.tsx
│   │   ├── CreateBookForm.tsx
│   │   ├── EditBookModal.tsx
│   │   ├── ManageChapters.tsx
│   │   └── BooksList.tsx
│   ├── contexts/          # Context API
│   │   └── AuthContext.tsx
│   ├── lib/               # Utilidades
│   │   └── api.ts
│   ├── types/             # TypeScript types
│   │   └── index.ts
│   └── App.tsx
├── docs/
│   └── CONFIGURACION.md   # Documentación completa
├── netlify.toml           # Configuración Netlify
└── package.json
```

## Seguridad

- Autenticación JWT con expiración de 24h
- Validación de credenciales en cada request
- Variables de entorno para secretos
- CORS configurado
- Rate limiting básico

## API Endpoints

### Autenticación

- `POST /.netlify/functions/auth` - Login

### Libros

- `GET /.netlify/functions/get-books` - Listar libros
- `POST /.netlify/functions/create-book` - Crear libro
- `PUT /.netlify/functions/edit-book` - Editar libro

### Capítulos

- `GET /.netlify/functions/get-chapters?slug={slug}` - Listar capítulos
- `POST /.netlify/functions/upload-chapter` - Subir capítulo
- `DELETE /.netlify/functions/delete-chapters` - Eliminar capítulos

## Requisitos del Sistema

- Node.js 18+
- pnpm 8+
- Cuenta de GitHub con acceso al repositorio
- Cuenta de Netlify (para deploy)

## Variables de Entorno Requeridas

```env
GITHUB_TOKEN          # Token de acceso GitHub
GITHUB_OWNER          # Usuario/org del repositorio
GITHUB_REPO           # Nombre del repositorio
GITHUB_BRANCH         # Rama a modificar (main)
ADMIN_PASSWORD        # Password del panel admin
JWT_SECRET            # Clave secreta JWT
```

## Documentación Completa

Para instrucciones detalladas de configuración y uso, consulta:

- [Documentación de Configuración](docs/CONFIGURACION.md)

## Soporte

Para problemas o preguntas, revisar:
1. Logs de Netlify Functions
2. Variables de entorno configuradas
3. Permisos del GitHub Token
4. Documentación completa

## Licencia

Privado y Propietario
