# Privacy-Policy
Trader OS privacy policy

# Trader OS

Trader OS is an iOS app for disciplined trade logging: checklists before entry, structured trade records, journaling, and optional AI coaching. Data syncs for signed-in users via **Supabase**.

---

## Requirements

- **Xcode** 15+ (recommended: latest stable)
- **iOS** deployment target: **17.0** (see project settings)
- **Swift Package Manager** dependency: [supabase-swift](https://github.com/supabase/supabase-swift)

---

## Building

1. Open `Trader_OS.xcodeproj` in Xcode.
2. Select the **Trader_OS** scheme and a simulator or device.
3. **Product → Build** (⌘B). Resolve Swift packages if prompted (**File → Packages → Resolve Package Versions**).

The app expects a configured Supabase project (URL, anon key, and tables/functions matching your backend). Client configuration lives in `Trader_OS/App/SupabaseClient.swift` and related services.

---

## Features (overview)

| Area | Description |
|------|-------------|
| **Auth** | Email/password (or your Supabase auth setup) via Supabase. |
| **Trades** | Log market, direction, entry, stop, target; optional strategy tags; sync to `trades`. |
| **Checklists** | Pre-trade checklists; sync to `checklists`. |
| **Journal** | Post-trade reflections linked to trades; sync to `trade_journals`. |
| **Dashboard** | Today’s stats, discipline, quick navigation. |
| **AI Coach** | Optional chat backed by Supabase Edge Functions (configure secrets/APIs on the server). |
| **Live quotes** | Optional market quotes via Edge Function `market-quote`. |

---

## Privacy & App Store

- **Privacy Policy:** see [`PRIVACY_POLICY.md`](./PRIVACY_POLICY.md) in this repository.
- **App Store Connect:** paste your privacy policy URL (host the markdown on GitHub Pages, your website, or a doc host) in **App Privacy** and the **Privacy Policy URL** field.
- **App Privacy questionnaire:** align answers with `PRIVACY_POLICY.md` (account data, user content, identifiers, analytics if any, etc.).
- Replace the placeholder support email in `PRIVACY_POLICY.md` before submission.

---

## Project layout (high level)

```
Trader_OS/
  App/           Theme, Supabase client, session
  Models/        Trades, checklists, Supabase mapping
  Views/         Dashboard, Trade entry, Journal, Checklist, Auth, etc.
```

---

## Configuration & secrets

- Do **not** commit production **service role** keys or API secrets.
- The app ships with a **Supabase anon key** in the client (expected for Supabase client apps). Protect your project with Row Level Security (RLS) and server-side validation.
- Edge Functions (`ai-coach`, `market-quote`, etc.) should keep provider keys in **Supabase secrets**, not in the iOS binary.

---

## License

All rights reserved unless you add a separate `LICENSE` file. Update this section if you open-source the project.

---

## Support

For App Store “support URL” and contact, use the same email or site you place in `PRIVACY_POLICY.md` Section 10.

