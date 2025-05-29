# 🚀 Wacky Flip Game - Deployment Guide

This guide will help you deploy the **Wacky Flip Game** website with full analytics integration.

## 📋 Prerequisites

- **Node.js** (v16 or higher)
- **npm** or **yarn**
- **Vercel** account (for deployment and analytics)
- **Google Analytics** account (for GA tracking)

## ⚡ Quick Start

### 1. Clone and Setup

```bash
# Clone the repository
git clone https://github.com/Richard-Fu/wackyflipgame.git
cd wackyflipgame

# Install dependencies
npm install

# Start local development server
npm run dev
```

### 2. Local Development

The game will be available at `http://localhost:3000` or similar port shown in terminal.

## 🔧 Analytics Configuration

### Google Analytics Setup

1. **Create GA4 Property**:

   - Go to [Google Analytics](https://analytics.google.com)
   - Create a new GA4 property
   - Copy your Measurement ID (format: G-XXXXXXXXX)

2. **Update Configuration**:
   - Replace `G-GGT9J10SJH` in `index.html` with your Measurement ID
   - Located in the `<head>` section

```html
<!-- Google tag (gtag.js) -->
<script
  async
  src="https://www.googletagmanager.com/gtag/js?id=YOUR_GA_ID"
></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag() {
    dataLayer.push(arguments);
  }
  gtag("js", new Date());
  gtag("config", "YOUR_GA_ID");
</script>
```

### Vercel Analytics Setup

1. **Deploy to Vercel**:

```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel --prod
```

2. **Enable Analytics**:

   - Go to your Vercel dashboard
   - Select your project
   - Navigate to Analytics tab
   - Enable Analytics for your project

3. **Verify Integration**:
   - The `@vercel/analytics` package is already configured
   - Analytics will automatically start tracking after deployment

## 🌐 Domain Configuration

### Custom Domain Setup

1. **Add Domain in Vercel**:

   - Go to Project Settings → Domains
   - Add your custom domain (e.g., `wackyflipgame.me`)

2. **Update URLs**:
   - Update `sitemap.xml` with your domain
   - Update canonical URLs in `index.html`
   - Update any hardcoded domain references

### SSL Certificate

Vercel automatically provides SSL certificates for all domains.

## 📊 Analytics Events

The following events are automatically tracked:

### Game Events

- `page_view` - Initial page load
- `game_loaded` - Game iframe successfully loaded
- `game_rated` - User submits a rating
- `comment_posted` - User submits a comment
- `faq_interaction` - User opens/closes FAQ items

### Event Data Structure

```javascript
// Example event tracking
trackEvent("game_rated", {
  rating: 5,
  game: "wacky_flip",
});

trackEvent("comment_posted", {
  game: "wacky_flip",
  comment_length: 150,
});
```

## 🔍 SEO Configuration

### Search Console Setup

1. **Add Property**:

   - Go to [Google Search Console](https://search.google.com/search-console)
   - Add your domain as a property

2. **Submit Sitemap**:
   - Upload `sitemap.xml` to Search Console
   - URL: `https://yourdomain.com/sitemap.xml`

### robots.txt

The `robots.txt` file is already configured to:

- Allow all search engines
- Point to your sitemap
- Set appropriate crawl delays

## 📈 Performance Optimization

### Core Web Vitals

The site is optimized for:

- **LCP** (Largest Contentful Paint) - Game loads quickly
- **FID** (First Input Delay) - Responsive interactions
- **CLS** (Cumulative Layout Shift) - Stable layout

### Mobile Optimization

- Responsive design for all screen sizes
- Touch-friendly game controls
- Optimized game frame for mobile devices

## 🚀 Deployment Checklist

- [ ] Clone repository
- [ ] Install dependencies (`npm install`)
- [ ] Update Google Analytics ID
- [ ] Test locally (`npm run dev`)
- [ ] Deploy to Vercel (`vercel --prod`)
- [ ] Enable Vercel Analytics
- [ ] Configure custom domain
- [ ] Submit sitemap to Search Console
- [ ] Verify analytics tracking

## 🔒 Security Considerations

### Data Protection

- User ratings and comments stored locally (localStorage)
- No sensitive data transmitted
- XSS protection implemented
- Input validation for user content

### Rate Limiting

- Daily limits on ratings (1 per day)
- Daily limits on comments (3 per day)
- Prevents spam and abuse

## 📞 Support

### Common Issues

**Q: Analytics not working?**
A: Check your GA Measurement ID and ensure Vercel Analytics is enabled

**Q: Game not loading?**
A: Verify iframe src URL and check browser console for errors

**Q: Mobile display issues?**
A: Clear browser cache and ensure responsive meta tag is present

### Getting Help

- **Issues**: [GitHub Issues](https://github.com/Richard-Fu/wackyflipgame/issues)
- **Discussions**: [GitHub Discussions](https://github.com/Richard-Fu/wackyflipgame/discussions)
- **Documentation**: This deployment guide

## 🎮 Play the Game

After successful deployment, your game will be live at:

**🎯 [Play Wacky Flip](https://wackyflipgame.me) 🎯**

---

**Happy Gaming! 🎮**
