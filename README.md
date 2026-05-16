# Fuel Management System

A comprehensive, modern, and scalable solution for managing fuel stations, bookings, and user operations across multiple platforms. The system includes a robust backend API, web-based admin dashboard, and mobile applications for seamless fuel management.

## Demo Video

[![Watch the Loom walkthrough](https://cdn.loom.com/sessions/thumbnails/39617daace92433c94defa692ca21ea9-with-play.png)](https://www.loom.com/share/39617daace92433c94defa692ca21ea9)

Click the image to watch the full system walkthrough on Loom.

## 🎯 Project Overview

The Fuel Management System is an integrated platform designed to revolutionize fuel distribution and consumption management. It provides administrators with complete control over fuel stations, enables efficient booking systems with real-time queue management, and offers users convenient access to fuel services.

**System Architecture:**

- **Backend API**: RESTful service with TypeScript, Express.js, PostgreSQL
- **Admin Web Dashboard**: Next.js admin interface for system management
- **Mobile App**: React Native/Expo cross-platform application for users

---

## 📦 Project Structure

```
fuel-management-system/
├── fuel-backend/                    # REST API Server
│   ├── src/
│   │   ├── index.ts                 # Entry point
│   │   ├── controllers/             # Request handlers
│   │   ├── routes/                  # API endpoints
│   │   ├── middleware/              # Custom middleware
│   │   ├── db/                      # Database schema & migrations
│   │   └── utils/                   # Utility functions
│   ├── drizzle/                     # Database migrations
│   ├── package.json
│   └── README.md                    # Backend documentation
│
├── fuel-admin-frontend/             # Admin Dashboard
│   ├── app/                         # Next.js app directory
│   ├── components/                  # React components
│   ├── lib/                         # Utility functions
│   ├── store/                       # State management
│   ├── public/                      # Static assets
│   ├── package.json
│   └── README.md                    # Frontend documentation
│
└── fuel-mobile/                     # Mobile Application
    ├── app/                         # Expo app directory
    ├── components/                  # React Native components
    ├── screens/                     # Screen components
    ├── services/                    # API services
    ├── stores/                      # State management
    ├── assets/                      # Images & assets
    ├── package.json
    └── README.md                    # Mobile documentation
```

---

## 🌐 Live Deployments

### Admin Frontend

- **Production URL**: https://fuel-admin-frontend.vercel.app/

- **Admin Frontend repository**:(https://github.com/mame534424/fuel-admin-frontend)

- **Purpose**: Administrative dashboard for managing stations,
  bookings, users, and analytics.

### Backend API

-**Backend Repository**(https://github.com/mame534424/fuel-management-backend/)

- **Production URL**: integrated on the frontend
- **Purpose**: Core API for authentication, station management, bookings, and fuel inventory.

### Mobile App

- **Mobile App repository**(https://github.com/mame534424/e-fuel-mobile)

- **Deployment Status**: In progress / future release
- **Purpose**: Mobile experience for users to discover stations, create bookings, and track queues.

---

## 🚀 Quick Start Guide

### Prerequisites

- Node.js v18+
- npm or yarn
- PostgreSQL (for backend)
- Git

### Clone the Repository

```bash
git clone <repository-url>
cd fuel-management-system
```

### 1. Set Up Backend

```bash
cd fuel-backend

# Install dependencies
npm install

# Create .env file
cat > .env << EOF
DATABASE_URL=postgresql://username:password@localhost:5432/fuel_db
PORT=3000
JWT_SECRET=your_jwt_secret_key
NODE_ENV=development
EOF

# Run database migrations
npm run seed
npm run seed:fuel

# Start development server
npm run dev
```

Backend will be available at: `http://localhost:3000`

### 2. Set Up Admin Frontend

```bash
cd ../fuel-admin-frontend

# Install dependencies
npm install

# Create .env.local file
cat > .env.local << EOF
NEXT_PUBLIC_API_URL=http://localhost:3000
NEXT_PUBLIC_APP_NAME=Fuel Management System
EOF

# Start development server
npm run dev
```

Admin dashboard will be available at: `http://localhost:3001` (or next available port)

### 3. Set Up Mobile App

```bash
cd ../fuel-mobile

# Install dependencies
npm install

# Create .env file (if needed)
# Configure API endpoint

# Start Expo development server
npm start

# Choose: i (iOS), a (Android), or scan QR code with Expo Go
```

---

## 🛠️ Technology Stack

### Backend

| Technology  | Version | Purpose               |
| ----------- | ------- | --------------------- |
| Express.js  | ^5.2.1  | Web framework         |
| TypeScript  | ^6.0.3  | Type safety           |
| PostgreSQL  | Latest  | Database              |
| Drizzle ORM | ^0.45.2 | Database ORM          |
| JWT         | ^9.0.3  | Authentication        |
| bcrypt      | ^6.0.0  | Password hashing      |
| CORS        | ^2.8.6  | Cross-origin requests |

### Frontend (Admin)

| Technology   | Version | Purpose          |
| ------------ | ------- | ---------------- |
| Next.js      | ^16.2.4 | React framework  |
| React        | ^19.2.4 | UI library       |
| TypeScript   | ^5      | Type safety      |
| Tailwind CSS | ^4      | Styling          |
| Zustand      | ^5.0.12 | State management |
| Axios        | ^1.15.1 | HTTP client      |
| Lucide React | ^1.8.0  | Icons            |

### Mobile

| Technology   | Version | Purpose                   |
| ------------ | ------- | ------------------------- |
| React Native | Latest  | Mobile framework          |
| Expo         | Latest  | Development platform      |
| TypeScript   | Latest  | Type safety               |
| NativeWind   | Latest  | Tailwind for React Native |
| Zustand      | ^5.0.12 | State management          |
| Axios        | Latest  | HTTP client               |

---

## 📋 Database Schema

### Core Entities

**Users**

- Authentication and role management
- Supports multiple roles: Admin, SubAdmin, User
- Secure password storage with bcrypt

**Stations**

- Fuel station locations and details
- GPS coordinates for mapping
- Status management (active/inactive)
- Owner assignment to sub-admins

**Fuel Types**

- Available fuel types catalog
- (e.g., Premium Petrol, Regular Petrol, Diesel)

**Station Fuel**

- Inventory tracking per station
- Quantity monitoring
- Availability status

**Bookings**

- Fuel booking records
- Queue management with queue numbers
- Multiple status states
- Support for both registered users and guests

**Station Queue Counter**

- Daily queue numbering
- Per-station queue tracking

---

## 🔐 Security Features

### Authentication

- **JWT-based**: Token-based authentication
- **Password Security**: Bcrypt hashing for passwords
- **Token Management**: Automatic token refresh mechanism
- **Session Handling**: Secure session management

### Authorization

- **Role-Based Access Control (RBAC)**
  - Admin: Full system access
  - SubAdmin: Station management
  - User: Booking operations
  - Guest: Limited access

### API Security

- CORS configuration for authorized domains
- Environment variable protection
- Middleware-based request validation
- Secure error handling (no sensitive info exposure)

---

## 📡 API Documentation

For detailed API documentation, see [Backend README](./fuel-backend/README.md)

### Main API Endpoints

#### Authentication

```
POST   /auth/signup        - Register new user
POST   /auth/signin        - Login user
```

#### Stations

```
POST   /stations/create    - Create new station (Admin)
```

#### Bookings

```
POST   /bookings/          - Create booking
GET    /bookings/station/:id - Get station bookings
PATCH  /bookings/:id/complete - Complete booking
PATCH  /bookings/:id/cancel   - Cancel booking
```

#### Admin Operations

```
POST   /admin/subadmin     - Create sub-admin
PATCH  /admin/assign-station - Assign station
GET    /admin/stats        - Get statistics
GET    /admin/stations     - Get all stations
PATCH  /admin/:id/toggle-status - Toggle station status
```

#### Manager Operations

```
POST   /manager/fuel-type  - Create fuel type
POST   /manager/station-fuel - Add station fuel
PATCH  /manager/update-station-fuel - Update fuel quantity
GET    /manager/station-status - Get station status
GET    /manager/fuel-types - Get all fuel types
```

---

## 🎯 Key Features

### For Administrators

- ✅ Comprehensive system dashboard
- ✅ Station creation and management
- ✅ Sub-admin user management
- ✅ System-wide analytics and reporting
- ✅ Real-time booking management
- ✅ Fuel inventory tracking
- ✅ User activity monitoring

### For Station Managers

- ✅ Station-specific dashboard
- ✅ Booking queue management
- ✅ Fuel inventory management
- ✅ Customer queue tracking
- ✅ Booking status updates
- ✅ Fuel type configuration

### For Users

- ✅ Browse fuel stations
- ✅ View real-time fuel availability
- ✅ Make fuel bookings
- ✅ Track booking status
- ✅ View booking history
- ✅ Locate nearest stations
- ✅ Track queue position

---

## 🎨 User Interfaces

### Admin Dashboard

- Professional, intuitive interface
- Real-time statistics and metrics
- Drag-and-drop station assignment
- Responsive design for all devices
- Dark mode support

### Mobile App

- User-friendly booking interface
- Real-time station discovery
- Map integration
- Booking history
- Payment integration ready
- Cross-platform (iOS/Android)

---

## 🚀 Deployment

### Backend Deployment

```bash
cd fuel-backend
npm run build
npm start
```

### Frontend Deployment

```bash
cd fuel-admin-frontend
npm run build
npm start
```

For detailed deployment instructions, refer to individual project READMEs.

---

## 🧪 Testing & Development

### Development Workflow

1. Start backend: `npm run dev` (from fuel-backend)
2. Start frontend: `npm run dev` (from fuel-admin-frontend)
3. Start mobile: `npm start` (from fuel-mobile)

### Database Management

```bash
cd fuel-backend

# Run migrations
npm run seed

# Seed fuel types
npm run seed:fuel

# Generate new migrations
npx drizzle-kit generate:pg

# Apply migrations
npx drizzle-kit push:pg
```

---

## 📖 Documentation

Each project module has its own detailed README:

- **[Backend API Documentation](./fuel-backend/README.md)**
  - API endpoints reference
  - Database schema details
  - Setup instructions
  - Authentication flow

- **[Admin Frontend Documentation](./fuel-admin-frontend/README.md)**
  - Component library
  - Page routes
  - State management
  - Deployment guide

- **[Mobile App Documentation](./fuel-mobile/README.md)**
  - Feature overview
  - Installation steps
  - Screen descriptions
  - Integration guide

---

## 🔧 Environment Variables

### Backend (.env)

```
DATABASE_URL=postgresql://user:password@localhost:5432/fuel_db
PORT=3000
JWT_SECRET=your_jwt_secret_key_here
NODE_ENV=development
```

### Frontend (.env.local)

```
NEXT_PUBLIC_API_URL=http://localhost:3000
NEXT_PUBLIC_APP_NAME=Fuel Management System
```

### Mobile (.env)

```
EXPO_PUBLIC_API_URL=http://your-backend-url
EXPO_PUBLIC_API_TIMEOUT=30000
```

---

## 🤝 Contributing

We welcome contributions! Please follow these guidelines:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Code Standards

- Use TypeScript for all new code
- Follow project naming conventions
- Write meaningful commit messages
- Test changes before submitting
- Update documentation accordingly

---

## 🐛 Common Issues & Troubleshooting

### Backend Won't Connect to Database

```bash
# Check PostgreSQL is running
# Verify DATABASE_URL in .env
# Ensure database exists
```

### CORS Errors

- Backend CORS is configured in `index.ts`
- Verify `NEXT_PUBLIC_API_URL` in frontend `.env.local`
- Ensure backend API_URL matches frontend configuration

### Module Not Found Errors

```bash
# Clear node_modules and reinstall
rm -rf node_modules package-lock.json
npm install
```

### Port Already in Use

```bash
# Change the port in environment or use --port flag
npm run dev -- -p 3001
```

---

## 📊 System Architecture

```
┌─────────────────────────────────────────────────────────┐
│                   FUEL MANAGEMENT SYSTEM                 │
└─────────────────────────────────────────────────────────┘
           │                        │                   │
      ┌────▼────┐             ┌────▼────┐        ┌────▼────┐
      │  Mobile  │             │  Admin   │        │ Backend  │
      │   App    │             │Dashboard │        │   API    │
      │(Expo)    │             │(Next.js) │        │(Express) │
      └────┬────┘             └────┬────┘        └────┬────┘
           │                        │                   │
           └────────────────────────┼───────────────────┘
                                    │
                             ┌──────▼──────┐
                             │ PostgreSQL   │
                             │  Database    │
                             └──────────────┘
```

---

## 📞 Support & Contact

For issues, questions, or suggestions:

- **Email**: support@fuelmanagementsystem.com
- **Issues**: Create an issue in the repository
- **Documentation**: Check individual project READMEs

---

## 📝 License

This project is licensed under the ISC License - see individual projects for details.

---

## 🎯 Roadmap

### Phase 1 (Current)

- ✅ Core API development
- ✅ Admin dashboard
- ✅ Mobile app foundation
- ✅ Basic booking system

### Phase 2 (Planned)

- [ ] Payment gateway integration
- [ ] Real-time notifications
- [ ] Advanced analytics
- [ ] Multi-language support

### Phase 3 (Future)

- [ ] AI-based demand prediction
- [ ] Loyalty program
- [ ] Subscription management
- [ ] API rate limiting

---

## 👥 Team

Built with ❤️ by the Fuel Management System Development Team

---

## 🙏 Acknowledgments

- Express.js community
- Next.js framework
- React Native community
- Drizzle ORM team
- All contributors and testers

---

**Project Status**: Active Development  
**Last Updated**: May 13, 2026  
**Version**: 1.0.0 (Beta)

---

**Quick Links:**

- [Backend Repository](https://github.com/mame534424/fuel-management-backend/)
- [Admin Frontend repository](https://github.com/mame534424/fuel-admin-frontend)
- [Mobile App repository](https://github.com/mame534424/e-fuel-mobile)
