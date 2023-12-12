### How does Planship work?
Planship implements entitlement and subscription logic and stores all related data so you don’t have to. Planship lets you define product features, metered usage, subscription plans, and, finally, entitlements that decide what features and metered usage are available on which plan. With your product fully defined in Planship, you can use the Planship API to register/unregister customers, create/delete subscriptions, add/remove customers to/from subscriptions, retrieve customer entitlements, report usage, and more.

### Can Planship help me enforce feature limits for different customers?
Yes, Planship supports this via feature entitlements.

### What are Planship features and feature entitlements?
Features represent various levers that you can use to allow or limit access to your product features. Feature entitlements define how these levers are applied to customers on different plans. For instance, consider a product that does parallel processing of customer data, and different plans offer different levels of processing concurrency. To accomplish this with Planship, you would define an execution-concurrency feature, and then create entitlements that specify desired execution-concurrency values on different plans (for example, 1, 10 and 100 on Free, Personal and Business plans respectively).

### Does Planship offer different types of feature flags?
Yes, Planship supports the following feature types today:
Boolean - True/False flag for features that either exist or don’t on a given plan.
Flag - Similar to boolean but automatically defaults to False on any plan that doesn’t have an explicit entitlement for this feature
Integer - Represents features tied to numerical values that are not metered levers.
List - list of values to represent features like a list of 3rd-party integrations available on a given plan

### What is a feature entitlement in Planship?
Feature entitlements are rules defined on a plan level that specify a value of a given feature on a given plan.

### Can Planship track metered usage?
Yes. Planship enables you to define metered usage levers on a product level just like you define features. Once defined, you can report usage for these levers to Planship via the Planship API.

### Can Planship help me enforce usage limits for different customers?
Yes, Planship supports this via metered lever entitlements.

### How do metered lever entitlements work in Planship?
Metered lever entitlements are defined on a plan level to enforce limits for metered usage. As you emit usage records to Planship via the Planship API, Planship will process and aggregate usage data asynchronously, and return remaining allowed usage as a part of customer entitlements check.

### Does Planship support different types of metered usage?
Yes, Planship lets you define it as a part of entitlement configuration on a plan level.

### If I use Planship to enforce usage limits, can I still allow overage?
Yes. When you define a metered lever entitlement on a Planship plan, you can configure overage rules as a part of it.

### What happens if my customer goes over a usage limit I defined in Planship?
Planship lets you retrieve usage information including overage via the Planship API, and it’s entirely up to you what to do with this information.

### Can I track unique customer usage (e.g. Monthly Active Users) with Planship?
Yes, Planship supports tracking unique usage. You can include a unique usage identifier when reporting metered usage to Planship, and Planship will automatically take care of the rest.

### Can I combine different features and usage limits in a single Planship plan?
Yes, Planship supports even the most complex feature and usage rules by allowing any combination of entitlements of various types on any given plan.
