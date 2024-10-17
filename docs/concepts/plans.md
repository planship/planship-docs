# Pricing plans

In Planship, a plan represents a single pricing offering of your product. A Planship plan can represent one of the tiers of a multi-tier pricing model, a one-off package that never expires, a temporary add-on to a recurring subscription plan, or anything in between.

A plan has a subscription period, renewal rules, subscriber limits, and a set of [***entitlements***](#entitlements) that define how various [*feature*](feature-levers.md) and [*metered*](metered-levers.md) pricing levers are applied to customers of the plan.

Customers can subscribe to a plan either by creating a new subscription or by joining an existing subscription (I.e. a team account).

## Subscription periods and renewals

Each plan has a subscription duration and renewal configuration. This configuration enables subscription plan changes at the end of a subscription period, as well as the renewal or reset of metered-lever usage.

- *Subscription duration* - expressed as a name of the time unit and a number of units. Time unit name can be one of the following: *minute*, *hour*, *day*, *week*, *month*, *year*, or *infinity*. For *infinity*, the number of units will be ignored.
- *Subscription renewal* - consists of the *auto-renew* flag. It specifies whether a subscription should automatically renew or not.
- *Renewal plan* - the plan the subscription should change to at the end of the subscription period if the *auto-renew* flag is set to `true`. If *auto-renew* isn't enabled, the subscription will lapse and default to no plan at the end of the subscription period.

## Entitlements

 Entitlements define how various product [feature](feature-levers.md) and [metered](metered-levers.md) levers apply to a plan. They're used to determine what a customer on a subscription to a plan can and can't do at a point in time. If an explict entitlement to a lever isn't defined, the default value defined on the lever is applied as an implicit entitlement.

## Subscriber limits (teams and seats)

By default, every plan subscription is limited to a single customer. This limit can be changed to any arbitrary number or removed entirely to allow unlimited customers per subsciption. Subscriber limits can be used for implementing team subscriptions or per-seat pricing models.


## Subscribing and unsubscribing customers

A customer can be subscribed to a plan by either creating a new plan subscription for them, adding them to an existing subscription (e.g. a team subscription), or changing a plan on one of their active subscriptions.

Similarily, customers can be unsubscribed from a plan by deleting their active subscription, removing them from a subscription (e.g. a team subscription), or by letting their active subscription expire (no auto-renew) or renew to a different plan.

## Individual vs. team subscriptions

By default, Planship plans have a subscribers limit of `1`, representing a non-team setup where each customer has their own subscription (or more than one if needed) and subscription resources (E.g. metered usage) aren't shared between customers.

In a team subscription model (I.e. subscribers limit set to more than 1), customers can be added to or removed from an existing subscription by a subscription administrator.

### Subscription administrators

The _subscription administrator_ is a customer role tied to a specific subscription. If a customer is an administrator on a subscription, they can modify the subscription (E.g. change plan, renew plan, add and remove customers, etc.).

The customer who creates a subscription is automatically the administrator for that subscription. Every subscription needs to have at least one administrator with no upper limit on the number of administrators.
