# Kiara AI Architecture — Owe

Kiara is Owe's on-device + cloud AI assistant (lucky-cat brand).  
**Apple handles body & math. OpenAI handles language. Cloudflare holds the API key.**

## Responsibility split

### Apple only (on-device, $0, private, works offline where noted)

| Capability | Technology | Notes |
|------------|------------|--------|
| Speech → text | `Speech` framework | Audio never sent to OpenAI |
| All math | Swift (`DebtMathService`, amortization, snowball, etc.) | **OpenAI must never calculate** |
| Loan & debt storage | Local stores + optional iCloud sync | No server database |
| Siri shortcuts | App Intents (future) | e.g. "Log $50 payment" |
| App lock & vault | `LocalAuthentication` / Face ID | Already in app |

### OpenAI via Cloudflare (Pro / Kiara subscription)

| Feature ID | Purpose | Output |
|------------|---------|--------|
| `advisor` | Financial education Q&A | Plain text |
| `extract_loan` | Parse voice rant → structured fields | JSON only |
| `explain_result` | Humanize pre-calculated Swift numbers | Plain text |
| `general` | Open chat in Kiara voice | Plain text |

### Cloudflare Worker

- Holds `OPENAI_API_KEY` and `APP_API_KEY`
- Routes by `feature` → Kiara system prompt
- No data storage, no thinking

## Workflow example

1. User speaks → **Apple** Speech → text  
2. App reads saved debts → **Apple** local store  
3. App runs affordability math → **Apple** Swift  
4. App sends text + facts to Worker → **Cloudflare** adds API key → **OpenAI**  
5. Kiara reply shown → **Apple** UI  

## Branding — Kiara

- **Name:** Kiara (empathetic, human, memorable)
- **Mascot:** Premium minimalist lucky cat (not cartoonish)
- **Tone:** Encouraging, accurate, prosperity-focused
- **Micro-interactions (future):** Paw raise on payment logged, glow ring while listening

## Privacy rules (enforce in code)

1. Never send raw audio to OpenAI  
2. Never ask OpenAI to compute payments, APR, or payoff dates  
3. Send only text the user chose to share + anonymized numeric summaries  
4. No PII: no full account numbers, SSN, bank logins  

## iOS code map

| File | Role |
|------|------|
| `KiaraFeature.swift` | Feature enum + prompt contract |
| `KiaraService.swift` | High-level API (advisor, extract, explain) |
| `AIService.swift` | HTTP client to Worker |
| `AIConfiguration.swift` | Worker URL + app API key |

## Worker

- Live: `https://owe-ai.ravicraj.workers.dev`
- Dashboard code: `cloudflare/owe-ai/dashboard-worker.js`
- Re-paste into Cloudflare after prompt updates

## Build order (suggested)

1. ✅ Worker + health + chat  
2. ✅ Kiara feature routing + iOS service layer  
3. Kiara chat UI (Pro-gated)  
4. Speech input (Apple Speech)  
5. Loan extraction flow (voice → JSON → form prefill)  
6. Explain-result chips on calculators  
7. Siri App Intents  
8. Lucky-cat micro-animations  
