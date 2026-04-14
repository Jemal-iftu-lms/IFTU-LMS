# Deployment Guide - IFTU LMS

This guide covers deploying the IFTU LMS application to Vercel.

## Pre-Deployment Checklist

- [ ] All tests pass: `npm run type-check`
- [ ] No console errors in development build
- [ ] Environment variables are correctly configured
- [ ] Supabase credentials are valid
- [ ] Gemini API key is active
- [ ] Database migrations completed
- [ ] Code committed to Git repository

## Deployment Methods

### Method 1: Vercel CLI (Recommended)

1. **Install Vercel CLI**
   ```bash
   npm i -g vercel
   ```

2. **Login to Vercel**
   ```bash
   vercel login
   ```

3. **Deploy**
   ```bash
   vercel --prod
   ```

### Method 2: GitHub Integration

1. **Connect GitHub Repository**
   - Go to https://vercel.com
   - Click "New Project"
   - Select GitHub repository
   - Configure project settings

2. **Configure Build Settings**
   - Framework: Vite
   - Build Command: `npm run build`
   - Output Directory: `dist`
   - Install Command: `npm install`

3. **Set Environment Variables**
   In Vercel Project Settings → Environment Variables:
   ```
   SUPABASE_URL=https://your-project.supabase.co
   SUPABASE_ANON_KEY=your_anon_key
   GEMINI_API_KEY=your_gemini_key
   VITE_BASE_PATH=/iftu-portal/
   ```

4. **Deploy**
   - Push to main branch
   - Vercel automatically deploys

### Method 3: Manual Upload

1. **Build the project**
   ```bash
   npm run build
   ```

2. **Upload to Vercel**
   - Drag and drop `dist/` folder to Vercel
   - Or use Vercel CLI: `vercel --prod`

## Environment Variables Setup

### Production Variables (Vercel Dashboard)

1. Go to Project Settings
2. Click Environment Variables
3. Add the following:

```
SUPABASE_URL          - Your Supabase project URL
SUPABASE_ANON_KEY     - Your Supabase anonymous key
GEMINI_API_KEY        - Your Google Gemini API key
VITE_BASE_PATH        - /iftu-portal/ (or your custom path)
NODE_ENV              - production
```

### Verifying Variables

Check that variables are correctly set:
```bash
vercel env pull  # Pull production variables locally
```

## Domain Configuration

### Custom Domain

1. **In Vercel Dashboard**
   - Go to Project Settings → Domains
   - Add your custom domain
   - Update DNS records as instructed

2. **DNS Records** (Example for iftu-portal.edu.et)
   ```
   Type: CNAME
   Name: www
   Value: cname.vercel.sh
   ```

3. **Verify Domain**
   - Vercel automatically verifies after DNS propagates
   - This typically takes 5-48 hours

### Subdomain Configuration

For deployment at subdomain (e.g., portal.iftu.edu.et):

1. Add DNS record:
   ```
   Type: CNAME
   Name: portal
   Value: cname.vercel.sh
   ```

2. In vercel.json, update base path if needed:
   ```json
   "env": {
     "VITE_BASE_PATH": "/portal/"
   }
   ```

## Database Migrations

### Before First Deployment

1. **Create Supabase Project**
   - Go to https://supabase.com
   - Create new project
   - Create required tables

2. **Run Migrations**
   ```bash
   # Execute SQL migrations from supabase dashboard
   # Or use Supabase CLI if available
   ```

### After Deployment

1. **Verify Database Connection**
   - Check Supabase dashboard
   - Run test queries
   - Verify RLS policies

## Monitoring Deployment

### Vercel Deployment Logs

1. **View Logs**
   ```bash
   vercel logs
   ```

2. **Real-time Logs**
   - Dashboard → Deployments → Select deployment → Logs

### Production Monitoring

1. **Error Tracking**
   - Monitor console errors
   - Set up Sentry or similar service

2. **Performance Metrics**
   - Check Vercel Analytics
   - Monitor Core Web Vitals

3. **Database Health**
   - Check Supabase dashboard
   - Monitor query performance
   - Review connection logs

## Rollback Procedure

If deployment has issues:

### Using Vercel CLI
```bash
vercel rollback
```

### Using Vercel Dashboard
1. Go to Deployments
2. Click on previous stable version
3. Promote it as production

## Post-Deployment Tasks

1. **Verify Application**
   - Visit deployed URL
   - Test core functionality
   - Check console for errors

2. **Database Backup**
   ```bash
   # In Supabase dashboard
   - Enable automated backups
   - Create manual backup
   ```

3. **Security Check**
   - Update environment variables
   - Rotate API keys
   - Configure CORS if needed

4. **Performance Optimization**
   - Enable Vercel caching
   - Optimize images
   - Review bundle size

## Troubleshooting Deployment

### Build Failures

**Error: Cannot find module**
```bash
# Rebuild dependencies
rm -rf node_modules package-lock.json
npm install
npm run build
```

**Error: Environment variable undefined**
- Check Vercel dashboard for correct variable names
- Ensure variables are set for correct environment
- Redeploy after adding variables

### Runtime Errors

**Blank page or 404 errors**
- Check Vercel logs for errors
- Verify routes configuration
- Check vercel.json rewrite rules

**API connection errors**
- Verify Supabase credentials
- Check CORS configuration
- Ensure API is accessible from Vercel region

### Performance Issues

**Slow initial load**
- Check bundle size: `npm run build --report`
- Enable code splitting
- Optimize images

**Database connection slow**
- Check Supabase connection pool
- Review query performance
- Consider database indexing

## Scaling & Advanced Configuration

### Environment-Specific Configuration

Create different configurations for staging and production:

```json
{
  "env": {
    "STAGING": {
      "SUPABASE_URL": "https://staging.supabase.co",
      "SUPABASE_ANON_KEY": "staging_key"
    },
    "PRODUCTION": {
      "SUPABASE_URL": "https://prod.supabase.co",
      "SUPABASE_ANON_KEY": "prod_key"
    }
  }
}
```

### Regional Deployment

Configure specific Vercel regions:
```json
{
  "regions": ["sfo1", "iad1"]
}
```

## Maintenance & Updates

### Regular Tasks

- [ ] Weekly: Check error logs
- [ ] Monthly: Review performance metrics
- [ ] Quarterly: Security audit
- [ ] As needed: Update dependencies

### Updating the Application

1. **Create feature branch**
   ```bash
   git checkout -b feature/new-feature
   ```

2. **Make changes and test**
   ```bash
   npm run dev
   npm run type-check
   ```

3. **Push and create PR**
   ```bash
   git push origin feature/new-feature
   ```

4. **Merge to main**
   - Vercel automatically deploys on merge

## Support & Resources

- **Vercel Docs**: https://vercel.com/docs
- **Supabase Docs**: https://supabase.com/docs
- **Vite Guide**: https://vitejs.dev/guide/
- **React Docs**: https://react.dev

---

**Last Updated**: April 2026
**Deployment Version**: 1.0.0
