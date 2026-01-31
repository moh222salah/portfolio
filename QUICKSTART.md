# ⚡ Quick Start Guide

Get your portfolio live in **under 10 minutes**!

## 🚀 Fastest Route to Live Website

### Option 1: GitHub Pages (5 minutes)

```bash
# 1. Initialize git
git init
git add .
git commit -m "Initial commit"

# 2. Create repo on GitHub.com (click "New Repository")

# 3. Push to GitHub
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git branch -M main
git push -u origin main

# 4. Enable GitHub Pages
# Go to: Settings > Pages > Source: main branch > Save

# ✅ Live at: https://YOUR_USERNAME.github.io/YOUR_REPO/
```

### Option 2: Netlify Drop (2 minutes)

1. Zip all project files
2. Go to [Netlify Drop](https://app.netlify.com/drop)
3. Drag and drop the zip file
4. ✅ Instant live URL!

---

## 📝 Essential Customizations (3 minutes)

### 1. Update Contact Info

**File**: `index.html`

Find and replace:
- `+20 111 390 3070` → Your phone number
- `https://wa.me/201113903070` → Your WhatsApp link
- `https://moh222salah.github.io/cv` → Your portfolio URL
- `Mohamed Salah` → Your name

### 2. Update Stats

**File**: `index.html` (Stats Section)

```html
<!-- Change these numbers to match your experience -->
<h3 class="stat-number" data-target="150">0</h3> <!-- Projects -->
<h3 class="stat-number" data-target="50">0</h3>  <!-- Clients -->
<h3 class="stat-number" data-target="8">0</h3>   <!-- Years -->
<h3 class="stat-number" data-target="30">0</h3>  <!-- Technologies -->
```

### 3. Change Colors (Optional)

**File**: `styles.css` (line 11)

```css
/* Find and change this line */
--primary-gradient: linear-gradient(135deg, #667eea 0%, #764ba2 100%);

/* Options: */
/* Teal/Green */
--primary-gradient: linear-gradient(135deg, #11998e 0%, #38ef7d 100%);

/* Orange/Pink */
--primary-gradient: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);

/* Blue/Cyan */
--primary-gradient: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
```

---

## 🧪 Test Locally

```bash
# Open directly
open index.html

# Or use a local server (recommended)
python -m http.server 8000
# Visit: http://localhost:8000
```

---

## 📱 Mobile Testing

1. Open Chrome DevTools (F12)
2. Click device toggle (Ctrl+Shift+M)
3. Test on different screen sizes

---

## ✅ Pre-Launch Checklist

- [ ] Updated all contact information
- [ ] Changed personal details
- [ ] Updated statistics
- [ ] Tested on desktop
- [ ] Tested on mobile
- [ ] All links work
- [ ] Colors look good

---

## 🎯 Next Steps

1. **Read** [README.md](README.md) for full documentation
2. **Customize** using [CUSTOMIZATION.md](CUSTOMIZATION.md)
3. **Deploy** with [DEPLOYMENT.md](DEPLOYMENT.md)

---

## 🆘 Need Help?

**Mohamed Salah** - Elite Full-Stack Developer

📲 WhatsApp: [+20 111 390 3070](https://wa.me/201113903070)
🌐 Portfolio: [moh222salah.github.io/cv](https://moh222salah.github.io/cv)

---

**That's it! You're ready to go live! 🚀**
