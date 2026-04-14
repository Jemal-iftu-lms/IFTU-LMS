# IFTU LMS - Project Setup Guide

This document provides a comprehensive setup guide for the IFTU LMS (National Digital Sovereign Education Center) project.

## Project Overview

- **Name**: IFTU-LMS - National Digital Sovereign Education Center
- **Type**: React + Vite SPA with Express backend
- **Framework**: Vite, React 19
- **Database**: Supabase (PostgreSQL)
- **Authentication**: Supabase Auth + Custom
- **AI Integration**: Google Gemini API
- **Deployment**: Vercel

## Prerequisites

- Node.js 16.x or higher
- npm, yarn, or pnpm
- Git
- Supabase account
- Google Gemini API key (for AI features)

## Installation Steps

### 1. Clone the Repository
```bash
git clone https://github.com/Jemal-iftu-lms/IFTU-LMS.git
cd IFTU-LMS
```

### 2. Install Dependencies
```bash
npm install
# or
yarn install
# or
pnpm install
```

### 3. Environment Configuration

Copy the `.env.example` file to `.env.development.local`:

```bash
cp .env.example .env.development.local
```

Update the following environment variables:

```env
# Supabase Configuration
SUPABASE_URL=https://blkxqartwbmjmkvyelzq.supabase.co
SUPABASE_ANON_KEY=your_supabase_anon_key

# Gemini API
GEMINI_API_KEY=your_gemini_api_key

# Application
VITE_BASE_PATH=/iftu-portal/
NODE_ENV=development
```

### 4. Development Server

Start the development server:

```bash
npm run dev
```

The application will be available at:
- Frontend: `http://localhost:3000`
- API Endpoints: `http://localhost:3000/api/*`

### 5. Building for Production

```bash
npm run build
npm run preview
```

This creates an optimized production build in the `dist/` directory.

## File Structure

```
IFTU-LMS/
├── src/
│   ├── components/          # React components
│   ├── pages/              # Page components
│   ├── services/           # API services
│   ├── utils/              # Utility functions
│   └── types.ts            # TypeScript types
├── public/                 # Static assets
├── dist/                   # Build output (generated)
├── server.ts              # Express server
├── vite.config.ts         # Vite configuration
├── tsconfig.json          # TypeScript configuration
├── tailwind.config.js     # Tailwind CSS configuration
├── vercel.json            # Vercel deployment config
├── firebase.json          # Firebase configuration (optional)
├── package.json           # Dependencies and scripts
└── README.md              # Project documentation
```

## Key Components

### Pages
- **AdminDashboard**: Admin panel for system management
- **StudentProfile**: Student profile and settings
- **TeacherDashboard**: Teacher management interface
- **CourseViewer**: Course content display
- **ExamEngine**: Exam creation and management
- **PaymentPortal**: Payment processing
- **LiveInterviewer**: Live interview system
- **CampusLocator**: Campus location finder
- **CertificatePortal**: Certificate management

### Services
- **supabaseClient.ts**: Supabase database client
- **geminiService.ts**: Google Gemini API integration
- **dbService.ts**: Database operations
- **validationService.ts**: Input validation
- **firebase.ts**: Firebase integration (optional)

## Configuration Details

### Vercel Configuration (vercel.json)
- Framework: Vite
- Build Command: `npm run build`
- Dev Command: `npm run dev`
- Output Directory: `dist/`
- Environment variables configured for production

### TypeScript Configuration (tsconfig.json)
- Target: ES2022
- Strict mode enabled
- Module resolution: bundler
- Path aliases configured for imports

### Vite Configuration (vite.config.ts)
- React plugin enabled
- HMR disabled for development (remote dev)
- Environment variables loaded
- Port: 3000

## Database Setup

### Supabase Tables
The following tables should be created in Supabase:

- `users` - User accounts
- `courses` - Course information
- `students` - Student records
- `exams` - Exam data
- `assignments` - Assignment records
- `submissions` - Student submissions
- `certificates` - Certificate data
- `payments` - Payment transactions

See `supabaseClient.ts` for table schema details.

## API Endpoints

### Express Server Routes

```
POST /api/validate-exam
- Validates exam configuration
- Request body: { title, subject, questions, durationMinutes, categories }
- Response: { valid: boolean, errors?: string[] }
```

## Deployment

### Vercel Deployment

1. Push your code to GitHub:
```bash
git push origin main
```

2. Import project to Vercel:
- Go to https://vercel.com
- Click "Import Project"
- Select GitHub repository
- Configure environment variables
- Deploy

### Environment Variables (Vercel)
Set these in Vercel project settings:
- `SUPABASE_URL`
- `SUPABASE_ANON_KEY`
- `GEMINI_API_KEY`
- `VITE_BASE_PATH`

## Development Workflow

### Running Tests
```bash
# Type checking
npm run type-check

# Lint code
npm run lint
```

### Building
```bash
# Development build
npm run build

# Production preview
npm run preview
```

### Database Operations
- Access Supabase dashboard: https://app.supabase.com
- View/manage data in real-time
- Configure Row Level Security (RLS) policies
- Set up database backups

## Troubleshooting

### Common Issues

1. **Port 3000 already in use**
   ```bash
   # Kill process on port 3000
   lsof -ti :3000 | xargs kill -9
   ```

2. **Missing environment variables**
   - Ensure `.env.development.local` is created
   - Copy values from `.env.example`
   - Verify Supabase credentials

3. **Supabase connection errors**
   - Check SUPABASE_URL format (must be HTTPS)
   - Verify SUPABASE_ANON_KEY is correct
   - Check network connectivity

4. **Vite build issues**
   ```bash
   rm -rf node_modules package-lock.json
   npm install
   npm run build
   ```

## Performance Optimization

- Enable Vite compression in production
- Use lazy loading for routes
- Implement code splitting
- Optimize images and assets
- Enable browser caching headers

## Security Considerations

- Never commit `.env.development.local` or `.env.production.local`
- Use Row Level Security (RLS) in Supabase
- Validate all user inputs
- Implement rate limiting for API endpoints
- Use HTTPS in production
- Rotate API keys regularly
- Implement CSRF protection for forms

## Monitoring & Logging

- Check Vercel deployment logs
- Monitor Supabase logs in dashboard
- Set up error tracking (Sentry recommended)
- Review performance metrics

## Support & Resources

- **Vite Documentation**: https://vitejs.dev
- **React Documentation**: https://react.dev
- **Supabase Documentation**: https://supabase.com/docs
- **Google Gemini API**: https://ai.google.dev
- **Vercel Documentation**: https://vercel.com/docs
- **TypeScript**: https://www.typescriptlang.org

## Contributors

See CONTRIBUTORS.md for team information.

## License

See LICENSE file for licensing information.

---

**Last Updated**: April 2026
**Version**: 1.0.0
