<div align="center">
<img width="1200" height="475" alt="IFTU LMS Banner" src="https://github.com/user-attachments/assets/0aa67016-6eaf-458a-adb2-6e31a0763ed6" />
</div>

# IFTU LMS - National Digital Sovereign Education Center

A comprehensive Learning Management System built with React, Vite, and modern web technologies. This platform provides educators and students with an integrated solution for course management, assessments, interactive learning, and institutional administration.

**Project Status**: Active Development  
**Latest Version**: 0.0.0  
**Last Updated**: April 2026  

## 🚀 Quick Start

### Prerequisites
- Node.js 16.x or higher
- npm, yarn, or pnpm
- Git
- Supabase account
- Google Gemini API key

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Jemal-iftu-lms/IFTU-LMS.git
   cd IFTU-LMS
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Configure environment variables:**
   ```bash
   cp .env.example .env.development.local
   ```
   Update `.env.development.local` with your credentials

4. **Run the development server:**
   ```bash
   npm run dev
   ```
   
   The app runs at `http://localhost:3000`

## 📚 Documentation

- **[SETUP.md](SETUP.md)** - Complete setup and configuration guide
- **[DEPLOYMENT.md](DEPLOYMENT.md)** - Deployment procedures and best practices
- **[SETUP_CHECKLIST.md](SETUP_CHECKLIST.md)** - Configuration verification checklist

## 🏗️ Technology Stack

**Frontend:**
- React 19.2.4
- Vite 6.2.0 (Build tool)
- TypeScript 5.8
- Tailwind CSS
- Recharts (Data visualization)

**Backend:**
- Express.js 5.2.1 (API server)
- Node.js with TSX
- Supabase (PostgreSQL)

**AI & Services:**
- Google Gemini API
- Firebase (optional)
- Supabase Auth

**Deployment:**
- Vercel
- Firebase Hosting (optional)

## 📦 Project Structure

```
IFTU-LMS/
├── src/
│   ├── components/           # React components
│   ├── services/            # API services
│   ├── types.ts             # TypeScript types
│   ├── constants.tsx        # Application constants
│   └── [Components].tsx     # Feature components
├── public/                  # Static assets
├── dist/                    # Build output (generated)
├── server.ts               # Express server
├── vite.config.ts          # Vite configuration
├── tsconfig.json           # TypeScript config
├── vercel.json             # Vercel deployment config
├── firebase.json           # Firebase config
├── .env.example            # Environment template
├── package.json            # Dependencies
├── SETUP.md                # Setup guide
├── DEPLOYMENT.md           # Deployment guide
└── README.md               # This file
```

## 🎯 Key Features

### For Students
- **Course Viewer** - Access course materials
- **Study Hall** - Collaborative learning space
- **Exam Engine** - Take assessments and quizzes
- **Assignment Portal** - Submit and track assignments
- **Live Interview** - Interactive assessment sessions
- **Performance Hub** - Track academic progress
- **Certificate Portal** - View earned certificates

### For Teachers
- **TeacherDashboard** - Class management
- **Course Management** - Create and manage courses
- **Assignment Grading** - Review student submissions
- **Performance Analytics** - View class statistics
- **Student Management** - Manage student records

### For Administrators
- **Admin Dashboard** - System management
- **Campus Locator** - Location-based services
- **Leaderboard** - Student rankings
- **Payment Hub** - Transaction management
- **Report Card** - Generate reports
- **Feedback Widget** - Collect feedback

### AI-Powered Features
- **AI Tutor** - Intelligent tutoring system using Gemini API
- **Video Generator** - Create educational content
- **Smart Assessment** - AI-enhanced exam generation

## 🛠️ Build Commands

```bash
# Development
npm run dev              # Start development server with HMR

# Production
npm run build           # Create optimized production build
npm run preview         # Preview production build locally

# Code Quality
npm run lint            # Run TypeScript linter
npm run type-check      # Full type checking

# Utilities
npm start               # Run Express server
npm run clean           # Clean build artifacts
npm run vercel-build    # Vercel production build
```

## 🔐 Environment Configuration

Required environment variables (see `.env.example`):

```env
# Supabase Configuration
SUPABASE_URL=https://your-project.supabase.co
SUPABASE_ANON_KEY=your_anon_key

# Gemini API
GEMINI_API_KEY=your_gemini_api_key

# Application
VITE_BASE_PATH=/iftu-portal/
NODE_ENV=development
```

## 🚀 Deployment

### Deploy to Vercel

1. **Push to GitHub:**
   ```bash
   git push origin main
   ```

2. **Import project to Vercel:**
   - Go to https://vercel.com
   - Click "Import Project"
   - Select GitHub repository
   - Configure environment variables
   - Click Deploy

**For detailed deployment instructions, see [DEPLOYMENT.md](DEPLOYMENT.md)**

### Environment Variables (Vercel)
Set these in Vercel project settings:
- `SUPABASE_URL`
- `SUPABASE_ANON_KEY`
- `GEMINI_API_KEY`
- `VITE_BASE_PATH`

## 📊 API Endpoints

### Exam Validation
```
POST /api/validate-exam
Content-Type: application/json

Request:
{
  "title": "Exam Title",
  "subject": "Subject",
  "durationMinutes": 60,
  "questions": [...],
  "categories": [...]
}

Response:
{
  "valid": true,
  "errors": [] // if valid: false, contains error messages
}
```

## 🔧 Development Workflow

1. **Create feature branch:**
   ```bash
   git checkout -b feature/new-feature
   ```

2. **Run development server:**
   ```bash
   npm run dev
   ```

3. **Check types:**
   ```bash
   npm run type-check
   ```

4. **Build for testing:**
   ```bash
   npm run build
   npm run preview
   ```

5. **Commit and push:**
   ```bash
   git commit -m "feat: add new feature"
   git push origin feature/new-feature
   ```

6. **Create pull request on GitHub**

## 📱 Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

## 🐛 Troubleshooting

### Common Issues

**Port 3000 already in use:**
```bash
lsof -ti :3000 | xargs kill -9
npm run dev
```

**Dependencies issue:**
```bash
rm -rf node_modules package-lock.json
npm install
```

**Type errors:**
```bash
npm run type-check
```

**Build fails:**
```bash
npm run clean
npm install
npm run build
```

For more troubleshooting, see [SETUP.md](SETUP.md#troubleshooting)

## 📋 Project Roadmap

- [ ] Course recommendation system
- [ ] Advanced analytics dashboard
- [ ] Mobile application
- [ ] Offline mode support
- [ ] Advanced collaboration features
- [ ] Learning path customization
- [ ] Integration with third-party tools
- [ ] Enhanced AI features

## 🤝 Contributing

Contributions are welcome! Please:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Run type-check: `npm run type-check`
5. Commit with clear messages
6. Push to your fork
7. Create a pull request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🔗 Resources

- [Vite Documentation](https://vitejs.dev)
- [React Documentation](https://react.dev)
- [TypeScript Handbook](https://www.typescriptlang.org)
- [Supabase Documentation](https://supabase.com/docs)
- [Vercel Documentation](https://vercel.com/docs)
- [Google Gemini API](https://ai.google.dev)

## 📞 Support

For issues, questions, or suggestions:
1. Check [SETUP.md](SETUP.md) for setup help
2. Check [DEPLOYMENT.md](DEPLOYMENT.md) for deployment help
3. Review [SETUP_CHECKLIST.md](SETUP_CHECKLIST.md) for verification
4. Open an issue on GitHub

## 👥 Team

**IFTU LMS Development Team**
- Project: National Digital Sovereign Education Center
- Organization: IFTU (Institute For Tech University)
- Region: East Africa

## 📈 Stats

- **Total Components**: 20+
- **Services**: 5+ API services
- **Database Tables**: 8+
- **Configuration Files**: 7 optimized
- **Documentation**: 4 comprehensive guides

---

**Last Updated**: April 2026  
**Version**: 0.0.0  
**Status**: ✅ Active Development
