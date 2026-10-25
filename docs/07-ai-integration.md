# AI Integration Analysis: Amazon Clone

## Current Status: No AI Integration

The repository currently contains **No AI integration**. Products are statically populated in `Home.js`.

---

## Architectural Blueprint: AI Personalized Recommendation & Visual Product Search

```mermaid
sequenceDiagram
    autonumber
    actor Shopper as Customer
    participant UI as Amazon Home View
    participant AIProxy as Cloudflare Worker AI Gateway
    participant Gemini as Gemini 1.5 Flash API
    participant VectorDB as Pinecone Vector Store

    Shopper->>UI: Adds "Mechanical Gaming Keyboard" to basket
    UI->>AIProxy: POST /api/recommend { basket: ['Mechanical Gaming Keyboard'] }
    AIProxy->>VectorDB: Queries item vector nearest neighbors
    VectorDB-->>AIProxy: Returns related product IDs (Wrist Rest, Desk Mat)
    AIProxy-->>UI: Renders "Frequently Bought Together" carousel
```
