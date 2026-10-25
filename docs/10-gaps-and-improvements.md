# Gaps, Hardening & Technical Debt: Amazon Clone

## Prioritized Improvement Roadmap

| Priority | Area | Current Implementation | Production Hardening Recommendation |
|---|---|---|---|
| **P1** | Backend Payment Secret | Client-side mock secret | Deploy an Express / Firebase Cloud Function to create real Stripe `PaymentIntents` securely on the server. |
| **P2** | Firestore Security Rules | Default open rules | Enforce strict security rules: `allow read, write: if request.auth != null && request.auth.uid == userId;`. |
| **P3** | Dynamic Catalog | Hardcoded product list in `Home.js` | Migrate products to a Firestore `products` collection with category filtering and keyword search. |
| **P4** | Cart Quantity Counter | Duplicates add new array items | Refactor basket to map `{ id, quantity, price }` to prevent duplicate row rendering in checkout. |
