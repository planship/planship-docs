# Welcome to Planship

Planship enables you to quickly build subscription-related logic that scales with your business, whether you price on features, seats, usage, or any combination of these. Planship doesn’t replace existing billing solutions; it works alongside them. Get started in minutes with Planship’s lightweight SDKs and enjoy clutter-free pricing logic decoupled from product code.

## How it works

**1. Define pricing levers and plans**

Identify your product's pricing levers; these can be any combination of [features](/concepts/feature-levers), [metered usage](/concepts/metered-levers), and [seats](/concepts/plans/#subscriber-limits-teams-and-seats). Then define them with the [Planship console](https://app.planship.io). Finally, use the console to create plans and connect them to your pricing levers via [entitlements](/concepts/plans/#entitlements).

**2. Instrument your code**

Use the [Planship SDK](/integration/#getting-started-with-planship-sdks) of your choice to retrieve and use entitlement data, report metered usage, register new customers with Planship, and manage their plan subscriptions. With Planship, there's no need for pricing logic based on customer plan IDs, names, account numbers, etc. Planship abstracts everything away and lets you keep your product code and data model free of clutter.

**3. Iterate on pricing and manage customers**

Use the Planship Console to manage customers and subscriptions, and tweak and iterate on your pricing plans without touching product code. The only time you'll need to instrument your code again is when adding a quick entitlement check for a new pricing lever.
