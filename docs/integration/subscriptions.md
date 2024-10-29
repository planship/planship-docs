Once a customer is [successfully registered with Planship](customers.md), you can subscribe them to a [Planship plan](../concepts/plans.md) by creating a new subscription for them using their ID and the slug of the desired plan.

??? question "Using Stripe?"
    If you use the Planship Stripe app, all of your customers and their subscriptions are automatically mirrored in Planship. You can go straight to the [Getting Customer Entitlements](entitlements.md) and [Reporting Usage](usage.md) integration guides.
    <br/><br/>
    Interested in the Planship Stripe app? Head to our [Stripe integration HOW-TO guide](../howtos/use-planship-with-stripe.md) to learn more.

=== "JavaScript"

    ``` js
    const subscription = await planship.createSubscription(
      customer.id, // customer ID
      'medium', // plan slug
    )
    ```

=== "TypeScript"

    ``` ts
    const subscription: SubscriptionWithPlan = await planship.createSubscription(
      customer.id, // customer ID
      'medium', // plan slug
    )
    ```

=== "Python"

    ``` py
    subscription = planship.create_subscription(
        customer.id, # customer ID
        "medium", # plan slug
    )
    ```

=== "Java"

    ``` java
    SubscriptionWithPlan subscription = planship.createSubscription(
        customer.getId(), // customer ID
        "medium" // plan slug
    )
    ```

The returned `subscription` object contains a subscription `id`, which is required when managing and modifying subscriptions. However, unlike customer IDs, subscription IDs don't need to be persisted in your product database as you can retrieve them programatically for a customer.

!!! info
    The *customer ID* can be the Planship-generated customer ID or your own ID provided to Planship as an [alternative ID](customers.md#using-your-own-customer-id).

### Listing customer subscriptions

To find a subscription ID, simply list all subscriptions for a given customer.

=== "JavaScript"

    ``` js
    const subscriptions = await planship.listSubscriptions(
      customer.id // customer ID
    )
    ```

=== "TypeScript"

    ``` ts
    const subscription: Array<CustomerSubscriptionWithPlan> = await planship.listSubscriptions(
      customer.id // customer ID
    )
    ```

=== "Python"

    ``` py
    subscriptions = planship.list_subscriptions(
        customer.id # customer ID
    )
    ```

=== "Java"

    ``` java
    List<CustomerSubscriptionWithPlan> subscriptions = planship.listSubscriptions(
        customer.getId() // customer ID
    )
    ```

The return value is a list of subscription objects that contain a subscription ID, plan, renew-plan slug, the customer's role in the subscription, and more.

### Change subscription plan and renew plan (upgrades and downgrades)

When a customer upgrades their plan, you may want to apply this change immediately. This can be done by changing the subscription plan.

=== "JavaScript"

    ``` js
    const subscription = await planship.changeSubscriptionPlan(
      customer.id, // customer ID
      subscription.id, // existing subscription ID
      'large', // new plan slug
    )
    ```

=== "TypeScript"

    ``` ts
    const subscription: CustomerSubscriptionWithPlan = await planship.changeSubscriptionPlan(
      customer.id, // customer ID
      subscription.id, // existing subscription ID
      'large', // new plan slug
    )
    ```

=== "Python"

    ``` py
    subscription = planship.change_subscription_plan(
        customer.id, # customer ID
        subscription.id, # subscription ID
        "large", # new plan slug
    )
    ```

=== "Java"

    ``` java
    CustomerSubscriptionWithPlan subscription = planship.changeSubscriptionPlan(
        customer.getId(), // customer ID string
        subscription.getId(), // subscription ID
        "large", // new plan slug
    )
    ```

The same operation can be used when customers downgrade their subscriptions with an immediate effect (usually accompanied by a refund). However, downgrades are often processed at the end of a subscription period. This way, customers continue to have access to all of the product resources (like [features](../concepts/feature-levers.md) and/or [usage limits](../concepts/metered-levers.md)) they already paid for. To accomplish this, change the subscription's renew plan instead.

=== "JavaScript"

    ``` js
    const subscription = await planship.changeSubscriptionRenewPlan(
      customer.id, // customer ID
      subscription.id, // existing subscription ID
      'large', // new renew plan slug
    )
    ```

=== "TypeScript"

    ``` ts
    const subscription: CustomerSubscriptionWithPlan = await planship.changeSubscriptionRenewPlan(
      customer.id, // customer ID
      subscription.id, // existing subscription ID
      'large', // new renew plan slug
    )
    ```

=== "Python"

    ``` py
    subscription = planship.change_subscription_renew_plan(
        customer.id, # customer ID
        subscription.id, # subscription ID
        "large", # new renew plan slug
    )
    ```

=== "Java"

    ``` java
    CustomerSubscriptionWithPlan subscription = planship.changeSubscriptionRenewPlan(
        customer.getId(), // customer ID string
        subscription.getId(), // subscription ID
        "large", // new renew plan slug
    )
    ```

Instead of downgrading a subscription to a different plan, you may want to cancel it completely. To do so, set the subsciptions's *auto renew* property to *false*.

=== "JavaScript"

    ``` js
    const subscription = await planship.setSubscriptionAutoRenew(
      customer.id, // customer ID
      subscription.id, // existing subscription ID
      false, // set subscription auto-renew to false
    )
    ```

=== "TypeScript"

    ``` ts
    const subscription: CustomerSubscriptionWithPlan = await planship.setSubscriptionAutoRenew(
      customer.id, // customer ID
      subscription.id, // existing subscription ID
      false, // set subscription auto-renew to false
    )
    ```

=== "Python"

    ``` py
    subscription = planship.set_subscription_auto_renew(
        customer.id, # customer ID
        subscription.id, # subscription ID
        False, # set subscription auto-renew to false
    )
    ```

=== "Java"

    ``` java
    CustomerSubscriptionWithPlan subscription = planship.setSubscriptionAutoRenew(
        customer.getId(), // customer ID string
        subscription.getId(), // subscription ID
        false, // set subscription auto-renew to false
    )
    ```

The same call can be used to set a subscription's *auto renew* property to *true*.

## Team subscriptions

### Add a customer to a team subscription

If your plans support team subscriptions, instead of creating a new subscription for a customer, you may want to add them to an exisiting subscription.

=== "JavaScript"

    ``` js
    const newSubscriptionCustomer = await planship.addSubscriptionCustomer(
      customer.id, // customer ID
      subscription.id, // existing subscription ID
      newCustomer.id, // new subscription customer ID
    )
    ```

=== "TypeScript"

    ``` ts
    const newSubscriptionCustomer: SubscriptionCustomer = await planship.addSubscriptionCustomer(
      customer.id, // customer ID
      subscription.id, // existing subscription ID
      newCustomer.id, // new subscription customer ID
    )
    ```

=== "Python"

    ``` py
    new_subscription_customer = planship.add_subscription_customer(
        customer.id, # customer ID
        subscription.id, # existing subscription ID
        new_customer.id, # new subscription customer ID
    )
    ```

=== "Java"

    ``` java
    SubscriptionCustomer newSubscriptionCustomer = planship.addSubscriptionCustomer(
        customer.getId(), // customer ID
        subscription.getId(), // existing subscription ID
        newCustomer.getId(), // new subscription customer ID
    )
    ```

Please note that this operation requires two customer IDs:

 - ID of an existing subscription customer to execute the operation, has to be an [administrator](../concepts/plans.md#subscription-administrators) of the subscription with a given ID
 - ID of a customer to be added to the subscription with a given ID


### Remove a customer from a team subscription

Customers can be also removed from subscriptions they belong to.

=== "JavaScript"

    ``` js
    const removedSubscriptionCustomer = await planship.removeSubscriptionCustomer(
      customer.id, // customer ID
      subscription.id, // existing subscription ID
      customerToRemove.id, // ID of a customer being removed
    )
    ```

=== "TypeScript"

    ``` ts
    const removedSubscriptionCustomer: SubscriptionCustomerInDbBase = await planship.removeSubscriptionCustomer(
      customer.id, // customer ID
      subscription.id, // existing subscription ID
      customerToRemove.id, // ID of a customer being removed
    )
    ```

=== "Python"

    ``` py
    removed_subscription_customer = planship.remove_subscription_customer(
        customer.id, # customer ID
        subscription.id, # existing subscription ID
        new_customer.id, # ID of a customer being removed
    )
    ```
=== "Java"

    ``` java
    SubscriptionCustomerInDbBase removedSubscriptionCustomer =  planship.removeSubscriptionCustomer(
        customer.getId(), // customer ID
        subscription.getId(), // existing subscription ID
        customerToRemove.getId(), // ID of a customer being removed
    )
    ```

Just as when adding a customer to a subscription, two customer IDs are required.

!!! info
    Customers can remove themselves from a subscription as long as they are not the only administrator or subscriber of the subscription.
