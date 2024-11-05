If metered usage is a pricing dimension of your product and you've defined one or more [metered levers](../concepts/metered-levers.md), you will likely need to report customer usage to Planship. Metered usage is reported for a [*metering ID*](../concepts/metered-levers.md#metering-id), which is associated with one or more metered levers.

=== "JavaScript"

    ``` js
    const meteringRecord = await planship.reportUsage(
      customer.id, // customer ID
      'some-metering-id', // metering ID
      15, // reported usage
    )
    ```

=== "TypeScript"

    ``` ts
    const meteringRecord: MeteringRecord = await planship.reportUsage(
      customer.id, // customer ID
      'some-metering-id', // metering ID
      15, // reported usage
    )
    ```

=== "Python"

    ``` py
    metering_record = planship.report_usage(
        customer.id, # customer ID
        "some-metering-id", # metering ID
        15, # reported usage
    )
    ```

=== "Java"

    ``` java
    MeteringRecord meteringRecord = planship.reportUsage(
        customer.getId(), // customer ID
        "some-metering-id", // metering ID
        15, // reported usage
    )
    ```

!!! question "Using Stripe?"
    If you use the Planship Stripe app, the customer ID is your Stripe customer ID prefixed with **`stripe`** (E.g. **`stripe:cus_Qv7TP2s0BZ6XAV`** for Stripe customer **`cus_Qv7TP2s0BZ6XAV`**).

Every time usage is reported, Planship creates a metering record for traceability. Metering records are automatically processed and aggregated in the background and included in the totals for all usage levers with a matching *metering ID*.

### Reporting bucketed usage

If your product defines usage levers that take advantage of *usage per bucket* or *unique buckets* [aggregation formulas](../concepts/metered-levers.md#formula), you will want to include a *bucket* identifier when reporting usage to Planship.

=== "JavaScript"

    ``` js
    const meteringRecord = await planship.reportUsage(
      customer.id, // customer ID
      'some-metering-id', // metering ID
      15, // reported usage
      'bucket-name', // usage bucket
    )
    ```

=== "TypeScript"

    ``` ts
    const meteringRecord: MeteringRecord = await planship.reportUsage(
      customer.id, // customer ID
      'some-metering-id', // metering ID
      15, // reported usage
      'bucket-name', // usage bucket
    )
    ```

=== "Python"

    ``` py
    metering_record = planship.report_usage(
        customer.id, # customer ID
        "some-metering-id", # metering ID
        15, # reported usage
        "bucket-name", // usage bucket
    )
    ```

=== "Java"

    ``` java
    MeteringRecord meteringRecord = planship.reportUsage(
        customer.getId(), // customer ID
        "some-metering-id", // metering ID
        15, // reported usage
        "bucket-name", // usage bucket
    )
    ```

The specified bucket value becomes part of the metering record and is used by Planship's usage processing engine.

## Check current usage

While the remaining usage is returned as part of a customer's [entitlements](entitlements.md), you may want to retrieve the actual, current customer usage for a given metered usage lever.

=== "JavaScript"

    ``` js
    const leverUsage = await planship.geLeverUsage(
      customer.id, // customer ID
      'usage-lever', // lever slug
    )
    ```

=== "TypeScript"

    ``` ts
    const leverUsage: LeverUsage = await planship.geLeverUsage(
      customer.id, // customer ID
      'usage-lever', // lever slug
    )
    ```

=== "Python"

    ``` py
    lever_usage = planship.get_lever_usage(
        customer.id, # customer ID
        "usage-lever", # lever slug
    )
    ```

=== "Java"

    ``` java
    LeverUsage leverUsage = planship.geLeverUsage(
        customer.getId(), // customer ID
        "usage-lever", // lever slug
    )
    ```

The returned object contains the usage by bucket, by subscription, and total usage:

=== "JavaScript"

    ``` js

    // Example usage for a lever that aggregates usage per bucket
    {
      'total': 5,
      'byBucket': {
        'First project': 3,
        'Second project': 2
      },
      'bySubscription': {
        'c49c142e-310c-44b7-86bd-c4de568bc4ac': [
          {
            'usage': 3,
            'bucket': 'First project'
          }, {
            'usage': 2,
            'bucket': 'Second project'
          }
        ]
      }
    }
    ```

=== "TypeScript"

    ``` ts

    // Example usage for a lever that aggregates usage per bucket
    {
        'total': 5,
        'byBucket': {
          'First project': 3,
          'Second project': 2
        },
        'bySubscription': {
          'c49c142e-310c-44b7-86bd-c4de568bc4ac': [
            {
              'usage': 3,
              'bucket': 'First project'
            }, {
              "usage": 2,
              "bucket": "Second project"
            }
          ]
        }
    }
    ```

=== "Python"

    ``` py

    # Example usage for a lever that aggregates usage per bucket
    {
        "total": 5,
        "by_bucket": {
            "First project": 3,
            "Second project": 2
        },
        "by_subscription": {
            "c49c142e-310c-44b7-86bd-c4de568bc4ac": [
                {
                    "usage": 3,
                    "bucket": "First project"
                }, {
                    "usage": 2,
                    "bucket": "Second project"
                }
            ]
        }
    }
    ```


!!! info
    Depending on the aggregation formula for a given lever, some of the properties of the returned object may be irrelevant. For instance, for a *Total usage* formula, usage-per-bucket will always be the same as total usage, and reported under a single `null` bucket.

    === "JavaScript"

        ``` js
        /// Example usage for a lever that aggregates total usage
        {
          'total': 5,
          'byBucket': {
            'null': 5,
          },
          'bySubscription': {
            'c49c142e-310c-44b7-86bd-c4de568bc4ac': [
              {
                'usage': 5,
                'bucket': null
              }
            ]
          }
        }
        ```

    === "TypeScript"

        ``` ts
        /// Example usage for a lever that aggregates total usage
        {
          'total': 5,
          'byBucket': {
            'null': 5,
          },
          'bySubscription': {
            'c49c142e-310c-44b7-86bd-c4de568bc4ac': [
              {
                'usage': 5,
                'bucket': null
              }
            ]
          }
        }
        ```

    === "Python"

        ``` py
        # Example usage for a lever that aggregates total usage
        {
          "total": 5,
          "by_bucket": {
              "null": 5,
          },
          "by_subscription": {
              "c49c142e-310c-44b7-86bd-c4de568bc4ac": [
                  {
                      "usage": 5,
                      "bucket": null
                  }
              ]
          }
        }
        ```

### Getting usage for multiple levers

If you have multiple levers that track usage for the same *metering ID* (E.g. aggregating it over a different time period), it may be helpful to retrieve usage for the levers all at once.

=== "JavaScript"

    ``` js
    const meteringIdUsage = await planship.getMeteringIdUsage(
      customer.id, // customer ID
      'some-metering-id', // metering ID
    )
    ```

=== "TypeScript"

    ``` ts
    const meteringIdUsage: { [key: string]: LeverUsage}  = await planship.getMeteringIdUsage(
      customer.id, // customer ID
      'some-metering-id', // metering ID
    )
    ```

=== "Python"

    ``` py
    metering_id_usage = planship.get_metering_id_usage(
        customer.id, # customer ID
        "some-metering-id", # metering ID
    )
    ```

=== "Java"

    ``` java
    Object meteringIdUsage = planship.getMeteringIdUsage(
        customer.getId(), // customer ID
        "some-metering-id", // metering ID
    )
    ```

The return value is an object containing usage data for individual levers keyed by their *slugs*.
