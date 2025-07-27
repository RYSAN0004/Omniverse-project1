# Iron Man-Style Holographic 3D Model Viewer

## Overview

This is a React-based 3D model viewer application inspired by Iron Man's holographic interface. The app provides gesture-controlled 3D model manipulation using computer vision, drawing capabilities, and an immersive sci-fi user experience.

## User Preferences

Preferred communication style: Simple, everyday language.
User requests: Professional clean UI without emoji buttons, developer branding "RYSAN" only in About section, improved camera permission system, overlay toggle functionality, drawing tools integration in 3-dot menu, enhanced drawing capabilities.

## System Architecture

The application follows a full-stack architecture with a clear separation between client and server:

- **Frontend**: React with TypeScript, using Three.js/React Three Fiber for 3D rendering
- **Backend**: Express.js server with file upload capabilities
- **Database**: PostgreSQL with Drizzle ORM (configured but minimal usage)
- **Build System**: Vite for development and production builds
- **Styling**: Tailwind CSS with custom holographic themes

## Key Components

### Frontend Architecture
- **React Three Fiber**: 3D scene management and rendering
- **MediaPipe Integration**: Hand gesture recognition and tracking
- **Zustand State Management**: Multiple stores for different concerns (game, gesture, model, audio, tutorial)
- **Radix UI Components**: Comprehensive UI component library
- **Custom Holographic Interface**: CSS-based sci-fi styling
- **Options Menu**: 3-dot menu with settings and toggles
- **Camera Permission System**: Secure camera access with user-friendly modal

### Backend Architecture
- **Express Server**: RESTful API with middleware for logging and error handling
- **File Upload System**: Multer for handling 3D model uploads (.glb, .gltf, .obj)
- **Memory Storage**: Simple in-memory storage for development (can be extended to database)
- **Vite Integration**: Development server with HMR support

### 3D Model System
- **Model Loading**: Support for GLTF, GLB, and OBJ formats
- **Gesture Controls**: Left hand pinch for zoom, right hand palm for rotation
- **Drawing Canvas**: 2D overlay for annotations on 3D models
- **Model History**: Track uploaded and manipulated models
- **Model Uploader**: File upload interface for 3D models

### Gesture Recognition
- **MediaPipe Hands**: Real-time hand tracking via webcam
- **Gesture Processing**: Convert hand landmarks to control inputs
- **Visual Feedback**: Holographic indicators for detected gestures
- **Toggle Control**: Ability to enable/disable gesture detection

### User Interface Features
- **Clean Professional Design**: Minimal interface without emoji buttons
- **3-Dot Options Menu**: Centralized control panel with all features
- **Developer Branding**: "RYSAN" name only shown in About section
- **Overlay Controls**: Toggle visibility of holographic overlays
- **Drawing Tools Integration**: Enhanced drawing tools within options menu
- **Interactive Tutorial**: Auto-start tutorial system for new users
- **Audio Controls**: Mute/unmute functionality
- **Camera Permission System**: User-friendly modal for camera access
- **About Section**: Comprehensive information about Omniverse platform
- **Mobile Responsive**: Optimized for mobile and tablet devices

## Data Flow

1. **Model Upload**: Files uploaded via REST API to server storage
2. **3D Rendering**: Models loaded into Three.js scene via React Three Fiber
3. **Gesture Detection**: MediaPipe processes webcam feed and outputs hand landmarks
4. **Control Mapping**: Hand gestures converted to 3D transformations (scale, rotation)
5. **State Management**: Zustand stores manage application state across components
6. **Visual Updates**: React renders UI updates based on state changes

## External Dependencies

### Core 3D and UI Libraries
- **@react-three/fiber**: React renderer for Three.js
- **@react-three/drei**: Useful helpers for React Three Fiber
- **three**: 3D graphics library
- **@radix-ui**: Accessible UI components

### Computer Vision
- **MediaPipe**: Hand tracking (loaded via CDN)
- Browser MediaDevices API for webcam access

### Database and Storage
- **@neondatabase/serverless**: PostgreSQL connection (Neon database)
- **drizzle-orm**: Type-safe ORM
- **multer**: File upload middleware

### Development Tools
- **vite**: Build tool and dev server
- **typescript**: Type safety
- **tailwindcss**: Utility-first CSS framework

## Deployment Strategy

### Development
- Vite dev server with HMR for frontend
- Express server with live reload via tsx
- Automatic TypeScript compilation

### Production Build
- `npm run build`: Compiles frontend assets and bundles server
- Frontend built to `dist/public`
- Server bundled with esbuild to `dist/index.js`
- Static asset serving for production

### Environment Configuration
- Database connection via `DATABASE_URL` environment variable
- File uploads stored in `uploads/models/` directory
- Support for both development and production environments

### Deployment Considerations
- Requires PostgreSQL database (Neon or similar)
- Camera permissions needed for gesture recognition
- File storage for uploaded 3D models
- HTTPS recommended for MediaDevices API access

The application is designed to be easily deployable on platforms like Replit, Vercel, or similar hosting services with Node.js support.