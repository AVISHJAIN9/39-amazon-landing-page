# Architectural Decision Records (ADRs): Amazon Clone

| ADR ID | Decision Title | Chosen Option | Alternatives Considered | Deciding Factors | Trade-Off Accepted | Revisit Trigger |
|---|---|---|---|---|---|---|
| **ADR-01** | State Architecture | Context API + useReducer | Redux Toolkit, MobX | Built-in React simplicity; zero dependency overhead | Potential unnecessary re-renders on deep trees | App exceeds 50 global actions |
| **ADR-02** | Payment Processing | Stripe Elements | Custom card form, PayPal | Complete PCI-DSS scope elimination; card data tokenization | 2.9% + 30c fee per transaction | Enterprise merchant volume discounts |
| **ADR-03** | Database Layer | Cloud Firestore | MongoDB Atlas, PostgreSQL | Native real-time subscriptions (`onSnapshot`), subcollection security | NoSQL complex joining limitations | Complex reporting & analytics required |
| **ADR-04** | Authentication | Firebase Auth | Auth0, Custom JWT Server | Instant email/password integration & session persistence | Vendor lock-in to Google Cloud | Multi-cloud enterprise migration |
