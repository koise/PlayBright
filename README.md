# PlayBright - Full-Stack Monorepo

A modern full-stack project with Mobile (React Native/Expo) and Web (React/Vite) platforms, built with MVC/MVCC architecture and a clean separation of concerns.

## 📁 Project Structure

```
PlayBright/
├── Mobile/
│   ├── Backend/          # Express API for Mobile
│   │   ├── src/
│   │   │   ├── config/       # Configuration files
│   │   │   ├── controllers/  # Request handlers
│   │   │   ├── core/         # Services, middleware, utils
│   │   │   ├── models/       # Data models & schemas
│   │   │   ├── routes/       # API route definitions
│   │   │   └── server.ts     # Entry point
│   │   └── package.json
│   └── Frontend/         # Expo React Native App
│       ├── src/
│       │   ├── app/          # Expo Router screens
│       │   ├── config/       # Configuration files
│       │   ├── core/         # Services, hooks, utils
│       │   ├── models/       # Data models
│       │   └── views/        # UI components
│       └── package.json
├── Web/
│   ├── Backend/          # Express API for Web
│   │   ├── src/
│   │   │   ├── config/       # Configuration files
│   │   │   ├── controllers/  # Request handlers
│   │   │   ├── core/         # Services, middleware, utils
│   │   │   ├── models/       # Data models & schemas
│   │   │   ├── routes/       # API route definitions
│   │   │   └── server.ts     # Entry point
│   │   └── package.json
│   └── Frontend/         # React Vite App
│       ├── src/
│       │   ├── config/       # Configuration files
│       │   ├── core/         # Services, hooks, utils
│       │   ├── models/       # Data models
│       │   └── views/        # Pages & components
│       └── package.json
├── shared/               # Shared code between platforms
│   ├── src/
│   │   ├── components/   # Shared React components
│   │   ├── hooks/        # Shared React hooks
│   │   ├── services/     # Shared services
│   │   └── types/        # Shared TypeScript types
│   └── package.json
└── package.json          # Root workspace configuration
```

## 🏗️ Architecture

This project follows **MVC (Model-View-Controller)** architecture with a clean separation:

### Backend Structure:
- **Models**: Data structures, schemas, and type definitions
- **Controllers**: HTTP request handlers (Express route handlers)
- **Services**: Business logic and data operations
- **Routes**: API endpoint definitions
- **Core**: Middleware, utilities, and shared services
- **Config**: Environment variables and constants

### Frontend Structure:
- **Models**: TypeScript interfaces and type definitions
- **Views/Screens**: UI components and pages
- **Services**: API communication layer
- **Hooks**: Custom React hooks for state management and API calls
- **Core**: Utilities and shared functionality
- **Config**: Environment variables and constants

**Note**: Controllers are **only** in the backend. Frontend uses services and hooks for API communication.

## 🚀 Getting Started

### Prerequisites

- Node.js >= 18.0.0
- npm >= 9.0.0
- Expo CLI (for mobile development)
- Supabase account (optional, for database)

### Installation

1. **Clone the repository** (if applicable) or navigate to the project directory

2. **Install all dependencies**:
   ```bash
   npm run install:all
   ```
   Or manually:
   ```bash
   npm install
   ```

3. **Set up environment variables**:

   - **Mobile Frontend**: Copy `Mobile/Frontend/src/config/env.example` to `.env` and fill in your values
   - **Mobile Backend**: Copy `Mobile/Backend/src/config/env.example` to `.env` and fill in your values
   - **Web Frontend**: Copy `Web/Frontend/src/config/env.example` to `.env` and fill in your values
   - **Web Backend**: Copy `Web/Backend/src/config/env.example` to `.env` and fill in your values

### Running the Project

**Run everything with one command**:
```bash
npm run dev
```

This will start:
- Mobile Backend on `http://localhost:4000`
- Web Backend on `http://localhost:5000`
- Mobile Frontend (Expo) - scan QR code with Expo Go app
- Web Frontend on `http://localhost:3000`

**Run individual services**:
```bash
# Mobile Frontend only
npm run dev:mobile

# Web Frontend only
npm run dev:web

# Mobile Backend only
npm run dev:mobile-backend

# Web Backend only
npm run dev:web-backend
```

## 📦 Key Dependencies

### Mobile Frontend
- **expo**: ~51.0.0 - React Native framework
- **expo-router**: ~3.5.0 - File-based routing
- **@react-navigation/native**: Navigation library
- **@supabase/supabase-js**: Database client
- **axios**: HTTP client
- **zod**: Schema validation
- **react-hook-form**: Form management

### Web Frontend
- **react**: ^18.2.0 - UI library
- **react-router-dom**: Client-side routing
- **vite**: Build tool
- **@supabase/supabase-js**: Database client
- **axios**: HTTP client
- **zod**: Schema validation
- **react-hook-form**: Form management

### Backend (Both Mobile & Web)
- **express**: Web framework
- **cors**: CORS middleware
- **dotenv**: Environment variables
- **@supabase/supabase-js**: Database client
- **zod**: Schema validation
- **axios**: HTTP client

## 🔧 Configuration

### Port Configuration

- Mobile Backend: `4000` (configurable via `PORT` env variable)
- Web Backend: `5000` (configurable via `PORT` env variable)
- Web Frontend: `3000` (configurable in `vite.config.ts`)

### Environment Variables

Each service has its own `.env` file. See the `env.example` files in each service's `config` directory for required variables.

## 📝 Development Guidelines

### Adding New Features

**Backend:**
1. **Models**: Define data structures and schemas in `models/` directory
2. **Services**: Add business logic in `core/services/` directory
3. **Controllers**: Add HTTP request handlers in `controllers/` directory
4. **Routes**: Define API endpoints in `routes/` directory

**Frontend:**
1. **Models**: Define TypeScript interfaces in `models/` directory
2. **Services**: Add API communication in `core/services/` directory
3. **Hooks**: Create custom React hooks in `core/hooks/` directory
4. **Views/Screens**: Create UI components in `views/` or `app/` directory

### Shared Code

Place code that should be shared between Mobile and Web in the `shared/` directory:
- Common types in `shared/src/types/`
- Shared services in `shared/src/services/`
- Shared hooks in `shared/src/hooks/`
- Shared components in `shared/src/components/`

### TypeScript

All projects use TypeScript with strict mode enabled. Ensure type safety when adding new code.

## 🧪 Testing

Add your test files following the same directory structure:
- Unit tests: `*.test.ts` or `*.test.tsx`
- Integration tests: `*.integration.test.ts`

## 📱 Mobile Development

### Running on iOS Simulator
```bash
cd Mobile/Frontend
npm run ios
```

### Running on Android Emulator
```bash
cd Mobile/Frontend
npm run android
```

### Running on Web
```bash
cd Mobile/Frontend
npm run web
```

## 🌐 Web Development

The web frontend uses Vite for fast development and hot module replacement.

## 🗄️ Database

This project is configured to use Supabase, but you can replace it with any database solution. Update the database service in `core/services/database.service.ts` accordingly.

## 📚 Additional Resources

- [Expo Documentation](https://docs.expo.dev/)
- [React Native Documentation](https://reactnative.dev/)
- [React Documentation](https://react.dev/)
- [Vite Documentation](https://vitejs.dev/)
- [Express Documentation](https://expressjs.com/)
- [Supabase Documentation](https://supabase.com/docs)
- [Zod Documentation](https://zod.dev/)

## 🤝 Contributing

1. Create a feature branch
2. Make your changes
3. Ensure all services run without errors
4. Submit a pull request

## 📄 License

[Your License Here]

---

**Happy Coding! 🚀**

#   P l a y B r i g h t  
 