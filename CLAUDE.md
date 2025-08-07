# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

STR33M Landing Page - A modern React-based marketing website for the str33m.gg streaming platform. Built with Vite and deployed to Cloudflare Pages.

## Essential Commands

### Development
```bash
# Install dependencies
npm install

# Start development server (opens browser at http://localhost:3000)
npm run dev

# Build for production
npm run build

# Preview production build locally
npm run preview

# Deploy to Cloudflare Pages
npm run deploy
```

### Deployment
The site is deployed to Cloudflare Pages. Deployment requires Cloudflare credentials:
```bash
npx wrangler pages deploy dist/ --project-name=str33m-landing
```

## Architecture

### Component Structure
Single-page React application with functional components using hooks. Each component has a corresponding CSS file in `src/styles/`:

- **App.jsx** - Main application wrapper, imports all components
- **components/Header.jsx** - Navigation header with branding
- **components/Hero.jsx** - Landing hero section with CTA
- **components/Features.jsx** - Feature showcase grid
- **components/Footer.jsx** - Footer with links and copyright

### Styling System
- CSS Variables defined in `src/styles/index.css` for theming
- Dark theme with purple/blue gradients (`--primary: #9333ea`, `--secondary: #3b82f6`)
- Each component has isolated styles in `src/styles/[ComponentName].css`
- Responsive design using flexbox and grid layouts

### Build Configuration
Vite configuration in `vite.config.js`:
- React plugin for JSX transformation
- Production optimizations: terser minification, console.log removal
- Development server on port 3000 with auto-open
- Output to `dist/` directory

### Security & Performance
Configured in `_headers`:
- CSP headers for XSS protection
- 1-year cache for static assets
- Security headers (X-Frame-Options, X-Content-Type-Options)
- SPA routing support via `_redirects`

## Key Technical Decisions

1. **No TypeScript** - Pure JavaScript/JSX for simplicity
2. **No Testing Framework** - Consider adding Vitest for React component testing
3. **CSS Modules Not Used** - Global CSS with BEM-like naming conventions
4. **No State Management** - Simple prop drilling (appropriate for landing page)
5. **Cloudflare Pages** - Edge deployment for global performance

## Common Development Tasks

### Adding New Components
1. Create component in `src/components/`
2. Create corresponding CSS in `src/styles/`
3. Import in `App.jsx` and add to component tree
4. Follow existing naming patterns and structure

### Updating Styles
- Global theme variables in `src/styles/index.css`
- Component-specific styles in `src/styles/[ComponentName].css`
- Maintain CSS variable usage for consistency

### Modifying Build Process
- Vite config in `vite.config.js`
- Cloudflare settings in `wrangler.toml`
- Security headers in `_headers`

## Important Notes

- React 19.0.0 (latest) - be aware of new features and deprecations
- No environment variables currently used - add `.env` support if needed
- Console logs automatically removed in production builds
- All routes redirect to index.html for SPA support
- Images should be optimized before adding to `public/`