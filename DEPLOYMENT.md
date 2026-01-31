# 🚀 Deployment Guide

Complete guide for deploying your Glassmorphism Portfolio to various platforms.

## Table of Contents

- [GitHub Pages Deployment](#github-pages-deployment)
- [Netlify Deployment](#netlify-deployment)
- [Vercel Deployment](#vercel-deployment)
- [Traditional Hosting](#traditional-hosting)
- [Custom Domain Setup](#custom-domain-setup)
- [Performance Optimization](#performance-optimization)
- [Security Best Practices](#security-best-practices)

---

## GitHub Pages Deployment

### Step 1: Prepare Your Repository

```bash
# Initialize git repository
git init

# Add all files
git add .

# Commit changes
git commit -m "Initial commit: Glassmorphism portfolio"

# Rename branch to main
git branch -M main
```

### Step 2: Create GitHub Repository

1. Go to [GitHub](https://github.com/new)
2. Create a new repository (e.g., `portfolio` or `cv`)
3. Don't initialize with README (you already have one)

### Step 3: Push to GitHub

```bash
# Add remote origin
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git

# Push to GitHub
git push -u origin main
```

### Step 4: Enable GitHub Pages

1. Go to repository **Settings**
2. Navigate to **Pages** section (left sidebar)
3. Under "Source", select:
   - Branch: `main`
   - Folder: `/ (root)`
4. Click **Save**

### Step 5: Access Your Site

Your site will be available at:
```
https://YOUR_USERNAME.github.io/YOUR_REPO/
```

**⏱️ Deployment Time**: 2-5 minutes

### GitHub Pages Configuration

Add this to your repository settings for optimal performance:

```yaml
# .github/workflows/deploy.yml (optional for custom build process)
name: Deploy to GitHub Pages

on:
  push:
    branches: [ main ]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./
```

---

## Netlify Deployment

### Method 1: Git Integration (Recommended)

1. **Sign up/Login** to [Netlify](https://www.netlify.com/)

2. **New Site from Git**
   - Click "New site from Git"
   - Choose GitHub
   - Authorize Netlify
   - Select your repository

3. **Build Settings**
   ```
   Build command: (leave empty - static site)
   Publish directory: /
   ```

4. **Deploy**
   - Click "Deploy site"
   - Netlify will assign a random domain: `random-name-12345.netlify.app`

### Method 2: Drag & Drop

1. Zip your project files
2. Drag and drop to Netlify dashboard
3. Site will be live instantly

### Netlify Configuration

Create `netlify.toml` in root:

```toml
[build]
  publish = "/"
  command = ""

[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 200

[[headers]]
  for = "/*"
  [headers.values]
    X-Frame-Options = "DENY"
    X-XSS-Protection = "1; mode=block"
    X-Content-Type-Options = "nosniff"
    Referrer-Policy = "strict-origin-when-cross-origin"

[[headers]]
  for = "*.js"
  [headers.values]
    Cache-Control = "public, max-age=31536000, immutable"

[[headers]]
  for = "*.css"
  [headers.values]
    Cache-Control = "public, max-age=31536000, immutable"

[[headers]]
  for = "*.jpg"
  [headers.values]
    Cache-Control = "public, max-age=31536000, immutable"

[[headers]]
  for = "*.png"
  [headers.values]
    Cache-Control = "public, max-age=31536000, immutable"
```

**⏱️ Deployment Time**: 30-60 seconds

---

## Vercel Deployment

### Method 1: Vercel CLI

```bash
# Install Vercel CLI globally
npm install -g vercel

# Login to Vercel
vercel login

# Deploy
vercel

# For production deployment
vercel --prod
```

### Method 2: Git Integration

1. Go to [Vercel Dashboard](https://vercel.com/dashboard)
2. Click "New Project"
3. Import your GitHub repository
4. Configure:
   ```
   Framework Preset: Other
   Build Command: (leave empty)
   Output Directory: ./
   ```
5. Click "Deploy"

### Vercel Configuration

Create `vercel.json`:

```json
{
  "version": 2,
  "name": "portfolio",
  "builds": [
    {
      "src": "index.html",
      "use": "@vercel/static"
    }
  ],
  "routes": [
    {
      "src": "/(.*)",
      "dest": "/$1"
    }
  ],
  "headers": [
    {
      "source": "/(.*)",
      "headers": [
        {
          "key": "X-Content-Type-Options",
          "value": "nosniff"
        },
        {
          "key": "X-Frame-Options",
          "value": "DENY"
        },
        {
          "key": "X-XSS-Protection",
          "value": "1; mode=block"
        }
      ]
    },
    {
      "source": "/(.*).css",
      "headers": [
        {
          "key": "Cache-Control",
          "value": "public, max-age=31536000, immutable"
        }
      ]
    },
    {
      "source": "/(.*).js",
      "headers": [
        {
          "key": "Cache-Control",
          "value": "public, max-age=31536000, immutable"
        }
      ]
    }
  ]
}
```

**⏱️ Deployment Time**: 20-40 seconds

---

## Traditional Hosting

### Via FTP/SFTP

1. **Connect to your server**
   ```
   Host: ftp.yourwebsite.com
   Username: your_username
   Password: your_password
   Port: 21 (FTP) or 22 (SFTP)
   ```

2. **Upload files**
   - Upload all files to `public_html` or `www` directory
   - Ensure `index.html` is in the root

3. **Set permissions**
   ```
   Directories: 755
   Files: 644
   ```

### Via cPanel File Manager

1. Login to cPanel
2. Navigate to File Manager
3. Go to `public_html`
4. Upload files (or upload zip and extract)
5. Verify file permissions

### Apache Configuration (`.htaccess`)

Create `.htaccess` file:

```apache
# Enable HTTPS
<IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteCond %{HTTPS} off
    RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
</IfModule>

# Compression
<IfModule mod_deflate.c>
    AddOutputFilterByType DEFLATE text/html text/plain text/xml text/css text/javascript application/javascript
</IfModule>

# Browser Caching
<IfModule mod_expires.c>
    ExpiresActive On
    ExpiresByType text/css "access plus 1 year"
    ExpiresByType application/javascript "access plus 1 year"
    ExpiresByType image/jpeg "access plus 1 year"
    ExpiresByType image/png "access plus 1 year"
    ExpiresByType image/gif "access plus 1 year"
    ExpiresByType image/svg+xml "access plus 1 year"
</IfModule>

# Security Headers
<IfModule mod_headers.c>
    Header set X-Content-Type-Options "nosniff"
    Header set X-Frame-Options "DENY"
    Header set X-XSS-Protection "1; mode=block"
    Header set Referrer-Policy "strict-origin-when-cross-origin"
</IfModule>
```

---

## Custom Domain Setup

### For GitHub Pages

1. **Add custom domain in repository settings**
   - Go to Settings > Pages
   - Enter your custom domain
   - Save

2. **Configure DNS records**

   **Option A: Apex Domain (example.com)**
   ```
   Type: A
   Name: @
   Value: 185.199.108.153
   Value: 185.199.109.153
   Value: 185.199.110.153
   Value: 185.199.111.153
   ```

   **Option B: Subdomain (www.example.com)**
   ```
   Type: CNAME
   Name: www
   Value: YOUR_USERNAME.github.io
   ```

3. **Create CNAME file in repository root**
   ```
   echo "yourdomain.com" > CNAME
   git add CNAME
   git commit -m "Add custom domain"
   git push
   ```

### For Netlify

1. Go to Site Settings > Domain Management
2. Click "Add custom domain"
3. Enter your domain
4. Follow DNS configuration instructions
5. Netlify provides automatic HTTPS

### For Vercel

1. Go to Project Settings > Domains
2. Add your custom domain
3. Configure DNS:
   ```
   Type: A
   Name: @
   Value: 76.76.21.21
   
   Type: CNAME
   Name: www
   Value: cname.vercel-dns.com
   ```

---

## Performance Optimization

### Pre-Deployment Checklist

- [ ] **Minify CSS**
  ```bash
  # Using online tools or
  npx cssnano styles.css styles.min.css
  ```

- [ ] **Minify JavaScript**
  ```bash
  npx terser script.js -o script.min.js
  ```

- [ ] **Optimize Images**
  - Convert to WebP format
  - Compress images (TinyPNG, ImageOptim)
  - Use appropriate sizes

- [ ] **Enable Gzip/Brotli Compression**
  - Configured in server settings or `.htaccess`

- [ ] **Set Cache Headers**
  - CSS/JS: 1 year
  - Images: 1 year
  - HTML: no-cache

### Post-Deployment Verification

1. **Test with Lighthouse**
   ```bash
   # Chrome DevTools > Lighthouse
   # Run audit for Performance, Accessibility, Best Practices, SEO
   ```

2. **Check Mobile Responsiveness**
   - Chrome DevTools Device Mode
   - Real device testing

3. **Verify SSL Certificate**
   - Ensure HTTPS is working
   - No mixed content warnings

4. **Test Load Time**
   - Use GTmetrix, PageSpeed Insights
   - Target: < 3 seconds

---

## Security Best Practices

### Content Security Policy

Add to HTML `<head>`:

```html
<meta http-equiv="Content-Security-Policy" 
      content="default-src 'self'; 
               script-src 'self' 'unsafe-inline' https://cdnjs.cloudflare.com; 
               style-src 'self' 'unsafe-inline' https://fonts.googleapis.com https://cdnjs.cloudflare.com; 
               font-src 'self' https://fonts.gstatic.com https://cdnjs.cloudflare.com; 
               img-src 'self' data: https:; 
               connect-src 'self';">
```

### Security Headers

Ensure these headers are set:

```
X-Content-Type-Options: nosniff
X-Frame-Options: DENY
X-XSS-Protection: 1; mode=block
Referrer-Policy: strict-origin-when-cross-origin
Permissions-Policy: geolocation=(), microphone=(), camera=()
```

### HTTPS Enforcement

Always redirect HTTP to HTTPS:

```javascript
// In script.js
if (location.protocol !== 'https:' && location.hostname !== 'localhost') {
    location.replace(`https:${location.href.substring(location.protocol.length)}`);
}
```

---

## Continuous Deployment

### GitHub Actions for Automated Deployment

Create `.github/workflows/deploy.yml`:

```yaml
name: Deploy Portfolio

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  deploy:
    runs-on: ubuntu-latest
    
    steps:
    - name: Checkout code
      uses: actions/checkout@v2
    
    - name: Deploy to GitHub Pages
      uses: peaceiris/actions-gh-pages@v3
      if: github.ref == 'refs/heads/main'
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
        publish_dir: ./
```

---

## Troubleshooting

### Common Issues

**Issue**: Site not loading after deployment
- **Solution**: Clear browser cache, check DNS propagation

**Issue**: CSS/JS not loading
- **Solution**: Verify file paths, check console for errors

**Issue**: 404 errors on refresh
- **Solution**: Configure server for SPA (single-page application)

**Issue**: Slow loading times
- **Solution**: Optimize images, enable compression, use CDN

---

## Monitoring & Analytics

### Add Google Analytics

```html
<!-- Add to <head> -->
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_MEASUREMENT_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'GA_MEASUREMENT_ID');
</script>
```

### Add Microsoft Clarity

```html
<!-- Add to <head> -->
<script type="text/javascript">
    (function(c,l,a,r,i,t,y){
        c[a]=c[a]||function(){(c[a].q=c[a].q||[]).push(arguments)};
        t=l.createElement(r);t.async=1;t.src="https://www.clarity.ms/tag/"+i;
        y=l.getElementsByTagName(r)[0];y.parentNode.insertBefore(t,y);
    })(window, document, "clarity", "script", "YOUR_PROJECT_ID");
</script>
```

---

## Success Checklist

After deployment, verify:

- ✅ Site loads correctly on desktop
- ✅ Site loads correctly on mobile
- ✅ All links work (internal and external)
- ✅ Images load properly
- ✅ Animations work smoothly
- ✅ Forms submit correctly (if applicable)
- ✅ SSL certificate is valid
- ✅ Lighthouse score > 90 in all categories
- ✅ Social media preview works
- ✅ Contact methods are functional

---

**Need Help?** Contact Mohamed Salah

📲 WhatsApp: [+20 111 390 3070](https://wa.me/201113903070)
🌐 Portfolio: [moh222salah.github.io/cv](https://moh222salah.github.io/cv)
