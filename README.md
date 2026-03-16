# SubastasApp — TPO DAI 1C2026

Aplicación móvil para gestionar subastas dinámicas ascendentes online.

## Stack

| Capa | Tecnología |
|------|------------|
| Frontend | React Native + Expo |
| Navegación | Expo Router |
| Backend | Node.js + Express + TypeScript |
| Base de datos | SQL Server |
| Tiempo real | Socket.io |
| Documentación API | Swagger (swagger.yaml) |

## Estructura

```
subastasApp/
├── frontend/                  # React Native + Expo
│   ├── app/                   # Pantallas (Expo Router)
│   │   ├── (auth)/            # Login, Registro etapa 1 y 2
│   │   ├── (tabs)/            # Navegación principal
│   │   │   ├── subastas/      # Listado y detalle de subastas
│   │   │   ├── mis-bienes/    # Bienes del usuario
│   │   │   └── perfil/        # Perfil y métricas
│   │   └── subasta/[id]/      # Subasta en vivo
│   ├── components/            # Componentes reutilizables
│   ├── hooks/                 # Custom hooks
│   ├── services/              # Llamadas a la API
│   ├── constants/             # Colores, URLs, etc.
│   └── assets/                # Imágenes, íconos, splash
│
├── backend/                   # Node.js + Express
│   ├── src/
│   │   ├── routes/            # Endpoints REST
│   │   ├── controllers/       # Lógica de cada ruta
│   │   ├── middleware/        # Auth JWT, validaciones
│   │   ├── db/                # Conexión SQL Server
│   │   └── sockets/           # WebSockets (Socket.io)
│   └── swagger.yaml           # Documentación API
│
├── .claude/
│   └── commands/
│       ├── fix.md
│       ├── endpoint.md
│       ├── pantalla.md
│       └── test.md
├── .claudecode                # Reglas del proyecto
└── README.md
```

## Iniciar el proyecto

### 1. Frontend — Expo
```bash
cd frontend
npx create-expo-app . --template blank-typescript
npx expo install expo-router react-native-safe-area-context react-native-screens
```

### 2. Backend — Node.js
```bash
cd backend
npm init -y
npm install express typescript ts-node mssql jsonwebtoken bcrypt socket.io dotenv
npm install -D @types/express @types/node @types/jsonwebtoken @types/bcrypt nodemon
npx tsc --init
```

### 3. Swagger
```bash
cd backend
npm install swagger-ui-express swagger-jsdoc
npm install -D @types/swagger-ui-express @types/swagger-jsdoc
```

## Entregas

| Entrega | Fecha | Estado |
|---------|-------|--------|
| 1 — Wireframes + Swagger | 20/04 | 🟡 En progreso |
| 2 — Backend + Frontend 50% | — | ⬜ Pendiente |
| 3 — App completa | — | ⬜ Pendiente |

## Reglas de negocio clave

- **Categorías**: común < especial < plata < oro < platino
- **Puja mínima**: última oferta + 1% del valor base
- **Puja máxima**: última oferta + 20% del valor base *(no aplica a oro/platino)*
- **Multa por incumplimiento de pago**: 10% del valor ofertado
- **Un usuario no puede estar en más de una subasta simultáneamente**
- **Medios de pago**: cuenta bancaria, tarjeta de crédito, cheque certificado
