# 🔗 Process payouts using saved payment methods

Payment method details of users are stored in a secure PCI-compliant locker, for processing payouts in future. These stored payment method details can be listed for a given customer, which returns a `payment_token` for processing payouts.

### How does it work?

#### Persisting payment method details in a secure PCI-compliant locker

There are two entry points to storing payment methods for a given customer.

* Persisting payment methods prior to processing transactions
  * &#x20;Payment methods can be created for a given customer using `/payment_methods` API.
  * This basically stores the passed payment method details in secure PCI-compliant locker.
* Persisting payment methods post a successful transaction
  * If a payment request was created with `"setup_future_usage": "off_session"` or if a payout request was created with `"recurring": true`, the payment method details will be stored in the secure locker once the transaction completes with a successful status.

#### Listing customer payment methods for processing payouts

Once the payment methods are stored in locker, they can be fetched using customer's list payment method API. This basically returns the identifiers for the saved payment methods along with a `payment_token` which can be used for processing transactions for a customer.

#### Processing payouts

Payouts can be created and processed using the `payment_token` for a given customer.

### How to get started?

We will be using HyperSwitch's hosted dashboard and Postman API collection and will be working only with the payout transactions for this bit. You can find API reference [here](https://api-reference.hyperswitch.io/api-reference/payouts/payouts--create).

Backend API endpoint - https://sandbox.hyperswitch.io

Dashboard - [https://app.hyperswitch.io](https://app.hyperswitch.io)

#### Pre-requisites

* Make sure processors are configured for processing payout transactions.
* Generate an API key by navigating to _**Developers**_ section.
* Note down your `merchant_id` from the dashboard's home page.

#### Steps

**Step 1 -** Import Postman collection from [here](https://api.postman.com/collections/9906252-c718fec5-b0ef-4fdb-b617-58e2dcb99a7b?access\_key=PMAT-01HP15F4SQTYT15XYETDWFP3DZ).

<figure><img src="../../../.gitbook/assets/image (8).png" alt=""><figcaption><p>Import Postman collection</p></figcaption></figure>

**Step 2 -** Navigate to collection's _**Variables**_ tab to set up below variables

* `baseUrl`
* `merchant_id`
* `api_key`

<figure><img src="../../../.gitbook/assets/image (9).png" alt=""><figcaption><p>Updating env variables in Postman collection</p></figcaption></figure>

**Step 3 -** Navigate to UseCase #1 section in the collection and execute in order.

**Step 4 -** Navigate to UseCase #2 section in the collection and execute in order.
