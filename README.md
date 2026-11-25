# NightSip — Your Night. Delivered Right.

NightSip is a student academic prototype exploring a compliance-first platform concept for legally permitted late-night services. It is **not** a live retailer or delivery service.

## Features
- Responsive React + TypeScript informational website.
- Sections covering the concept, problem, proposed workflow, compliance, market, business model, positioning and vision.
- Informational chatbot powered by Google Gemini through a Supabase Edge Function.
- Server-side Gemini secret handling; no Gemini key belongs in frontend code.

## Technology
- Frontend: React 18, TypeScript, Vite, Tailwind CSS
- Backend: Supabase Edge Functions (Deno)
- AI: Google Gemini via `@google/genai`

## Run locally

1. Install Node.js (LTS) and dependencies:

   ```bash
   npm install
   ```
2. Copy `.env.example` to `.env` and set the Supabase project URL and public anon key:

   ```bash
   cp .env.example .env
   ```
3. Start the frontend:

   ```bash
   npm run dev
   ```
4. Build for production:

   ```bash
   npm run build
   ```

The Supabase Edge Function must be deployed to the configured Supabase project. Set `GEMINI_API_KEY` as an Edge Function secret in Supabase; never put it in `.env`, frontend code, screenshots or GitHub. See the Supabase documentation for deploying Edge Functions and configuring secrets.

## Chatbot architecture
1. The browser sends the user's message and recent conversation history to the Supabase Edge Function at `/functions/v1/chat`.
2. The Edge Function reads `GEMINI_API_KEY` from its server-side environment.
3. The function calls Gemini and returns the generated reply to the frontend.
4. The frontend displays the response and handles loading/error states.

## Repository structure

```text
src/                         # React application and components
supabase/functions/chat/     # Gemini-backed Edge Function
supabase/config.toml         # Supabase function configuration
prompts/                     # Prompt engineering documentation
docs/                        # AI contribution and testing documentation
screenshots/                 # Project evidence screenshots
```

## Prompt engineering and AI tools
See `prompts/` and `docs/ai-tool-contributions.md`. Replace any reconstructed prompt with the exact original prompt from your Bolt session and attach genuine screenshots of each tool's contribution before final submission.

## Academic and legal disclaimer
This project is an educational concept only. It does not implement purchases, payments, orders, delivery arrangements or alcohol-product recommendations. Any real-world operation would require jurisdiction-specific legal review, licensing and regulatory authorization. The market figures and projections in the concept are illustrative unless independently verified.
