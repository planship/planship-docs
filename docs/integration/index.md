# Code integration

Once you define your Planship levers ([feature](/concepts/feature-levers) and/or [metered](/concepts/metered-levers)) and [plans](/concepts/plans), it's time to integrate your product with the [Planship API](/main-api/reference) to do the following:

 1. [Register your customers](customers)
 2. [Manage their subscriptions](subscriptions)
 3. [Retrieve their entitlements](entitlements)
 4. [Report metered usage](usage)

## Authentication and security

The Planship API uses token-based authentication where access tokens are obtained via an [OAuth2 Client Credentials flow](https://oauth.net/2/grant-types/client-credentials/). The credentials consist of a client ID and secret pair that is exchanged for a token that grants access to the resources within an organization. Client ID and secret pairs are managed on the [organization](/concepts/products#organizations) level by organization admins and collaborators. You can find them in the Planship console under your organization.

!!!info
    Since Planship API calls are authenticated by tokens rather than API keys, Planship can be securly integrated into your client-side code (E.g. browser) without compromising application secrets.

## Getting started with Planship SDKs

To get started, add a Planship SDK to your project. There are SDKs for JavaScript, Python, and Java, with more languages in the works. [Let us know if there's something you'd like to see](mailto:connect@planship.io).

!!!tip
    If the language or platform you use isn't currently supported by any of our SDKs, or you would rather build your own library, you can generate a Planship API client from our [OpenAPI spec](https://api.planship.io/openapi.json) using a generator like [openapi-generator](https://github.com/OpenAPITools/openapi-generator/tree/master).

=== "JavaScript Fetch"

    Using `pnpm`:
    ``` console
    pnpm install @planship/fetch
    ```

    Using `yarn`:
    ``` console
    yarn add @planship/fetch
    ```

=== "JavaScript Axios"

    Using `pnpm`:
    ``` console
    pnpm install @planship/axios
    ```

    Using `yarn`:
    ``` console
    yarn add @planship/axios
    ```

=== "Python"

    ``` console
    pip install planship
    ```

=== "Java"

    **Maven users**

    Add this dependency to your project's POM:

    ```xml
    <dependency>
      <groupId>org.planship</groupId>
      <artifactId>planship-java</artifactId>
      <version>0.1.0</version>
      <scope>compile</scope>
    </dependency>
    ```

    **Gradle users**

    Add this dependency to your project's build file:

    ```groovy
      repositories {
        mavenCentral()     // Needed if the 'planship-java' jar has been published to maven central.
        mavenLocal()       // Needed if the 'planship-java' jar has been published to the local maven repo.
      }

      dependencies {
        implementation "org.planship:planship-java:0.1.0"
      }
    ```

Then, import and initialize the client:

=== "JavaScript Fetch"

    ``` js
    import { Planship } from '@planship/fetch'

    const planship = new Planship(
        'clicker', // your Planship product slug
        'https://api.planship.io', // Planship API endpoint URL
        '273N1SQ3GQFZ8JSFKIOK', // Planship API client ID
        'GDSfzPD2NEM5PEzIl1JoXFRJNZm3uAhX' // Planship API client secret
    )
    ```

    **Client-side (browser) code**

    In client code, **the use of application secrets like your Planship API client secret should be avoided at all times**. Instead, you should retrieve a Planship access token from the server using your existing application API, and pass the token to the Planship client class constructor via an asynchronous getter function.

    ``` js
    const planship = new Planship(
        'clicker', // your Planship product slug
        'https://api.planship.io', // Planship API endpoint URL
        getAccessToken // function that returns a Promise that resolves with a valid Planship access token
    )
    ```

    To obtain the token on the server side, call the `getAccessToken` method on the server-side Planship client instance:

    ``` js
    const accessToken = await planship.getAccessToken()
    ```

=== "JavaScript Axios"

    ``` js
    import { Planship } from '@planship/axios'

    const planship = new Planship(
        'clicker', // your Planship product slug
        'https://api.planship.io', // Planship API endpoint URL
        '273N1SQ3GQFZ8JSFKIOK', // Planship API client ID
        'GDSfzPD2NEM5PEzIl1JoXFRJNZm3uAhX' // Planship API client secret
    )
    ```

    **Client-side (browser) code**

    In client code, **the use of application secrets like your Planship API client secret should be avoided at all times**. Instead, you should retrieve a Planship access token from the server using your existing application API, and pass the token to the Planship client class constructor via an asynchronous getter function.

    ``` js
    const planship = new Planship(
        'clicker', // your Planship product slug
        'https://api.planship.io', // Planship API endpoint URL
        getAccessToken // function that returns a Promise that resolves with a valid Planship access token
    )
    ```

    To obtain the token on the server side, call the `getAccessToken` method on the server-side Planship client instance:

    ``` js
    const accessToken = await planship.getAccessToken()
    ```

=== "Python"

    ``` py
    from planship import Planship

    planship = Planship(
        "clicker", # your Planship product slug
        "https://api.planship.io", # Planship API endpoint URL
        "273N1SQ3GQFZ8JSFKIOK", # Planship API client ID
        "GDSfzPD2NEM5PEzIl1JoXFRJNZm3uAhX" # Planship API client secret
    )
    ```

=== "Java"

    ``` java
    import org.planship;

    Planship planship = new Planship(
        "clicker", // your Planship product slug
        "https://api.planship.io", // Planship API endpoint URL
        "273N1SQ3GQFZ8JSFKIOK", //Planship API client ID
        "GDSfzPD2NEM5PEzIl1JoXFRJNZm3uAhX" // Planship API client secret
    )
    ```
