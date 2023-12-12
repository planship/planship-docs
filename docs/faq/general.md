### What is Planship?
Planship is a software service that makes plan and subscription code easy.

### What problem does Planship solve?
Today, developers implement pricing logic as a part of their product’s code. It typically starts as simple boilerplate code to check a customer's subscription plan, but, as product features and pricing evolve, the pricing logic becomes increasingly complex with pricing-related flags in the data model, checks for legacy plans, exceptions for specific customers, and enforcement of feature and usage limitations. While services like Stripe make it extremely easy to collect customers’ payment information and set up one-time charges or recurring subscriptions, when it comes to subscription related business logic, developers are on their own. Planship solves this problem so developers can focus on what matters most - building great apps.

### I’m building a new SaaS product. Toggling a couple of features based on my customer’s plan ID seems simple enough. Why should I use Planship?
What typically starts as simple boilerplate code can quickly become a complex, difficult to maintain mess of checks for legacy plans and special cases for individual customers. Planship provides a foundation for building scalable and easy-to-maintain pricing logic with no upfront cost.

### I’m a manager/owner of a SasS product. Our pricing logic has been built into the product code. Why should I consider migrating to Planship?
With Planship, product owners define pricing levers like features and metered usage, and developers instrument the product code to check for these entitlements using the Planship API. Once the initial integration is done, product owners can experiment and iterate on pricing without the need to write any additional code.

### Can’t I just use Stripe or Recurly for this?
No. While Stripe makes it extremely easy to collect payment information, set up one-time or recurring charges, and takes care of the billing mechanics like retries, it leaves the implementation of pricing-related logic to developers. Enforcing feature and usage limits for different subscriptions, tracking usage, and managing team subscriptions are some of the common tasks that developers have to build themselves.

### Is Planship an alternative to Stripe or Recurcly?
Not entirely. While you can use Planship for all aspects of your pricing infrastructure, including billing, you can also run it alongside your existing billing solution as a complimentary service. This allows you to take advantage of Planship’s entitlement, subscription, and metering capabilities while keeping your existing billing integration intact.

### Do I need to rewrite my existing Stripe integration code to use Planship?
No, Planship can be used as a complimentary service with Stripe to enforce feature and usage entitlements, track metering, manage team subscriptions, and more.

### Can Planship work alongside my current payment processor (e.g. Stripe)?
Yes, Planship has been designed as a complementary product to payment processors like Stripe.

### Can I use Planship instead of Stripe to charge my customers?
Yes, this is supported by Planship Cloud and a self-hosted version of Planship offered under a commercial license. You can define pricing for your plans in Planship, and Planship will take care of the rest using Stripe as a payment processor.

### Does Planship Cloud exclusively support Stripe? Can I use a different payment processor?
Planship Cloud will initially launch with Stripe integration, but other payment processors will be added later based on customer demand. Planship is extensible by design and isn’t tied to any single payment gateway.
