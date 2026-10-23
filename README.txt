DALAN NIN PAGTUBOD — APP STARTER V2

Brand:
Dalan nin Pagtubod
St. Stephen the Protomartyr Parish, Ligao City, Albay

Included:
- Responsive mobile-first progressive web app (PWA)
- Language selector for English, Filipino, and starter Bikol translations
- Prayer library with language-specific titles/texts
- Search, favorites, reflection notes saved locally
- Novena directory, Mass outline, Gospel source link
- Parish and announcement placeholders
- Admin workflow planning screen (not a real authenticated admin portal)
- Offline caching service worker

IMPORTANT CONTENT REVIEW:
The Filipino and Bikol texts are draft translations, not certified liturgical texts. Ask the parish priest or authorized reviewer to check all prayers and translations before public use. Bikol varies by locality; confirm the desired Ligao/Albay wording. Add complete approved novenas and licensed Gospel readings before launch. Some Bible translations and liturgical texts are copyrighted.

PREVIEW LOCALLY:
Open index.html in a browser for basic preview. Service worker and install features require HTTPS or localhost.

PUBLISH AS WEBSITE / INSTALLABLE APP:
1. Create a GitHub repository named dalan-nin-pagtubod.
2. Upload the files in this folder to the repository root.
3. GitHub > Settings > Pages > Deploy from branch > main > /(root).
4. Open the resulting HTTPS site on Android Chrome or iPhone Safari.
5. Android: browser menu > Install app / Add to Home screen.
6. iPhone: Safari Share > Add to Home Screen.
This is the quickest low-cost launch route; it does not by itself publish to Google Play or Apple's App Store.

PACKAGE FOR BOTH STORES:
- Android: use Capacitor to wrap the web app in an Android project, build a signed Android App Bundle (.aab), test it, then publish through Google Play Console.
- iOS: use Capacitor with Xcode on a Mac, configure signing and capabilities, test in TestFlight, then submit through App Store Connect. Apple developer membership is typically required for App Store distribution.
- A web/PWA build can be the shared codebase, but store packaging and testing are separate steps.

ADMIN PORTAL — PRODUCTION REQUIREMENTS:
Do not treat the included admin placeholder as secure login. Before allowing staff to publish:
1. Create a Supabase project.
2. Enable Supabase Auth; invite authorized staff rather than sharing a universal password.
3. Create tables for profiles, announcements, mass_schedules, prayers, novenas, and app_settings.
4. Enable Row Level Security on all tables.
5. Allow public read-only access only to published content.
6. Restrict insert/update/delete to authenticated users with approved admin/editor roles.
7. Never place the Supabase service-role key in client-side code.
8. Add a privacy notice and a way to report content errors.
9. Test unauthorized access and permissions before launch.

SUGGESTED DEPLOYMENT PHASES:
Phase 1 — Parish content review and PWA launch.
Phase 2 — Supabase database, staff authentication, announcements and schedules.
Phase 3 — Capacitor Android build and Play Console testing.
Phase 4 — iOS build, TestFlight testing, App Store submission.
Phase 5 — Analytics only if needed, accessibility review, maintenance and content update process.


VERSION 3 — OFFLINE ADMIN EDITING

New admin features:
- Add, edit and delete prayer entries with English, Filipino, and Bikol text fields.
- Add and delete novena directory entries.
- Add and delete custom library resources.
- Change primary and accent theme colors.
- Change logo initials or upload a small logo image.
- View local pending-change queue and connectivity status.
- Local content and theme settings are stored in browser localStorage and persist on that device.

IMPORTANT OFFLINE / SYNC LIMIT:
This build supports offline local editing, but does NOT yet perform real automatic cross-device synchronization. The sync panel is a setup/status placeholder, not a live backend connection. A secure sync service needs to be implemented and tested with Supabase Auth, a database schema, Row Level Security (RLS), conflict handling, and authorized admin/editor roles. Until that is done, edits made on one device do not appear on other devices. Never expose a Supabase service-role key in the app.

SECURITY:
The admin screen in this prototype is not protected by authentication. Do not deploy it publicly as a real admin portal or enter sensitive data. For production, use Supabase Auth and enforce authorization in database policies. Hiding the admin screen is not security.

CONTENT:
Bikol and Filipino prayer text is draft content and requires parish review. Novena directory entries are not complete novena texts. Daily Gospel links to a source rather than copying a copyrighted reading. Verify official parish contact details and Mass times before publishing.

TESTING:
Use a JavaScript syntax check before publishing (for example: node --check app.js). Then test prayer add/edit/delete, theme/logo changes, offline reload, language switching, and mobile layouts. Clear browser storage only after backing up local content.


OFFLINE WELLNESS GAMES (v4)
The app now includes five local-only activities: Calm Breathing, Gratitude Garden, Kindness Quest, Peaceful Pairs memory matching, and Weather Within mood check-in. The games work without internet after the app files have been loaded once and cached by the service worker. Notes/check-ins are stored in the browser on the current device and are not uploaded or shared. The activities are for everyday wellbeing and are not a diagnosis or a substitute for mental-health care. Review Filipino and Bikol wording with fluent local speakers before public release.


SEPARATE ADMIN LINK (v5)
The Admin Control tile has been removed from the public user home menu. Admins can open the separate entry page at /admin.html; its Open Admin Control link opens index.html?admin=1. Example for GitHub Pages: https://YOUR-USERNAME.github.io/YOUR-REPOSITORY/admin.html. This separation is navigation only, not access control: the prototype admin page is still not protected by authentication. Before public deployment, implement Supabase Auth and enforce admin/editor roles with database Row Level Security. Do not treat an unlisted URL or a hidden menu item as security.


Language policy update (Version 6): The public user interface is English-only. The public Tagalog/Filipino and Bikol language selector has been removed. Administrators can enter an English prayer and its Bikol translation in the separate admin page. This prototype stores edits locally on the current device; secure sign-in and cross-device sync still require backend implementation.
