# PRD — ACT QBN Carpet Cleaning

## Original Problem Statement
Build the ACT&QBN Carpet Cleaning website from scratch, fully autonomously. Analyze the uploaded logo and design around its aesthetic: deep dark navy background (#0B1320), neon/cyan glowing accents (#4CC9F0 / #00B4D8), silver metallic highlights, light blue/white text (#E0F2FE). Futuristic dark mode with metallic textures, glassmorphism, lens flare/sparkle effects, neon glow borders. Bold 3D metallic headers, clean sans-serif body. Components: hero with branding, service cards with glowing hover borders, contact section (info@actabncarpetcleaning.com.au, 0466 429 772), and a booking form.

## Architecture
- Frontend: React 19 + Tailwind CSS + Framer Motion + lucide-react + sonner toasts
- Backend: FastAPI + Motor (async MongoDB), routes prefixed /api
- Database: MongoDB via MONGO_URL/DB_NAME env vars; bookings collection with uuid string ids (no raw ObjectIds returned)

## User Personas
- Homeowner/tenant in Canberra or Queanbeyan needing carpet, rug, or upholstery cleaning
- Renter needing end-of-lease bond-back carpet cleaning
- Property manager seeking a reliable cleaning contractor

## Core Requirements (static)
1. Hero section with ACT QBN branding, metallic typography, neon CTA
2. Service cards with glassmorphism + neon glow hover borders
3. Contact info section: info@actabncarpetcleaning.com.au, 0466 429 772
4. Working booking form persisted to database
5. Exact color palette: #0B1320 bg, #4CC9F0/#00B4D8 accents, #E0F2FE text

## Implemented (2026-08-24)
- Fixed glassmorphism navbar with mobile menu + Book Now pill CTA
- Hero: metallic 3D-styled heading, floating brand logo with glow ring, animated sparkle/lens-flare particles, trust badges, call CTA
- Services: 6 glassmorphic cards (steam, rug, upholstery, stain removal, end of lease, protection) with neon hover glow, scroll-reveal animations
- Contact: email/phone/service-area glass cards + booking form (name, phone, email, service select, date, message)
- Backend: POST /api/bookings (validated, stored in MongoDB), GET /api/bookings, GET /api/health
- Footer with contact links
- data-testid attributes on all interactive/critical elements
- Design system in /app/design_guidelines.json (Outfit + Manrope fonts)

## Verified
- curl: health 200, booking create 201, list returns records, invalid input returns 422
- Screenshot flows: hero, services, contact render correctly; form submission shows success toast and clears

## Backlog / Next Tasks
- P0: Email notification to business owner on new booking (Resend)
- P1: Admin view of bookings (simple protected list page)
- P1: Gallery section with before/after photos
- P2: Pricing table, Google reviews/testimonials carousel, SEO meta tags
