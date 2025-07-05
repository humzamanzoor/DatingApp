# DatingApp - Modern Dating Platform

A full-stack dating application built with ASP.NET Core and Angular, featuring real-time messaging, user matching, and admin controls.

![.NET](https://img.shields.io/badge/.NET-7.0-purple)
![Angular](https://img.shields.io/badge/Angular-14-red)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-13-blue)
![SignalR](https://img.shields.io/badge/SignalR-Real--time-green)

## Features

- **User Management** - Registration, profiles, matching system
- **Real-Time Messaging** - Live chat with SignalR
- **Photo Management** - Upload, approval, gallery
- **Admin Panel** - User moderation, role management
- **Advanced Search** - Filter by gender, age, location

## Tech Stack

### Backend
- ASP.NET Core 7.0 Web API
- Entity Framework Core
- ASP.NET Core Identity (JWT)
- SignalR for real-time communication
- PostgreSQL/SQLite

### Frontend
- Angular 14
- Bootstrap 5
- SignalR Client
- File upload integration

### Infrastructure
- Cloudinary (photo storage)
- Fly.io deployment
- Docker support

## Quick Start

### Prerequisites
- .NET 7.0 SDK
- Node.js 16+
- PostgreSQL
- Cloudinary account

### Backend Setup
```bash
cd API
# Update appsettings.Development.json with your database and Cloudinary credentials
dotnet ef database update
dotnet run
```

### Frontend Setup
```bash
cd client
npm install
npm start
```



## Project Structure
```
DatingApp/
├── API/                    # Backend (.NET Core)
│   ├── Controllers/        # API endpoints
│   ├── Entities/          # Data models
│   ├── Data/              # Database layer
│   ├── Services/          # Business logic
│   └── SignalR/           # Real-time hubs
└── client/                # Frontend (Angular)
    └── src/app/
        ├── members/       # User profiles
        ├── messages/      # Messaging
        ├── admin/         # Admin panel
        └── _services/     # Angular services
```

## Deployment

### Fly.io
```bash
fly auth login
fly deploy
```

### Docker
```bash
docker build -t datingapp .
docker run -p 8080:8080 datingapp
```

## Database Schema

- **AppUser** - User profiles and authentication
- **Photo** - User photos with approval status
- **UserLike** - Like relationships
- **Message** - Chat messages
- **Group/Connection** - SignalR connections

## Security

- JWT Bearer token authentication
- Role-based authorization (Admin, Moderator, Member)
- CORS configuration
- Input validation
- SQL injection protection via Entity Framework

---

