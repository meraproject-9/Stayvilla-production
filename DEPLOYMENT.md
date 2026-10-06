# Production deployment checklist

## 1. Supabase
- Create production project.
- Run `supabase/schema.sql`.
- Configure Auth email/password and email templates.
- Create an admin profile after first sign-up.
- Add property, menu and caretaker records.
- Review RLS policies before opening bookings publicly.

## 2. Razorpay
Implement server-side order creation and webhook verification. Never mark a payment paid from a client-side callback alone.
Required production flow: booking -> server creates Razorpay order -> checkout -> Razorpay webhook -> verified payment row -> booking confirmation.

## 3. Firebase
Create a Firebase Web app and Cloud Messaging setup. Fill the Firebase env values. The caretaker PWA registers the messaging worker. For reliable Android alerts, configure notification channels and FCM server credentials in a server-side notification worker.

## 4. Domain
Deploy the Next.js app to Vercel/Cloudflare-compatible hosting, connect the custom domain, and enforce HTTPS. PWA installation and push notifications require a secure origin.

## 5. Operational safeguards
- Add server-side active-stay window enforcement (11 PM check-in date through 10 PM next day) based on property timezone.
- Add booking overlap/availability transactions.
- Add rate limiting/CAPTCHA on public booking requests.
- Add webhook idempotency for payments.
- Add audit logs for admin price/status changes.
- Add backups and monitoring.
