# StayVilla Production Starter

A production-oriented Next.js + Supabase foundation for a premium villa guest website and caretaker PWA.

## Included
- Premium customer website
- Reservation request flow
- Guest portal
- Menu ordering into service requests
- Caretaker live-request screen
- Web Audio test/new-request alert
- Installable PWA manifest for caretaker Android use
- Supabase Auth/database/RLS schema
- Running-folio data model
- Payment data model
- Admin foundation
- Health endpoint

## Local setup
1. Create a Supabase project.
2. Run `supabase/schema.sql` in Supabase SQL Editor.
3. Copy `.env.example` to `.env.local` and fill Supabase values.
4. `npm install`
5. `npm run dev`
6. Open `http://localhost:3000`.

## Production integrations still requiring credentials/config
- Razorpay order creation + webhook signature verification
- Firebase Cloud Messaging credentials/service worker for background push
- Transactional email provider for booking/account emails
- Domain/DNS
- Supabase production project and storage policies
- Android packaging (if a native caretaker APK is required)

The included caretaker PWA is the fastest production deployment path. For an always-on continuous alarm when the app is backgrounded, use FCM notification channels or a native Android wrapper; browsers/OSes can restrict background audio.

## Security notes
- Never expose a Supabase service-role key in the browser.
- Payment confirmation must be performed server-side through a verified Razorpay webhook.
- Keep RLS enabled.
- Add server-side validation that a guest has an active booking before allowing menu/service requests.
- Add rate limiting and abuse protection before public launch.
