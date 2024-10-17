# Welcome to Planship

Planship enables you to quickly build subscription-related logic that scales with your business. Working alongside your existing billing solution, Planship enables pricing on any combination of features, seats, and usage. Get started in minutes using our lightweight SDKs and enjoy clutter-free pricing logic decoupled from product code.

## How it works

**1. Define pricing levers and plans**

Identify your product's pricing levers: [features](concepts/feature-levers.md), [metered usage](concepts/metered-levers.md), and/or [seats](concepts/plans.md#subscriber-limits-teams-and-seats). Define them with the [Planship console](https://app.planship.io) and connect them to your plans via [entitlements](concepts/plans.md#entitlements).

**2. Instrument your code**

Use the [Planship SDK](integration/index.md#getting-started-with-planship-sdks) of your choice to fetch entitlement data, report metered usage, register new customers, and manage their plan subscriptions. Once complete, the only time you'll need to instrument your code again is when adding a quick entitlement check for a new pricing lever or emitting a new usage metric.

**3. Iterate on pricing and manage customers**

Effortlessly iterate on your pricing plans from the Planship Console without modifying product code.
