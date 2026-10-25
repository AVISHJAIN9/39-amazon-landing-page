# Project Pitch: Amazon E-Commerce Platform

## 30-Second Elevator Pitch
"I built a production-grade Amazon e-commerce platform using React 18, Firebase Authentication, Cloud Firestore, and Stripe. The application features full user account management, a centralized shopping basket managed via React's Context API and useReducer, dynamic subtotal calculations, secure credit card transactions processed through Stripe Elements, and persistent order history logs stored in Firestore."

---

## 2-Minute Technical Interview Pitch
"The Amazon Clone is a full-stack e-commerce application engineered to handle the complete customer lifecycle from authentication to order fulfillment. 

For the frontend, I utilized React 18 with React Router for single-page routing across the storefront, cart, checkout, payment, and orders views. To manage state cleanly without third-party library overhead like Redux, I implemented a global data layer combining the React Context API with the `useReducer` hook inside `StateProvider.js`. This allows components anywhere in the tree to dispatch typed actions—such as `ADD_TO_BASKET` or `REMOVE_FROM_BASKET`—while keeping basket mutations immutable and enabling linear-time basket total calculations.

For security and backend infrastructure, I leveraged Google Cloud Firebase. Firebase Authentication handles credential validation and session persistence via `auth.onAuthStateChanged`. When a customer initiates checkout, the application integrates with Stripe using `@stripe/react-stripe-js` to securely capture card details via `CardElement`. Upon payment confirmation, the transaction payload—including item lists, order amounts, and creation timestamps—is committed directly into a NoSQL Cloud Firestore collection scoped to the authenticated user's UID. The result is a secure, reactive e-commerce portal delivering enterprise-grade purchasing flows."
