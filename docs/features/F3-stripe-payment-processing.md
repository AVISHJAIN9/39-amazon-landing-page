# F3: Stripe Payment Processing & Order Fulfillment

## Overview & Architecture
PCI-DSS compliant payment processing utilizing Stripe Elements `CardElement` and Cloud Firestore persistence.

```mermaid
flowchart TD
    SubmitCard[Customer submits card via Stripe CardElement] --> StripeConfirm[stripe.confirmCardPayment]
    StripeConfirm --> FirestoreLog[db.collection('users').doc(uid).collection('orders').set]
    FirestoreLog --> EmptyCart[dispatch EMPTY_BASKET]
    EmptyCart --> Redirect[history.replace('/orders')]
```

## Say It Out Loud
> "For the payment flow in `Payment.js`, I integrated the Stripe JavaScript SDK. The payment form embeds Stripe's `CardElement`, which securely tokenizes sensitive credit card data directly on Stripe's PCI-compliant servers without our frontend ever handling raw card numbers. When the shopper submits the order, the component calls `stripe.confirmCardPayment`. Once authorized, the transaction payload—including item breakdown, total amount, and timestamp—is committed to a subcollection in Cloud Firestore under the user's specific UID. Finally, an `EMPTY_BASKET` action clears the cart state, and the user is navigated to their orders screen."
