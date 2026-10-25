# API & Cloud Services Reference: Amazon Clone

## Firebase Services Matrix

| Service | SDK Method | Purpose | Authentication |
|---|---|---|---|
| **Firebase Auth** | `auth.signInWithEmailAndPassword(email, pass)` | Authenticates returning user session. | Public |
| **Firebase Auth** | `auth.createUserWithEmailAndPassword(email, pass)` | Registers new customer account. | Public |
| **Firebase Auth** | `auth.onAuthStateChanged(callback)` | Synchronizes active session with React Context. | Local Session |
| **Cloud Firestore** | `db.collection('users').doc(uid).collection('orders').set()` | Records confirmed purchase transaction. | Scoped to UID |
| **Cloud Firestore** | `db.collection('users').doc(uid).collection('orders').onSnapshot()` | Real-time subscription to order history. | Scoped to UID |

---

## Stripe Payments Gateway

| Endpoint / Method | Purpose | Payload |
|---|---|---|
| `stripe.confirmCardPayment(clientSecret, { payment_method })` | Authorizes & captures card charge. | `CardElement` token + billing details |
