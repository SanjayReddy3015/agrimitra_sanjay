# SmartKisan - AI-Powered Agricultural Platform for Indian Farmers

## Overview
Full-stack web application serving Indian farmers with AI-driven advisory, market prices, logistics, mandi maps, voice assistant, and hyperlocal weather alerts.

## Tech Stack
- **Frontend**: React + Vite + TypeScript + TailwindCSS + Shadcn UI + Wouter
- **Backend**: Express.js + TypeScript
- **Database**: PostgreSQL via Drizzle ORM
- **AI**: Google Gemini (via Replit AI Integrations) — no API key needed
- **Maps**: OpenStreetMap via Leaflet (loaded via CDN)
- **Weather**: Open-Meteo API (free, no key required)

## Features
1. **Dashboard** (`/`) — Hero, weather widget, quick access to all features
2. **Market Prices** (`/market`) — Agmarknet live prices, 60-day trend charts, category filters
3. **AI Calculators** (`/calculators`) — Irrigation, fertilizer, and yield calculators (Gemini-powered)
4. **Farmer Profiles** (`/profiles`) — Register and manage farmer + farm records
5. **Crop Calendar** (`/calendar`) — Seasonal crop planning guide
6. **Transport Finder** (`/transport`) — Nearby truck services, AI cost estimate, mandi routes
7. **Mandi Locator** (`/mandi`) — OpenStreetMap GPS map of nearby APMC mandis + navigation
8. **Weather Alerts** (`/weather`) — Real-time hyperlocal weather, rain/frost/heatwave/pest alerts + AI crop advisory
9. **AI Chatbot** (floating) — Gemini AI chatbot with 10 Indian language support + **Voice Assistant** (mic input + TTS output)
10. **Admin Portal** (`/admin`) — OTP-authenticated dashboard

## Key Architecture
- `shared/schema.ts` — All Drizzle ORM table definitions (farmers, farms, market_prices, price_history, conversations, messages)
- `shared/routes.ts` — Typed API contracts using Zod
- `server/routes.ts` — All Express route handlers with real Gemini AI
- `server/gemini.ts` — Gemini AI helpers (chat, irrigation, fertilizer, transport, weather)
- `server/agmarknet.ts` — Agmarknet API integration with history generation
- `server/storage.ts` — DatabaseStorage implementing IStorage interface
- `client/src/pages/` — All page components
- `client/src/components/Chatbot.tsx` — Voice-enabled multilingual AI chatbot

## Gemini AI Integration
Uses Replit AI Integrations (no personal API key required). Billed to Replit credits.
- Chat: All 10 Indian languages (hi, te, ta, kn, mr, gu, pa, bn, ml, en)
- Models used: `gemini-2.5-flash`

## Voice Assistant
- **Input**: Web Speech API (SpeechRecognition) — works in Chrome
- **Output**: Web Speech Synthesis (TTS) — speaks AI responses in selected language
- Language is automatically synced with chatbot language selector

## Environment Variables
- `DATABASE_URL` — PostgreSQL connection string
- `SESSION_SECRET` — Express session secret
- `AI_INTEGRATIONS_GEMINI_API_KEY` — Auto-set by Replit AI Integrations
- `AI_INTEGRATIONS_GEMINI_BASE_URL` — Auto-set by Replit AI Integrations
- `AGMARKNET_API_KEY` — Optional; falls back to public demo key
