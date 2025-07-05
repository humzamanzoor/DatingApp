# DatingApp - Modern Dating Platform

A full-stack dating application built with ASP.NET Core and Angular, featuring real-time messaging, user matching, and comprehensive admin controls.

![DatingApp](https://img.shields.io/badge/.NET-7.0-purple)
![Angular](https://img.shields.io/badge/Angular-14-red)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-13-blue)
![SignalR](https://img.shields.io/badge/SignalR-Real--time-green)

## 🌟 Features

### 👥 User Management
- **User Registration & Authentication** - Secure JWT-based authentication
- **Profile Management** - Complete user profiles with photos and preferences
- **Smart Matching** - Like/unlike system with mutual matching
- **Advanced Search** - Filter users by gender, age, location, and interests
- **Role-Based Access** - Admin, Moderator, and Member roles

### 💬 Real-Time Communication
- **Live Messaging** - Real-time chat between matched users
- **Online Presence** - See when users are online
- **Message History** - Complete conversation history
- **Instant Notifications** - Real-time updates

### 📸 Photo Management
- **Photo Upload** - Cloud storage with Cloudinary integration
- **Photo Approval** - Admin-controlled photo moderation
- **Main Photo Selection** - Set primary profile pictures
- **Photo Gallery** - Multiple photos per user

### 🛡️ Admin Panel
- **User Management** - View and manage all users
- **Photo Moderation** - Approve/reject uploaded photos
- **Role Management** - Assign and manage user roles
- **System Monitoring** - Track user activity and system health

## 🏗️ Architecture

### Backend (ASP.NET Core 7.0)
- **Entity Framework Core** - Data access and migrations
- **ASP.NET Core Identity** - User authentication and authorization
- **SignalR** - Real-time communication
- **AutoMapper** - Object mapping
- **JWT Bearer Tokens** - API security
- **Repository Pattern** - Clean data access layer

### Frontend (Angular 14)
- **Angular Router** - Client-side navigation
- **Bootstrap 5** - Responsive UI components
- **SignalR Client** - Real-time features
- **File Upload** - Photo management
- **Route Guards** - Protected routes
- **HTTP Interceptors** - Request/response handling

### Database
- **PostgreSQL** - Production database
- **SQLite** - Development database
- **Entity Framework Migrations** - Database versioning

## 🚀 Quick Start

### Prerequisites
- [.NET 7.0 SDK](https://dotnet.microsoft.com/download/dotnet/7.0)
- [Node.js 16+](https://nodejs.org/)
- [PostgreSQL](https://www.postgresql.org/download/) (for production)
- [Cloudinary Account](https://cloudinary.com/) (for photo storage)

### Backend Setup

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd DatingApp/API
   ```

2. **Configure database connection**
   - Update `appsettings.Development.json` with your PostgreSQL credentials
   - For production, set environment variables:
     ```bash
     DATABASE_URL=your_postgres_connection_string
     ```

3. **Configure Cloudinary**
   - Update `appsettings.Development.json` with your Cloudinary settings:
     ```json
     "CloudinarySettings": {
       "CloudName": "your_cloud_name",
       "ApiKey": "your_api_key",
       "ApiSecret": "your_api_secret"
     }
     ```

4. **Run database migrations**
   ```bash
   dotnet ef database update
   ```

5. **Start the API**
   ```bash
   dotnet run
   ```
   The API will be available at `https://localhost:5001`

### Frontend Setup

1. **Navigate to client directory**
   ```bash
   cd ../client
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Configure API URL**
   - Update `src/environments/environment.ts` if needed:
     ```typescript
     export const environment = {
       production: false,
       apiUrl: 'https://localhost:5001/api/',
       hubUrl: 'https://localhost:5001/hubs/'
     };
     ```

4. **Start the development server**
   ```bash
   npm start
   ```
   The application will be available at `http://localhost:4200`

## 📁 Project Structure

```
DatingApp/
├── API/                          # Backend (.NET Core)
│   ├── Controllers/              # API endpoints
│   │   ├── AccountController.cs  # Authentication
│   │   ├── UsersController.cs    # User management
│   │   ├── MessagesController.cs # Messaging
│   │   └── AdminController.cs    # Admin functions
│   ├── Entities/                 # Data models
│   │   ├── AppUser.cs           # User entity
│   │   ├── Message.cs           # Message entity
│   │   └── Photo.cs             # Photo entity
│   ├── Data/                    # Database layer
│   │   ├── DataContext.cs       # EF Core context
│   │   └── Repositories/        # Data access
│   ├── DTOs/                    # Data transfer objects
│   ├── Services/                # Business logic
│   └── SignalR/                 # Real-time hubs
└── client/                      # Frontend (Angular)
    └── src/app/
        ├── members/             # User profiles & matching
        ├── messages/            # Messaging system
        ├── admin/               # Admin panel
        ├── _services/           # Angular services
        ├── _guards/             # Route protection
        └── _models/             # TypeScript interfaces
```

## 🔧 Configuration

### Environment Variables

#### Backend
```bash
# Database
DATABASE_URL=postgresql://user:password@host:port/database

# JWT
TokenKey=your_secret_jwt_key_here

# Cloudinary
CloudinarySettings__CloudName=your_cloud_name
CloudinarySettings__ApiKey=your_api_key
CloudinarySettings__ApiSecret=your_api_secret
```

#### Frontend
```typescript
// environment.ts
export const environment = {
  production: false,
  apiUrl: 'https://localhost:5001/api/',
  hubUrl: 'https://localhost:5001/hubs/'
};
```

## 🚀 Deployment

### Using Fly.io

1. **Install Fly CLI**
   ```bash
   curl -L https://fly.io/install.sh | sh
   ```

2. **Login to Fly**
   ```bash
   fly auth login
   ```

3. **Deploy the application**
   ```bash
   fly deploy
   ```

### Using Docker

1. **Build the Docker image**
   ```bash
   docker build -t datingapp .
   ```

2. **Run the container**
   ```bash
   docker run -p 8080:8080 datingapp
   ```

## 🧪 Testing

### Backend Tests
```bash
cd API
dotnet test
```

### Frontend Tests
```bash
cd client
npm test
```

## 📊 Database Schema

### Core Entities
- **AppUser** - User profiles and authentication
- **Photo** - User photos with approval status
- **UserLike** - Like relationships between users
- **Message** - Chat messages between users
- **Group/Connection** - SignalR connection management

### Key Relationships
- Users can have multiple photos
- Users can like multiple other users
- Messages are exchanged between matched users
- Real-time connections are tracked for presence

## 🔒 Security Features

- **JWT Authentication** - Secure token-based authentication
- **Role-Based Authorization** - Granular permission system
- **CORS Configuration** - Controlled cross-origin requests
- **Input Validation** - Comprehensive data validation
- **SQL Injection Protection** - Entity Framework safeguards

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

If you encounter any issues or have questions:

1. Check the [Issues](https://github.com/your-repo/issues) page
2. Create a new issue with detailed information
3. Include error logs and steps to reproduce

## 🙏 Acknowledgments

- [ASP.NET Core](https://dotnet.microsoft.com/) - Backend framework
- [Angular](https://angular.io/) - Frontend framework
- [Bootstrap](https://getbootstrap.com/) - UI components
- [SignalR](https://dotnet.microsoft.com/apps/aspnet/signalr) - Real-time communication
- [Cloudinary](https://cloudinary.com/) - Cloud storage
- [PostgreSQL](https://www.postgresql.org/) - Database

---

**Note**: This application is currently deployed on Fly.io but may require server configuration updates. The codebase is production-ready and includes all essential dating platform features.
