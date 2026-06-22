# Screener Templates — UserTesting

> These are the exact screener questions to use for **Remote** tests on UserTesting.
> For **On-site** tests, do NOT use these questions. Instead, generate a "Participant Selection Criteria" section.
>
> Logic: Copy the questions for the identified **Persona × Wallet Variant** combination.
> Never modify Accept/Reject/Must select/May select labels.
> Trap answers are marked [Reject - Trap Answer] — always include them to filter low-quality respondents.

---

## PART A — Typeform Screener (General Recruitment)

Use these 4 questions for any recruitment channel outside UserTesting (Typeform, etc.).
They identify which persona the candidate matches before deeper screening.

### Question 1 — Crypto Motivation (Single choice)
*What is the main driving force behind your interest in crypto?*
- a) Total financial independence and protection against traditional systems → **[Felix]**
- b) Long-term growth of my assets and diversification of my investments → **[Warren]**
- c) Exploring technological innovation and participating in the building of Web3 → **[Talia]**
- d) The possibility of making quick profits by capitalizing on market volatility → **[Sam]**
- e) Curiosity about a cultural trend and the desire to learn without taking too many risks → **[Alex]**
- f) The opportunity to receive a fixed monthly passive income, guaranteed by platforms → **[Reject - Trap Answer]**

### Question 2 — Primary Crypto Activity (Single choice)
*Which activity best describes how you spend the majority of your time in crypto?*
- a) Monitoring the value of my assets and ensuring they are secure for the long term → **[Felix, Warren]**
- b) Analyzing markets and frequently trading (buying/selling/swapping) to generate profits → **[Sam]**
- c) Testing decentralized applications (DeFi, NFT), staking, or interacting with new protocols → **[Talia]**
- d) Learning the basics, reading articles, or watching videos to better understand the ecosystem → **[Alex]**
- e) Spending my cryptos with a debit card for my daily purchases like coffee or groceries → **[Reject - Trap Answer]**

### Question 3 — Biggest Frustration (Single choice)
*What is your biggest personal frustration in the current crypto ecosystem?*
- a) The constant threat of hacks and the feeling that my assets are never truly safe on platforms → **[Felix]**
- b) The lack of reliable information sources and professional tools to manage a portfolio seriously → **[Warren]**
- c) The fragmentation between blockchains which makes experimenting with new applications complex and risky → **[Talia]**
- d) Transaction fees that are too high and the slowness of platforms that reduce my potential gains → **[Sam]**
- e) The general complexity, technical jargon, and fear of making a costly mistake as a beginner → **[Alex]**
- f) The impossibility of reaching an advisor by phone 24/7 to cancel a transaction → **[Reject - Trap Answer]**

### Question 4 — Investment Strategy (Single choice)
*Which of these strategies is closest to your way of thinking?*
- a) "Time is my best ally. I hold my assets for the long term." → **[Felix, Warren]**
- b) "The market is a game of speed. I'm here to seize opportunities, not to wait." → **[Sam]**
- c) "Value is in technology. I invest in projects I want to see succeed." → **[Talia]**
- d) "I am cautious. I observe and learn before committing more seriously." → **[Alex]**
- e) "My strategy is simple: I only invest in cryptos recommended by celebrities on social media." → **[Reject - Trap Answer]**

---

## PART B — UserTesting Screeners by Persona × Wallet Variant

---

### 🧱 FELIX

**Profile:** Security-focused HODLer. Prioritizes asset protection, transacts infrequently but deliberately.

#### Felix — Hardware Wallet

**Crypto ownership:**
- Have you owned any cryptocurrencies in the past 12 months? (including NFTs and stablecoins)
  - Yes → **[Accept]**
  - No → **[Reject]**

**Transaction frequency:**
- On average, how often do you make transactions?
  - Several times a day → **[Reject]**
  - Once a day → **[Reject]**
  - Once a week → **[Accept]**
  - Once a month → **[Accept]**
  - Once a semester → **[Accept]**
  - Almost never → **[Reject]**

**Experience level (6-point scale):**
- 1. Bought/sold via centralized exchange → **[Reject]**
- 2. Participated in staking on centralized exchanges → **[Reject]**
- 3. Set up a self-custodial wallet (Metamask, Trust Wallet) → **[Reject]**
- 4. Bought/sold/swapped on a DEX → **[Reject]**
- 5. Set up a hardware wallet (Trezor, Ledger) → **[Accept]**
- 6. Set up a validator and/or mining node → **[Accept]**
- None of the above → **[Reject]**

**Motivation (up to 2 selections):**
- a) Total financial independence and protection against traditional systems → **[Must select]**
- b) Long-term growth of my assets and diversification → **[May select]**
- c) Exploring technological innovation and Web3 → **[May select]**
- d) Quick profits by capitalizing on volatility → **[Reject]**
- e) Curiosity about a cultural trend, learn without too much risk → **[May select]**
- f) The ability to pay my taxes with cryptocurrency → **[Reject]**

**Activities (up to 3 selections):**
- A) Ensuring the security of my assets in a wallet I fully control → **[Must select]**
- B) Using crypto for practical applications like fast and cheaper payments → **[May select]**
- C) Investing seriously and prudently, prioritizing reputable brands → **[May select]**
- D) Investing methodically long-term to grow my wealth → **[May select]**
- E) Exploring and interacting with new decentralized applications (DeFi, DAOs) → **[May select]**
- F) Monitoring markets and trading frequently → **[Reject]**
- G) Learning the basics simply and guided, making small investments → **[Reject]**
- H) Keeping an eye on trends and acting fast to seize opportunities → **[Reject]**
- I) Collecting and managing unique digital assets (NFTs) → **[May select]**

---

#### Felix — Software Wallet

*Same as Felix Hardware Wallet except experience level question:*

**Experience level (6-point scale):**
- 1. Bought/sold via centralized exchange → **[Reject]**
- 2. Participated in staking on centralized exchanges → **[Reject]**
- 3. Set up a self-custodial wallet (Metamask, Trust Wallet) → **[Accept]**
- 4. Bought/sold/swapped on a DEX → **[Accept]**
- 5. Set up a hardware wallet (Trezor, Ledger) → **[Reject]**
- 6. Set up a validator and/or mining node → **[Reject]**
- None of the above → **[Reject]**

---

### 📈 WARREN

**Profile:** Serious long-term investor. Portfolio-focused, methodical, uses CEX primarily.
**Demographics:** Age 30–65 | Income $60K–$150K+ | Country: US

#### Warren — Exchange

**Crypto ownership:**
- Have you owned any cryptocurrencies in the past 12 months?
  - Yes → **[Accept]** | No → **[Reject]**

**Transaction frequency:**
- Several times a day → **[Reject]** | Once a day → **[Reject]** | Once a week → **[Accept]**
- Once a month → **[Accept]** | Once a semester → **[Accept]** | Almost never → **[Reject]**

**Experience level:**
- 1. Bought/sold via centralized exchange → **[Accept]**
- 2. Participated in staking on centralized exchanges → **[Accept]**
- 3. Set up a self-custodial wallet → **[Reject]**
- 4. Bought/sold/swapped on a DEX → **[Reject]**
- 5. Set up a hardware wallet → **[Reject]**
- 6. Set up a validator/mining node → **[Reject]**
- None of the above → **[Reject]**

**Motivation (up to 2):**
- a) Financial independence → **[May select]**
- b) Long-term growth and diversification → **[Must select]**
- c) Technological innovation / Web3 → **[Reject]**
- d) Quick profits → **[Reject]**
- e) Curiosity / learn without risk → **[May select]**
- f) Pay taxes with crypto → **[Reject]**

**Activities (up to 3):**
- A) Asset security in wallet I control → **[May select]**
- B) Practical payments → **[Reject]**
- C) Investing seriously, prioritizing reputable brands → **[May select]**
- D) Investing methodically long-term → **[Must select]**
- E) Exploring DeFi/DAOs → **[Reject]**
- F) Frequent trading → **[Reject]**
- G) Learning the basics → **[May select]**
- H) Trend-watching, acting fast → **[May select]**
- I) NFT collecting → **[May select]**

---

#### Warren — Software Wallet

*Same as Warren Exchange except experience level:*
- 1. Bought/sold via CEX → **[Reject]**
- 2. Staking on CEX → **[Reject]**
- 3. Self-custodial wallet → **[Accept]**
- 4. DEX trading → **[Accept]**
- 5. Hardware wallet → **[Reject]**
- 6. Validator/mining node → **[Reject]**
- None → **[Reject]**

---

#### Warren — Hardware Wallet

*Same as Warren Exchange except experience level:*
- 5. Set up a hardware wallet → **[Accept]**
- 6. Set up a validator/mining node → **[Accept]**
- All others → **[Reject]**

---

### 🔬 TALIA

**Profile:** Web3 explorer, DeFi enthusiast. Experiments with new protocols, active on-chain.

#### Talia — Hardware Wallet

**Crypto ownership:** Yes → **[Accept]** | No → **[Reject]**

**Transaction frequency:**
- Several times a day → **[Accept]** | Once a day → **[Accept]** | Once a week → **[Accept]**
- Once a month → **[Accept]** | Once a semester → **[Reject]** | Almost never → **[Reject]**

**Experience level:**
- 1–4 → **[Reject]**
- 5. Hardware wallet → **[Accept]**
- 6. Validator/mining node → **[Accept]**
- None → **[Reject]**

**Motivation (up to 2):**
- a) Financial independence → **[May select]**
- b) Long-term growth → **[May select]**
- c) Technological innovation / Web3 → **[Must select]**
- d) Quick profits → **[May select]**
- e) Curiosity / learn → **[May select]**
- f) Fixed passive income → **[Reject]**

**Activities (up to 3):**
- A) Asset security → **[May select]**
- B) Practical payments → **[May select]**
- C) Serious investing, reputable brands → **[May select]**
- D) Long-term investing → **[May select]**
- E) Exploring DeFi/DAOs → **[Must select]**
- F) Frequent trading → **[May select]**
- G) Learning basics → **[Reject]**
- H) Trend-watching → **[May select]**
- I) NFT collecting → **[May select]**

---

#### Talia — Exchange & Software Wallet

*Same as Talia Hardware except experience level:*
- 1. CEX buying → **[Reject]**
- 2. CEX staking → **[Accept]**
- 3. Self-custodial wallet → **[Accept]**
- 4. DEX trading → **[Accept]**
- 5. Hardware wallet → **[Reject]**
- 6. Validator → **[Reject]**
- None → **[Reject]**

---

### ⚡ SAM

**Profile:** Active trader. Frequent transactions, capitalizes on volatility, speed-oriented.
**Demographics:** Age 24–54 | Income $60K–$150K+ | Country: US

#### Sam — Hardware Wallet

**Crypto ownership:** Yes → **[Accept]** | No → **[Reject]**

**Transaction frequency:**
- Several times a day → **[Accept]** | Once a day → **[Accept]** | Once a week → **[Accept]**
- Once a month → **[Reject]** | Once a semester → **[Reject]** | Almost never → **[Reject]**

**Experience level:**
- 1–4 → **[Reject]**
- 5. Hardware wallet → **[Accept]**
- 6. Validator/mining node → **[Accept]**
- None → **[Reject]**

**Motivation (up to 2):**
- a) Financial independence → **[May select]**
- b) Long-term growth → **[May select]**
- c) Technological innovation → **[May select]**
- d) Quick profits from volatility → **[Must select]**
- e) Curiosity / learn → **[Reject]**
- f) Fixed passive income → **[Reject]**

**Activities (up to 3):**
- A) Asset security → **[May select]**
- B) Practical payments → **[May select]**
- C) Serious investing → **[May select]**
- D) Long-term investing → **[May select]**
- E) DeFi exploration → **[May select]**
- F) Frequent trading → **[Must select]**
- G) Learning basics → **[Reject]**
- H) Trend-watching → **[May select]**
- I) NFT collecting → **[May select]**

---

#### Sam — Exchange & Software Wallet

*Same as Sam Hardware except experience level:*
- 1. CEX buying → **[Reject]**
- 2. CEX staking → **[Accept]**
- 3. Self-custodial wallet → **[Accept]**
- 4. DEX trading → **[Accept]**
- 5. Hardware wallet → **[Reject]**
- 6. Validator → **[Reject]**
- None → **[Reject]**

---

### 🌱 ALEX

**Profile:** Cautious beginner. Learning mode, low risk tolerance, uses CEX only.
**Demographics:** Age 18–44 | Income $20K–$100K | Country: US

#### Alex — Exchange

**Crypto ownership:** Yes → **[Accept]** | No → **[Reject]**

**Transaction frequency:**
- Several times a day → **[Reject]** | Once a day → **[Accept]** | Once a week → **[Accept]**
- Once a month → **[Accept]** | Once a semester → **[Accept]** | Almost never → **[Reject]**

**Experience level:**
- 1. CEX buying/selling → **[Accept]**
- 2. CEX staking → **[Accept]**
- 3. Self-custodial wallet → **[Reject]**
- 4. DEX trading → **[Reject]**
- 5. Hardware wallet → **[Reject]**
- 6. Validator → **[Reject]**
- None → **[Reject]**

**Motivation (up to 2):**
- a) Financial independence → **[May select]**
- b) Long-term growth → **[May select]**
- c) Technological innovation → **[Reject]**
- d) Quick profits → **[May select]**
- e) Curiosity / learn without too much risk → **[Must select]**
- f) Fixed passive income → **[Reject]**

**Activities (up to 3):**
- A) Asset security → **[May select]**
- B) Practical payments → **[May select]**
- C) Serious investing → **[May select]**
- D) Long-term investing → **[May select]**
- E) DeFi exploration → **[Reject]**
- F) Frequent trading → **[Reject]**
- G) Learning basics, guided → **[Must select]**
- H) Trend-watching → **[May select]**
- I) NFT collecting → **[May select]**

---

#### Alex — Software Wallet

*Same as Alex Exchange except experience level:*
- 1. CEX buying → **[Reject]**
- 2. CEX staking → **[Reject]**
- 3. Self-custodial wallet → **[Accept]**
- 4. DEX trading → **[Accept]**
- 5. Hardware wallet → **[Reject]**
- 6. Validator → **[Reject]**
- None → **[Reject]**

---

## Quick Reference: Persona × Wallet Matrix

| Persona | Hardware Wallet | Software Wallet | Exchange |
|---------|:--------------:|:---------------:|:--------:|
| Felix   | ✅ | ✅ | ❌ |
| Warren  | ✅ | ✅ | ✅ |
| Talia   | ✅ | ✅ (combined with Exchange) | ✅ |
| Sam     | ✅ | ✅ (combined with Exchange) | ✅ |
| Alex    | ❌ | ✅ | ✅ |
