# Free Multi-Tool - Fast & Safe Online Conversion

A powerful web-based toolset for file conversion and productivity tasks. Convert PDFs to Word, compress images, trim audio, and more—all in your browser or on mobile.

## 🚀 Features

- **PDF to Word** - Convert PDFs to editable .docx files via CloudConvert API
- **Image Compressor** - Compress images locally without quality loss
- **Audio Cutter** - Trim audio files to specific timestamps
- **Resume Builder** - Create professional resumes easily
- **Dark Mode** - Auto-detect or manual toggle
- **PWA Ready** - Install as mobile app on Android/iOS
- **Analytics** - Google Analytics & Sentry error tracking
- **Ads** - AdSense integration for monetization
- **Newsletter** - Backend subscription support

## 📁 Project Structure

```
free-editing-tools/
├── fasttools-mobile-app/          # Main PWA app
│   ├── index.html                 # Frontend markup
│   ├── app.js                      # Application logic
│   ├── styles.css                  # Styling & dark mode
│   ├── config.js                   # Configuration (edit this!)
│   ├── api.js                      # Backend API wrapper
│   ├── package.json                # Capacitor dependencies
│   ├── capacitor.config.json       # Native app config
│   ├── manifest.json               # PWA manifest
│   └── backend/                    # Python API server
│       ├── main.py                 # FastAPI application
│       ├── services/               # Conversion logic
│       └── requirements.txt        # Python dependencies
│
├── config.js                       # Backend base URL config
├── manifest.json                   # PWA configuration
└── README.md                       # This file
```

## 🎯 Quick Start

### Frontend (Static Host)

1. **Edit configuration:**
   ```bash
   # Edit fasttools-mobile-app/config.js
   # Update FASTTOOLS_API_BASE, AdSense IDs, Analytics IDs
   ```

2. **Serve locally:**
   ```bash
   # Using Python 3
   python -m http.server 8000 --directory fasttools-mobile-app
   # Then open http://localhost:8000
   ```

3. **Deploy to static host:**
   - GitHub Pages
   - Netlify
   - Vercel
   - AWS S3 + CloudFront

### Backend (Python API)

1. **Setup:**
   ```bash
   cd fasttools-mobile-app/backend
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   pip install -r requirements.txt
   ```

2. **Configure environment:**
   ```bash
   cp .env.example .env
   # Edit .env and add:
   # - CLOUDCONVERT_API_KEY (for PDF to Word)
   # - SENTRY_DSN (optional, for error tracking)
   # - ALLOWED_ORIGINS (CORS configuration)
   ```

3. **Run server:**
   ```bash
   uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
   ```

4. **Test API:**
   - Health check: `http://localhost:8000/api/health`
   - API docs: `http://localhost:8000/docs`

## ⚙️ Configuration

### AdSense Setup

1. Get your **AdSense Client ID** from Google AdSense
2. Update in `fasttools-mobile-app/config.js`:
   ```javascript
   window.FASTTOOLS_ADS = {
     client: "ca-pub-YOUR_ID_HERE",
     slots: {
       hero: "1111111111",        // Replace with real slot IDs
       tools: "2222222222",
       articleRect: "3333333333",
       articleSmall: "4444444444"
     }
   };
   ```

### Google Analytics

1. Get your **GA4 Measurement ID**
2. Add to config:
   ```javascript
   window.FASTTOOLS_GA_MEASUREMENT_ID = "G-XXXXXXXXXX";
   ```

### Sentry Error Tracking

1. Get your **Sentry DSN**
2. Add to config:
   ```javascript
   window.FASTTOOLS_SENTRY_DSN = "https://...@sentry.io/...";
   ```

### Branding

Customize in `fasttools-mobile-app/config.js`:
```javascript
window.FASTTOOLS_BRAND = {
  name: "Your App Name",
  tagline: "Your tagline",
  description: "Your description",
  primaryColor: "#0057d9",
  logoUrl: "./assets/logo.svg"
};
```

## 📱 Mobile Apps (Capacitor)

Convert to native Android/iOS:

```bash
cd fasttools-mobile-app
npm install
npx cap init YourAppName com.yourcompany.app
npx cap add android
npx cap add ios
npx cap sync
npx cap open android  # or ios
```

## 🔌 API Endpoints

### POST /api/convert
Convert files (PDF→Word, Image→Compressed, Audio→Trimmed)

### POST /api/subscribe
Newsletter subscription

### POST /api/track
Analytics event tracking

### POST /api/client-error
Frontend error logging

### GET /api/health
Health check

## 📊 Backend Services

- **PDF to Word** - CloudConvert API integration
- **Image Compress** - Pillow (PIL) local processing
- **Audio Cutter** - pydub + ffmpeg local processing
- **Analytics** - Event database logging
- **Sentry** - Server-side error tracking

## 🌐 Deployment

### Frontend
- GitHub Pages: Push to `gh-pages` branch
- Netlify: Connect repo, set build command to `npm run build`
- Vercel: Connect repo, auto-deploy on push

### Backend
- Render.com
- Heroku
- Railway
- DigitalOcean App Platform
- AWS Lambda + API Gateway

## 📝 License

Designed for studying and learning purposes.

## 🤝 Contributing

Feel free to fork, improve, and submit pull requests!