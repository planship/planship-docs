### How does Planship customer and subscription management work?
You start by registering your customers with Planship. Once your customers are registered, you can subscribe them to any plan that you defined for your product in Planship, add/remove them to/from existing subscriptions (If you support team subscriptions), modify subscriptions (E.g. upgrade or downgrade a subscription plan), and more.

### Do I need to register all of my customers with Planship?
Yes, Planship requires that all customers be registered so you can manage their subscriptions, entitlements, and usage via Planship.

### What does registering a customer with Planship mean?
Registering a customer with Planship simply means obtaining a unique customer ID from Planship that you will then use to identify that customer in Planship. Planship customer ID is the default way to identify your customers so you can manage their subscriptions, retrieve entitlements, and track usage via Planship.
How do I register my customers with Planship?
Customer registration can be done either via the Planship API (E.g. when a new customer signs up for your product), or as a batch operation via the Planship Management UI, CLI, or API.

### I don’t want to store a Planship customer ID in my product data model. Can I use my internal customer ID to identify my customers instead?
Yes, Planship lets you use your internal customer ID when registering a new customer as long as that ID is a string that’s unique across all of your customers within your organization. You can use that alternative ID to manage subscriptions, retrieve entitlements, and track usage of your customers via Planship.

### Does Planship store PII or any other sensitive customer data (e.g. payment instruments)?
No, Planship doesn’t require any data when registering a customer. However, you can pass extra data to Planship like a customer’s name, email, and metadata to make it easier to identify customers when using Planship Management Dashboard and CLI.

### I would like my customers to be able to subscribe to more than one plan at the same time. Does Planship support this model?
Yes, Planship supports multiple subscriptions per customer, and it will automatically calculate and resolve all entitlements across all subscriptions of a customer.

### Can Planship help me manage team subscriptions?
Yes, Planship supports team subscriptions where multiple customers belong to the same subscription. Planship API lets you add, remove, and modify subscription customers, and it will automatically resolve all entitlements across all customers on a single subscription.

### How can I enable team subscriptions on my Planship plan?
This is done as a part of a Planship plan definition where you can choose either a fixed or an unlimited number of subscribers on any given plan subscription. You can also tie a number of subscribers to a plan pricing configuration so you can charge your customers using a per-seat pricing model.

### How do feature and metered entitlements work with team subscriptions?
Feature entitlements work in the same way in team subscriptions as they do on individual ones. For metered usage levers, you can decide if entitlements apply to individual subscription customers, or an entire subscription. For instance, if you define a 1,000 compute-hours limit on one of your plans, you can decide if this limit caps combined usage of all subscription customers or if it’s applied per customer.

### Are team subscriptions tied to per-seat pricing?
They can be. Planship lets you decide if you’d like to charge per-seat price for additional subscription customers or not. If you choose to do so, Planship supports flat, graduated, volume and discounted per-seat pricing.
