# STR33M Landing Page

A modern, high-performance landing page for str33m.gg built with React and optimized for Cloudflare Pages deployment.

## 🚀 Tech Stack

- **Frontend**: React 18 with Vite
- **Styling**: CSS3 with CSS Variables for theming
- **Build Tool**: Vite for lightning-fast HMR and optimized builds
- **Deployment**: Cloudflare Pages for global CDN distribution
- **Performance**: Code splitting, lazy loading, and optimized assets

## 📋 Prerequisites

- Node.js 18+ and npm/yarn
- Cloudflare account (free tier works)
- Wrangler CLI (installed as dev dependency)

## 🛠️ Local Development

### 1. Install Dependencies

```bash
npm install
```

### 2. Start Development Server

```bash
npm run dev
```

The site will be available at `http://localhost:3000` with hot module replacement.

### 3. Build for Production

```bash
npm run build
```

Creates optimized production build in `dist/` directory.

### 4. Preview Production Build

```bash
npm run preview
```

## 🌐 Deployment to Cloudflare

### Option 1: Direct CLI Deployment

```bash
npm run deploy
```

This runs the build and deploys directly to Cloudflare Pages using Wrangler.

### Option 2: GitHub Integration (Recommended)

1. Push code to GitHub repository
2. Go to [Cloudflare Pages Dashboard](https://dash.cloudflare.com/pages)
3. Click "Create a project" → "Connect to Git"
4. Select your repository
5. Configure build settings:
   - **Build command**: `npm run build`
   - **Build output directory**: `dist`
   - **Root directory**: `/` (or your project path)
6. Deploy!

### Option 3: Manual Upload

1. Build the project: `npm run build`
2. Go to Cloudflare Pages Dashboard
3. Create new project → Upload assets
4. Drag and drop the `dist` folder

## 🔧 Configuration

### Custom Domain Setup

1. In Cloudflare Pages dashboard, go to your project
2. Navigate to "Custom domains"
3. Add `str33m.gg` as custom domain
4. Update DNS records as instructed

### Environment Variables

Create `.env.local` for local development:

```env
VITE_API_URL=https://api.str33m.gg
VITE_ANALYTICS_ID=your-analytics-id
```

For production, set these in Cloudflare Pages dashboard under Settings → Environment variables.

## 📁 Project Structure

```
str33m-landing/
├── public/              # Static assets
│   └── favicon.svg
├── src/
│   ├── components/      # React components
│   │   ├── Header.jsx
│   │   ├── Hero.jsx
│   │   ├── Features.jsx
│   │   └── Footer.jsx
│   ├── styles/          # Component styles
│   │   ├── index.css
│   │   ├── App.css
│   │   └── ...
│   ├── App.jsx          # Main app component
│   └── main.jsx         # Entry point
├── index.html           # HTML template
├── vite.config.js       # Vite configuration
├── wrangler.toml        # Cloudflare config
├── package.json         # Dependencies
└── README.md           # This file
```

## 🎨 Customization

### Updating Content

- **Text/Copy**: Edit components in `src/components/`
- **Styles**: Modify CSS files in `src/styles/`
- **Colors/Theme**: Update CSS variables in `src/styles/index.css`
- **Features**: Add/remove feature cards in `src/components/Features.jsx`

### Adding New Sections

1. Create new component in `src/components/`
2. Import and add to `src/App.jsx`
3. Create corresponding CSS in `src/styles/`

## 🏗️ Architecture Decisions

### Why Static React Build?

- **Performance**: Pre-rendered HTML with client-side hydration
- **SEO**: Better search engine indexing
- **Cost**: No server runtime costs on Cloudflare
- **Scalability**: Infinite scaling via CDN
- **Developer Experience**: Component-based architecture with modern tooling

### Why Vite?

- **Speed**: Instant HMR in development
- **Optimization**: Automatic code splitting and tree shaking
- **Modern**: Native ES modules support
- **Cloudflare Ready**: Optimized output perfect for edge deployment

### Why Cloudflare Pages?

- **Global CDN**: 200+ edge locations worldwide
- **Performance**: Automatic HTTP/3, Brotli compression
- **Security**: DDoS protection, SSL included
- **Analytics**: Built-in Web Analytics
- **Cost**: Generous free tier (unlimited bandwidth)

## 📊 Performance Optimization

The site is optimized for Core Web Vitals:

- **Lazy Loading**: Components load on-demand
- **Code Splitting**: Automatic chunking by Vite
- **Asset Optimization**: Images and fonts optimized
- **Caching**: Aggressive cache headers via `_headers`
- **Compression**: Automatic Brotli/Gzip on Cloudflare

## 🔒 Security

- CSP headers configured in `_headers`
- XSS protection via React's built-in escaping
- HTTPS enforced by Cloudflare
- Regular dependency updates recommended

## 📝 License

MIT License - feel free to use for your projects!

## 🤝 Contributing

1. Fork the repository
2. Create feature branch (`git checkout -b feature/amazing`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing`)
5. Open Pull Request

## 💡 Future Enhancements

- [ ] Add contact form with Cloudflare Workers backend
- [ ] Implement dark/light theme toggle
- [ ] Add blog section with MDX support
- [ ] Integrate analytics dashboard
- [ ] Add i18n for multi-language support
- [ ] Implement A/B testing framework

## 🆘 Troubleshooting

### Build fails locally
- Clear node_modules: `rm -rf node_modules && npm install`
- Check Node version: `node --version` (should be 18+)

### Deployment fails on Cloudflare
- Verify build command and output directory
- Check environment variables are set
- Review build logs in Cloudflare dashboard

### Site not updating after deployment
- Clear Cloudflare cache: Dashboard → Caching → Purge Everything
- Check `_headers` file for cache settings
- Verify deployment completed successfully

---

Built with ❤️ for modern web streaming