# Master Feature Inventory: Amazon Clone

## Subsystem Matrix

| Feature ID | Feature Name | Core Implementation Files | Primary Architectural Mechanism |
|---|---|---|---|
| **F1** | Shopping Basket State Management | `StateProvider.js`, `reducer.js`, `Product.js`, `Header.js` | React Context API + `useReducer`, immutable array operations, basket count badge. |
| **F2** | Firebase User Authentication | `Login.js`, `firebase.js`, `App.js` | Firebase Auth (`signInWithEmailAndPassword`, `createUserWithEmailAndPassword`), `onAuthStateChanged` listener. |
| **F3** | Stripe Payment Processing | `Payment.js`, `axios.js`, `@stripe/react-stripe-js` | Stripe `CardElement`, client secret confirmation, asynchronous payment state. |
| **F4** | Firestore Order History | `Orders.js`, `Order.js`, `firebase.js` | Firestore query: `db.collection('users').doc(uid).collection('orders').orderBy('created', 'desc')`. |
| **F5** | Dynamic Subtotal Calculator | `Subtotal.js`, `reducer.js:L5` | Array `reduce()` accumulator calculating total price, `react-currency-format`. |
| **F6** | Product Rating & Cart Removal | `Product.js`, `CheckoutProduct.js`, `reducer.js:L21` | Array index search, `.splice(index, 1)` removal without mutating duplicate product IDs. |

---

## Detailed Feature Specifications

### F1: Shopping Basket State Management
- **User Facing Behavior**: Clicking "Add to Basket" updates the navbar cart badge immediately; checkout page reflects updated item count.
- **Trace**: `Product.js` -> `dispatch({ type: 'ADD_TO_BASKET', item: {...} })` -> `reducer.js` -> `Header.js` reads `basket?.length`.
- **Say It Out Loud**:
> "I built the global shopping cart state using React's Context API and the `useReducer` hook in `StateProvider.js` and `reducer.js`. When a customer clicks 'Add to Basket' on any product card, the component dispatches an `ADD_TO_BASKET` action containing the item metadata. The reducer creates a new immutable basket array by spreading previous items alongside the new payload. In `Header.js`, the cart count badge subscribes to the basket slice of state, instantly re-rendering the updated number without prop drilling."

---

### F3: Stripe Payment Processing & Order Fulfillment
- **User Facing Behavior**: Customer enters credit card details on the `/payment` page; upon clicking "Buy Now", the card is securely verified and charged, the shopping basket is cleared, and the customer is redirected to their orders receipt.
- **Trace**: `Payment.js` -> `stripe.confirmCardPayment` -> `db.collection('users').doc(user.uid).collection('orders').doc(paymentIntent.id).set({...})` -> `dispatch({ type: 'EMPTY_BASKET' })`.
- **Say It Out Loud**:
> "For the payment flow in `Payment.js`, I integrated the Stripe JavaScript SDK. The payment form embeds Stripe's `CardElement`, which securely tokenizes sensitive credit card data directly on Stripe's PCI-compliant servers without our frontend ever handling raw card numbers. When the shopper submits the order, the component calls `stripe.confirmCardPayment`. Once authorized, the transaction payload—including item breakdown, total amount, and timestamp—is committed to a subcollection in Cloud Firestore under the user's specific UID. Finally, an `EMPTY_BASKET` action clears the cart state, and the user is navigated to their orders screen."
