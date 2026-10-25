# Codebase Anatomy & Project Map: Amazon Clone

## Directory Tree

```
45-amazon-landing-page/
├── amazon landing page /
│   └── amazonself/
│       ├── package.json             # React dependencies, Stripe, Firebase
│       ├── firebase.json            # Firebase hosting configuration
│       ├── public/                  # HTML entry template & favicon
│       └── src/                     # React Application Root
│           ├── index.js             # React DOM root render with StateProvider
│           ├── App.js               # Route declaration & Firebase Auth listener
│           ├── StateProvider.js     # Context API Provider & Custom Hook
│           ├── reducer.js           # State reducer & basket total selector
│           ├── firebase.js          # Firebase SDK initialization (Auth + Firestore)
│           ├── axios.js             # Axios HTTP client configuration
│           ├── Header.js            # Top navbar, search input, basket badge
│           ├── Home.js              # Hero image carousel & product card grid
│           ├── Product.js           # Individual product card & Add to Basket
│           ├── Checkout.js          # Cart review view & promotional banner
│           ├── CheckoutProduct.js   # Cart item card with removal action
│           ├── Subtotal.js          # Price calculation & Proceed to Checkout CTA
│           ├── Login.js             # Sign-in & account registration forms
│           ├── Payment.js           # Stripe card element form & order placement
│           ├── Orders.js            # Historical order list query from Firestore
│           └── Order.js             # Order receipt card with unix time formatting
└── docs/                            # Interview-Ready Documentation Portal
```

---

## Dependency & Toolchain Directory

| Package Name | Exact Version | Type | Architectural Purpose |
|---|---|---|---|
| `react` | `^18.3.1` | `dependency` | Core component framework. |
| `firebase` | `^12.8.0` | `dependency` | BaaS SDK handling user authentication and Cloud Firestore database access. |
| `@stripe/stripe-js` | `^7.9.0` | `dependency` | Stripe client library initializing secure payment sessions. |
| `@stripe/react-stripe-js` | `^4.0.2` | `dependency` | React hooks (`useStripe`, `useElements`) and `CardElement` component. |
| `@material-ui/core` | `^4.11.0` | `dependency` | Material Design icon buttons and UI indicators. |
| `axios` | `^1.13.2` | `dependency` | HTTP client for external payment intent communication. |
| `moment` | `^2.30.1` | `dependency` | Date formatting library for order receipt timestamps. |
| `react-currency-format` | `^1.1.0` | `dependency` | Currency string formatting helper. |
