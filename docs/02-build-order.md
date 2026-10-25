# Step-by-Step Rebuild Guide: Amazon Clone

Constructing the Amazon Clone from scratch in strict architectural dependency order:

```mermaid
flowchart TD
    S1[Step 1: Setup React App & Material-UI] --> S2[Step 2: Context API & Reducer Setup]
    S2 --> S3[Step 3: Header Component & Navbar Layout]
    S3 --> S4[Step 4: Product Card & Add to Basket Dispatch]
    S4 --> S5[Step 5: Checkout View & Subtotal Calculations]
    S5 --> S6[Step 6: Firebase Auth Integration Login/Register]
    S6 --> S7[Step 7: Stripe Payment Flow & CardElement]
    S7 --> S8[Step 8: Cloud Firestore Orders Collection & History]
```

### Key Snippet: Global Context Provider (`src/StateProvider.js`)

```javascript
import React, { createContext, useContext, useReducer } from "react";

// Prepares the dataLayer
export const StateContext = createContext();

// Wrap our app and provide the Data layer
export const StateProvider = ({ reducer, initialState, children }) => (
  <StateContext.Provider value={useReducer(reducer, initialState)}>
    {children}
  </StateContext.Provider>
);

// Pull information from the data layer
export const useStateValue = () => useContext(StateContext);
```
