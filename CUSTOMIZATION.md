# 🎨 Customization Guide

Complete guide to personalizing your Glassmorphism Portfolio.

## Table of Contents

- [Quick Personalization](#quick-personalization)
- [Content Updates](#content-updates)
- [Design Customization](#design-customization)
- [Color Scheme](#color-scheme)
- [Typography](#typography)
- [Animations](#animations)
- [Adding New Sections](#adding-new-sections)
- [Advanced Customization](#advanced-customization)

---

## Quick Personalization

### 5-Minute Setup

1. **Update Personal Information** (index.html)
   - Replace "Mohamed Salah" with your name
   - Update phone number: `+20 111 390 3070`
   - Change portfolio link: `moh222salah.github.io/cv`
   - Update social media links

2. **Change Brand Colors** (styles.css)
   - Find `:root` section (line 8)
   - Modify `--primary-gradient`
   - Update `--accent-*` colors

3. **Update Stats** (index.html)
   - Modify numbers in Stats Section
   - Change `data-target` attributes

4. **Customize Content**
   - Replace hero title and description
   - Update service descriptions
   - Modify tech stack items

---

## Content Updates

### Hero Section

**Location**: `index.html` (lines ~80-140)

```html
<!-- Update Badge -->
<div class="hero-badge">
    <i class="fas fa-star"></i>
    <span>YOUR TAGLINE HERE</span>
</div>

<!-- Update Title -->
<h1 class="hero-title">
    Your Main Headline
    <span class="gradient-text">Highlighted Text</span>
</h1>

<!-- Update Description -->
<p class="hero-subtitle">
    Your professional description and value proposition...
</p>

<!-- Update Mini Stats -->
<div class="mini-stat">
    <span class="stat-number">10+</span>
    <span class="stat-label">Your Metric</span>
</div>
```

### Stats Section

**Location**: `index.html` (lines ~150-220)

```html
<!-- Update each stat card -->
<div class="stat-card reveal-element glass-card">
    <div class="stat-icon">
        <i class="fas fa-YOUR-ICON"></i>
    </div>
    <div class="stat-content">
        <!-- Change the number -->
        <h3 class="stat-number" data-target="200">0</h3>
        <p class="stat-label">Your Label</p>
        <span class="stat-badge">Your Badge</span>
    </div>
</div>
```

### Timeline/Process Section

**Location**: `index.html` (lines ~230-350)

```html
<!-- Update each phase -->
<div class="timeline-item reveal-element">
    <div class="timeline-number">01</div>
    <div class="timeline-content glass-card">
        <div class="timeline-icon">
            <i class="fas fa-YOUR-ICON"></i>
        </div>
        <h3>Your Phase Title</h3>
        <p>Your phase description...</p>
        <ul class="timeline-features">
            <li><i class="fas fa-check"></i> Feature 1</li>
            <li><i class="fas fa-check"></i> Feature 2</li>
            <li><i class="fas fa-check"></i> Feature 3</li>
        </ul>
    </div>
</div>
```

### Features Section

**Location**: `index.html` (lines ~360-480)

```html
<!-- Add or modify feature cards -->
<div class="feature-card reveal-element glass-card">
    <div class="feature-icon">
        <i class="fas fa-YOUR-ICON"></i>
    </div>
    <h3>Your Feature Title</h3>
    <p>Your feature description...</p>
    <div class="feature-tags">
        <span>Tag 1</span>
        <span>Tag 2</span>
        <span>Tag 3</span>
    </div>
</div>
```

### Tech Stack Section

**Location**: `index.html` (lines ~490-650)

```html
<!-- Add new technology category -->
<div class="tech-category reveal-element">
    <h3 class="tech-category-title">
        <i class="fas fa-YOUR-ICON"></i>
        Category Name
    </h3>
    <div class="tech-grid">
        <!-- Add technology items -->
        <div class="tech-item glass-card">
            <i class="fab fa-technology-icon"></i>
            <span>Technology Name</span>
        </div>
    </div>
</div>
```

### Contact Information

**Location**: `index.html` (lines ~660-700)

```html
<!-- Update WhatsApp link -->
<a href="https://wa.me/YOUR_PHONE_NUMBER" target="_blank">
    <i class="fab fa-whatsapp"></i>
    <span>WhatsApp: YOUR NUMBER</span>
</a>

<!-- Update Portfolio link -->
<a href="https://your-portfolio-url.com" target="_blank">
    <i class="fas fa-briefcase"></i>
    <span>View Portfolio</span>
</a>
```

---

## Design Customization

### Color Scheme

**Location**: `styles.css` (lines 8-45)

#### Change Primary Colors

```css
:root {
    /* Blue/Purple Theme (Default) */
    --primary-gradient: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    
    /* Alternative: Teal/Green */
    --primary-gradient: linear-gradient(135deg, #11998e 0%, #38ef7d 100%);
    
    /* Alternative: Orange/Red */
    --primary-gradient: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
    
    /* Alternative: Blue/Cyan */
    --primary-gradient: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
}
```

#### Adjust Glass Effect

```css
:root {
    /* More transparent */
    --glass-bg: rgba(255, 255, 255, 0.05);
    --glass-border: rgba(255, 255, 255, 0.12);
    
    /* More opaque */
    --glass-bg: rgba(255, 255, 255, 0.15);
    --glass-border: rgba(255, 255, 255, 0.25);
    
    /* Darker glass */
    --glass-bg: rgba(0, 0, 0, 0.2);
    --glass-border: rgba(255, 255, 255, 0.1);
}
```

#### Change Background

```css
.animated-background {
    /* Darker background */
    background: linear-gradient(135deg, #000000 0%, #1a1a2e 50%, #000000 100%);
    
    /* Lighter background */
    background: linear-gradient(135deg, #1a1f3a 0%, #2a3454 50%, #1a1f3a 100%);
    
    /* Custom gradient */
    background: linear-gradient(135deg, YOUR_COLOR_1 0%, YOUR_COLOR_2 50%, YOUR_COLOR_3 100%);
}
```

### Typography

**Location**: `styles.css` (lines 8-45, also in Google Fonts link in index.html)

#### Change Fonts

```html
<!-- In index.html <head>, replace Google Fonts link -->
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700;800;900&family=Montserrat:wght@400;500;600;700&display=swap" rel="stylesheet">
```

```css
/* In styles.css */
:root {
    --font-primary: 'Poppins', sans-serif;
    --font-headings: 'Montserrat', sans-serif;
}

body {
    font-family: var(--font-primary);
}

.section-title,
.hero-title {
    font-family: var(--font-headings);
}
```

#### Adjust Font Sizes

```css
:root {
    /* Larger text */
    --font-size-base: 18px;
    
    /* Smaller text */
    --font-size-base: 14px;
}

html {
    font-size: var(--font-size-base);
}

/* Or adjust specific elements */
.hero-title {
    font-size: 4rem; /* Make larger */
}

.section-title {
    font-size: 2.5rem; /* Make smaller */
}
```

---

## Animations

### Disable Animations

```css
/* Add this at the end of styles.css to disable all animations */
*,
*::before,
*::after {
    animation: none !important;
    transition: none !important;
}
```

### Adjust Animation Speed

```css
:root {
    /* Faster animations */
    --transition-fast: 0.1s ease;
    --transition-normal: 0.2s ease;
    --transition-slow: 0.3s ease;
    
    /* Slower animations */
    --transition-fast: 0.3s ease;
    --transition-normal: 0.5s ease;
    --transition-slow: 0.8s ease;
}
```

### Customize Specific Animations

```css
/* Change floating card animation */
.floating-card {
    animation: float 8s infinite ease-in-out; /* Slower */
}

/* Change gradient orb animation */
.gradient-orb {
    animation: float 15s infinite ease-in-out; /* Faster */
}

/* Disable particle animation */
.particles {
    display: none;
}
```

---

## Adding New Sections

### Template for New Section

```html
<!-- Add after existing sections in index.html -->
<section class="your-section" id="your-section">
    <div class="container">
        <!-- Section Header -->
        <div class="section-header reveal-element">
            <span class="section-badge">Your Badge</span>
            <h2 class="section-title">Your Section Title</h2>
            <p class="section-description">Your section description</p>
        </div>
        
        <!-- Section Content -->
        <div class="your-content-grid">
            <!-- Add your content here -->
        </div>
    </div>
</section>
```

```css
/* Add styling in styles.css */
.your-section {
    padding: 6rem 2rem;
    position: relative;
}

.your-content-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
}
```

### Example: Portfolio/Projects Section

```html
<section class="portfolio-section" id="portfolio">
    <div class="container">
        <div class="section-header reveal-element">
            <span class="section-badge">My Work</span>
            <h2 class="section-title">Featured Projects</h2>
            <p class="section-description">Showcasing excellence in development</p>
        </div>
        
        <div class="portfolio-grid">
            <div class="portfolio-item reveal-element glass-card">
                <div class="portfolio-image">
                    <img src="project1.jpg" alt="Project 1">
                </div>
                <div class="portfolio-content">
                    <h3>Project Title</h3>
                    <p>Project description...</p>
                    <div class="portfolio-tags">
                        <span>React</span>
                        <span>Node.js</span>
                    </div>
                    <a href="#" class="btn btn-primary">View Project</a>
                </div>
            </div>
        </div>
    </div>
</section>
```

```css
.portfolio-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
    gap: 2rem;
}

.portfolio-item {
    padding: 0;
    overflow: hidden;
}

.portfolio-image {
    width: 100%;
    height: 250px;
    overflow: hidden;
}

.portfolio-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform var(--transition-normal);
}

.portfolio-item:hover .portfolio-image img {
    transform: scale(1.1);
}

.portfolio-content {
    padding: 2rem;
}
```

---

## Advanced Customization

### Custom Cursor Effect

```html
<!-- Add to body in index.html -->
<div class="cursor-dot"></div>
<div class="cursor-outline"></div>
```

```css
/* Add to styles.css */
.cursor-dot,
.cursor-outline {
    pointer-events: none;
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    border-radius: 50%;
    z-index: 10000;
}

.cursor-dot {
    width: 8px;
    height: 8px;
    background: var(--accent-primary);
}

.cursor-outline {
    width: 30px;
    height: 30px;
    border: 2px solid var(--accent-primary);
    transition: transform 0.15s ease-out;
}
```

```javascript
// Add to script.js
document.addEventListener('mousemove', (e) => {
    const cursorDot = document.querySelector('.cursor-dot');
    const cursorOutline = document.querySelector('.cursor-outline');
    
    cursorDot.style.left = e.clientX + 'px';
    cursorDot.style.top = e.clientY + 'px';
    
    cursorOutline.style.left = e.clientX + 'px';
    cursorOutline.style.top = e.clientY + 'px';
});
```

### Dark/Light Mode Toggle

```html
<!-- Add to navbar in index.html -->
<button class="theme-toggle" id="themeToggle" aria-label="Toggle Theme">
    <i class="fas fa-moon"></i>
</button>
```

```css
/* Add to styles.css */
[data-theme="light"] {
    --bg-primary: #f5f5f5;
    --bg-secondary: #ffffff;
    --text-primary: #1a1a1a;
    --text-secondary: rgba(0, 0, 0, 0.8);
    --glass-bg: rgba(0, 0, 0, 0.05);
}

.theme-toggle {
    background: var(--glass-bg);
    border: 1px solid var(--glass-border);
    color: var(--text-primary);
    width: 40px;
    height: 40px;
    border-radius: 50%;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all var(--transition-normal);
}
```

```javascript
// Function already included in script.js
// Just uncomment initThemeToggle() in initializeApp()
```

### Scroll Progress Bar

```html
<!-- Add after opening body tag -->
<div class="scroll-progress" id="scrollProgress"></div>
```

```css
.scroll-progress {
    position: fixed;
    top: 0;
    left: 0;
    width: 0;
    height: 4px;
    background: var(--primary-gradient);
    z-index: 10000;
    transition: width 0.1s ease;
}
```

```javascript
// Function already included in script.js
// Just uncomment initScrollProgress() in initializeApp()
```

---

## Testing Your Changes

### Local Testing

1. **Open in browser**: Double-click `index.html`
2. **Use local server** (recommended):
   ```bash
   python -m http.server 8000
   # Visit: http://localhost:8000
   ```

### Browser DevTools

- **Chrome DevTools**: F12 or Ctrl+Shift+I (Cmd+Option+I on Mac)
- **Responsive Design Mode**: Ctrl+Shift+M (Cmd+Option+M on Mac)
- **Inspect Element**: Right-click > Inspect

### Cross-Browser Testing

Test on:
- Chrome/Edge
- Firefox
- Safari (if on Mac)
- Mobile browsers

---

## Performance Tips

### Optimize Images

```bash
# Convert to WebP
cwebp input.jpg -q 80 -o output.webp

# Compress PNG
pngquant image.png --output compressed.png
```

### Minify CSS

```bash
npx cssnano styles.css styles.min.css
```

### Minify JavaScript

```bash
npx terser script.js -o script.min.js
```

---

## Common Customizations

### Change Navigation Style

```css
/* Transparent navigation */
.navbar {
    background: transparent;
}

.navbar.scrolled {
    background: rgba(10, 14, 39, 0.98);
}

/* Solid navigation */
.navbar {
    background: var(--bg-primary);
    box-shadow: var(--shadow-md);
}
```

### Adjust Section Spacing

```css
/* More spacing */
section {
    padding: 8rem 2rem;
}

/* Less spacing */
section {
    padding: 4rem 2rem;
}
```

### Change Button Styles

```css
/* Rounded buttons */
.btn {
    border-radius: 50px;
}

/* Sharp buttons */
.btn {
    border-radius: 4px;
}

/* Larger buttons */
.btn {
    padding: 1.2rem 2.5rem;
    font-size: 1.1rem;
}
```

---

## Need Help?

If you need assistance with customization:

📲 **WhatsApp**: [+20 111 390 3070](https://wa.me/201113903070)
🌐 **Portfolio**: [moh222salah.github.io/cv](https://moh222salah.github.io/cv)

---

**Happy Customizing! 🎨**
