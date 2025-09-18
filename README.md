# MovieFinder (Monorepo)

A full-stack, Apple-quality movie discovery app. This repo includes:

- iOS SwiftUI app scaffold (XcodeGen config) with Home, Search, Onboarding, Profile, Watchlists.
- Supabase schema with RLS policies for profiles, friends, watchlists, playlists, parties, and caches.
- Supabase Edge Functions for recommendations and LLM rationales (with caching and cost controls). Optionally proxied via Cloudflare Worker.
- Configuration via `.xcconfig` (iOS) and `.env` (edge functions) with environment-based feature flags.
- A polished Cloud Code Opus 4.1 prompt to complete and productionize remaining pieces.

## Quickstart

1) Prereqs
- Xcode 15+
- XcodeGen (`brew install xcodegen`)
- Supabase CLI (`brew install supabase/tap/supabase`)
- Node 18+ for edge functions

2) Configure Supabase
- `cd supabase`
- `supabase init` (if not already initialized)
- `supabase start` (for local dev)
- `supabase db reset` (applies migrations)
- `supabase functions serve` (to run locally)

3) Configure iOS app
- `cd ios`
- Copy `App/Config/Debug.xcconfig.example` to `Debug.xcconfig` (and Release likewise), then fill in keys.
- `xcodegen generate`
- Open `MovieFinder.xcodeproj` in Xcode.

4) Run
- Set scheme to `MovieFinder` and run on iOS 17+ simulator.

5) Deploy
- Supabase: Import your existing schema at `Desktop/Movie Finder/supabase_schema.sql` and deploy functions if used.
- Cloudflare Worker: Configure `wrangler.toml` and set secrets (`SUPABASE_URL`, `SUPABASE_ANON_KEY`, `TMDB_API_KEY`).
- App Store: Archive via Xcode and submit with Transporter/App Store Connect.

See `CLOUD_CODE_OPUS_PROMPT.md` for the finishing instructions to complete and polish the app.
# whoopd
# fx-option
