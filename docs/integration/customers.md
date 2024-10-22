!!! tip "Using Stripe?"
    If you already use the Planship Stripe app, all of your customers and their subscriptions are automatically mirrored in Planship. Head straight to [Get Customer Entitlements](./entitlements.md) and [Report usage](./usage.md) integration guides.
    <br/><br/>
    Interested in the Planship Stripe app? Head to our [Stripe integration HOWTO guide](../howtos/use-planship-with-stripe.md) to learn more and get started.

Registering a [customer](../concepts/customers.md) with Planship enables your product to do the following:

 - Subscribe/unsubscribe customers to Planship plans
 - Retrieve feature and metered entitlements for a customer
 - Report and retrieve metered usage for a customer

When registering a customer with Planship, you can optionally provide their name, email and metadata.

=== "JavaScript"

    ```javascript
    const customer = await planship.createCustomer(
      {
        'name': 'Jenny Doe',
        'email': 'jenny.doe@example.com',
        'metadata': { 'phone': '111-867-5309' }
      }
    )
    ```

=== "TypeScript"

    ```typescript
    const customer: Customer = await planship.createCustomer(
      {
        'name': 'Jenny Doe',
        'email': 'jenny.doe@example.com',
        'metadata': { 'phone': '111-867-5309' }
      }
    )
    ```

=== "Python"

    ```python
    customer = planship.create_customer(
        {
            "name": "Jenny Doe",
            "email": "jenny.doe@example.com",
            "metadata": { "phone": "111-867-5309" }
        }
    )
    ```

=== "Java"

    ```java
    Customer customer = planship.createCustomer(
        new CreateCustomerParameters()
            .name("Jenny Doe")
            .email("jenny.doe@example.org")
            .metadata({ "phone": "111-867-5309" })
    )
    ```

The returned `customer` object contains a customer `id` that should be stored in your product's customer database for future customer operations. If you'd rather not store anything, you can specify your own customer ID.

### Using your own customer ID

If you would rather not store Planship customer IDs in your product database, you can provide your own ID to Planship when registering a customer as an _alternative ID_.

=== "JavaScript"

    ```javascript
    const customer = await planship.createCustomer(
      {
        'alternativeId': '<your_unique_customer_id>',
        'name': 'Jenny Doe',
        'email': 'jenny.doe@example.org',
        'metadata': { 'phone': '111-867-5309' }
      }
    )
    ```

=== "TypeScript"

    ```typescript
    const customer: Customer = await planship.createCustomer(
      {
        'alternativeId': '<your_unique_customer_id>',
        'name': 'Jenny Doe',
        'email': 'jenny.doe@example.org',
        'metadata': { 'phone': '111-867-5309' }
      }
    )
    ```

=== "Python"

    ```python
    customer = planship.create_customer(
        {
            "alternative_id": "<your_unique_customer_id>",
            "name": "Jenny Doe",
            "email": "jenny.doe@example.org",
            "metadata": { "phone": "111-867-5309" }
        }
    )
    ```

=== "Java"

    ```java
    Customer customer = planship.createCustomer(
        new CreateCustomerParameters()
            .alternativeId("<your_unique_customer_id>")
            .name("Jenny Doe")
            .email("jenny.doe@example.org")
            .metadata({ "phone": "111-867-5309" })
    )
    ```

Once created, you can use the alternative ID to identify the customer with Planshup instead of the `customer.id` value returned when registering a new customer. The alternative ID can be any string up to 256 characters long that's unique within your Planship organization. You can use your customer email, database ID, or anything else that uniquely identifies your customer.

### Registering a customer with no data

Finally, if you would rather not place any customer information into Planship, you can register your customer without any additional data.

=== "JavaScript"

    ``` js
    const customer = await planship.createCustomer()
    ```

=== "TypeScript"

    ``` typescript
    const customer: Customer = await planship.createCustomer()
    ```


=== "Python"

    ``` py
    customer = planship.create_customer()
    ```

=== "Java"

    ``` java
    Customer customer = planship.createCustomer()
    ```
