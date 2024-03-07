Once a customer is [registered with Planship](/integration/customers) and [subscribed to one or more Planship plans](/integration/subscriptions), you can check their entitlements.

=== "JavaScript"

    ``` js
    const entitlements = await planship.getEntitlements(
      customer.id // customer ID
    )
    ```

=== "TypeScript"

    ``` ts
    const entitlements: JSONValue = await planship.getEntitlements(
      customer.id // customer ID
    )
    ```

=== "Python"

    ``` py
    entitlements = planship.get_entitlements(
        customer.id # customer ID
    )
    ```

=== "Java"

    ``` java
    Object entitlements = planship.getEntitlements(
        customer.getId() // customer ID
    )
    ```

Entitlements are returned as a dictionary containing all feature and metered entitlements for the customer according to their current subscriptions. Entitlement values for individual levers are keyed by lever slugs.


=== "JavaScript"

    ``` js
    {
      'premium-button': true,
      'subscription-button-clicks': 75,
      'max-projects': 5,
      'project-types': [ 'Single', 'Random' ],
      'analytics-panel': false,
    }
    ```

=== "TypeScript"

    ``` ts
    {
      'premium-button': true,
      'subscription-button-clicks': 75,
      'max-projects': 5,
      'project-types': [ 'Single', 'Random' ],
      'analytics-panel': false,
    }
    ```

=== "Python"

    ``` py
    {
        "premium-button": True,
        "subscription-button-clicks": 75,
        "max-projects": 5,
        "project-types": [ "Single", "Random" ],
        "analytics-panel": False,
    }
    ```

=== "Java"

    ``` java
    {
        subscription-button-clicks=75.0,
        max-projects=5.0,
        project-types=[Single, Random],
        premium-button=true,
        button-clicks-per-project-per-day={null=10.0},
        analytics-panel=false
    }
    ```

!!!note

    Metered lever entitlement values represent the amount of metered usage available to a customer. For instance, if a customer has a limit of 100 SMS messages per subscription period, and they've already used 25 messages in the current period, the entitlements value for the lever (`subscription-sms-messages`) will be 75. If you'd like to get the current usage for a customer, see [`getLeverUsage`](/integration/usage/#check-current-usage).

### Receiving entitlements via a WebSocket connection

When using a Planship JavaScript SDK (`@planship/fetch` or `@planship/axios`) or Planship React SDK (`@planship/react`), you can also receive entitlements via a WebSocket connection every time they change. Simply pass your callback function to the `getEntitlements` call, and Planship will notify your client when it detects any change in entitlements for the customer.

=== "JavaScript"

    ``` js
    function onEntitlementsChange(entitlements) {
      // process an updated entitlements object here
    }

    const entitlements = await planship.getEntitlements(
      customer.id, // customer ID
      onEntitlementsChange, // entitlements changed callback
    )
    ```

=== "TypeScript"

    ``` ts
    function onEntitlementsChange(entitlements: JSONValue): void {
      // process an updated entitlements object here
    }

    const entitlements: JSONValue = await planship.getEntitlements(
      customer.id, // customer ID
      onEntitlementsChange, // entitlements changed callback
    )
    ```

When using the Planship React SDK [PlanshipCustomer provider](https://github.com/planship/planship-react?tab=readme-ov-file#planshipcustomer-context-provider), the callback is configured automatically to make consuming Planship entitlements in React and Next.js even simpler.

```js
import { usePlanshipCustomer } from '@planship/react'

export default function YourComponent({ children }) {
  const { entitlements } = usePlanshipCustomer()

  return (
    // Render some content using Planship customer entitlements
  )
}
```

### Entitlements across multiple subscriptions

If a customer belongs to multiple subscriptions, Planship will combine and calculate entitlements across all of the customer's subscriptions.

Entitlement values are calculated using an approach where the most permissive (or generous) plan entitlements take priority.
