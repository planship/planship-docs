# Getting started

## Step 1: Define your product plans, levers, and entitlements

To get started, sign into the [Planship Console](https://app.planship.io/auth/sign-in). If you don't have a Planship account yet, [sign up](https://app.planship.io/auth/sign-up) now.

In the console, you'll do the following:

- Create a [product](/concepts/products) that corresponds to your software product
- Create [feature](/concepts/feature-levers) and/or [metered](/concepts/metered-levers) levers that map to the pricing dimensions of your product.
- Create [plans](/concepts/plans) that map to your recurring subscription plans, one-off packages, add-ons, etc.
- Apply pricing levers to individual plans by defining [entitlements](/concepts/plans/#entitlements).

!!!tip "Want guidance?"
    If you're new to Planship, you can follow our [Planship Console walkthrough HOWTO guide](/howtos/console-step-by-step) for a step-by-step guide on creating products, plans, levers, and entitlements.

<figure markdown="span">
  ![Plans view of the Planship app showing a list of plans along with the details of the selected plan named 'Personal'](/assets/screenshots/23-plans-view.png){ width="600" }
  <figcaption>Defining plans and entitlements in the Planship Console</figcaption>
</figure>

## Step 2: Integrate Planship into your product code

With your levers, plans, and entitlements defined in Planship, it's time to integrate your product with the [Planship API](/main-api/reference) to do the following:

- [Register your customers](customers)
- [Manage their subscriptions](subscriptions)
- [Retrieve their entitlements](entitlements)
- [Report metered usage](usage)


### Languages and frameworks

Planship offers API client libraries for a number of languages including JavaScript/TypeScript, Python, and Java. In addition to langauage-specific libraries, Planship offers SDKs that streamline integration with popular application-developement libraries and frameworks, including [React](https://react.dev/) (and [Next.js](https://nextjs.org/)) as well as [Vue.js](https://vuejs.org/) (and [Nuxt](https://nuxt.com/)).

[Let us know if there's a language or framework you'd like for us to officially support](mailto:connect@planship.io).

!!!tip
    If the language or framework you use isn't currently supported by one of our SDKs, or you would rather build your own library, you can generate a Planship API client from our [OpenAPI spec](https://api.planship.io/openapi.json) using a generator like [openapi-generator](https://github.com/OpenAPITools/openapi-generator/tree/master).


### Choosing the right SDK for your project

The Planship SDKs you use depend on the languages and frameworks in your application's tech stack. Regardless of whether you are fetching and enforcing entitlements or managing customers and their subscriptions, you will likely need to call the Planship API from both the backend and frontend of your application.

#### Backend integration

For backend integration, use one of the Planship language libraries:

- **Node.js**: Use [@planship/fetch](https://www.npmjs.com/package/@planship/fetch) or [@planship/axios](https://www.npmjs.com/package/@planship/axios) for backends built with frameworks like [Express.js](https://expressjs.com/) and [NestJS](https://nestjs.com/).
- **Python**: Use [planship-python](https://pypi.org/project/planship/) for backends built with frameworks like [Flask](https://flask.palletsprojects.com/en/3.0.x/), [Django](https://www.django-rest-framework.org/), and [FastAPI](https://fastapi.tiangolo.com/).
- **Java**: Use [planship-java](https://mvnrepository.com/artifact/io.planship/planship-java) for backends built with frameworks like [Spring](https://spring.io/projects/spring-framework).


#### Frontend integration

Planship offers SDKs designed specifically for some of the most populars web frameworks:

- **React** SPA apps: Use [@planship/react](https://www.npmjs.com/package/@planship/react), which uses the [React Context API](https://react.dev/learn/passing-data-deeply-with-context) to expose Planship API clients and entitlements via React hooks.
- **Next.js** apps including SSR apps: Use [@planship/react](https://www.npmjs.com/package/@planship/react) for frontend operations and [@planship/fetch](https://www.npmjs.com/package/@planship/fetch) for server-side operations.
- **Vue.js** SPA apps: Use [@planship/vue](https://www.npmjs.com/package/@planship/vue).
- **Nuxt** apps including universal (server-side + client-side) apps: Use [@planship/nuxt](https://www.npmjs.com/package/@planship/nuxt), which includes [@planship/vue](https://www.npmjs.com/package/@planship/vue) and its composables along with server-side services for calling the Planship API from Nuxt [server routes](https://nuxt.com/docs/guide/directory-structure/server#server-routes), [server middleware](https://nuxt.com/docs/guide/directory-structure/server#server-middleware), and more.

If the frontend framework that you use doesn't have a dedicated Planship SDK yet, you can grab [@planship/fetch](https://www.npmjs.com/package/@planship/fetch) or [@planship/axios](https://www.npmjs.com/package/@planship/axios) and use them from your client-side and server-side code.


### Authentication and security

The Planship API uses token-based authentication where access tokens are obtained via an [OAuth2 Client Credentials flow](https://oauth.net/2/grant-types/client-credentials/). The credentials consist of a client ID and secret pair that is exchanged for a token that grants access to the resources within an organization. Client ID and secret pairs are managed on the [organization](/concepts/products#organizations) level by organization admins and collaborators. You can find them in the Planship console under your organization.

<figure markdown="span">
  ![Organization view of the Planship app showing a list of products and credentials](/assets/screenshots/24-org-credentials.png){ width="600" }
  <figcaption>Managing products and credentials</figcaption>
</figure>

!!!info
    Since Planship API calls are authenticated by tokens rather than API keys, Planship can be securly integrated into your client-side code (E.g. browser) without compromising application secrets.

### Getting started with Planship SDKs

To get started, add the desired Planship library or SDK to your project.

=== "JavaScript Fetch"

    The Planship [fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) client is part of the planship-js SDK codebase hosted at <https://github.com/planship/planship-js> and published to NPM as [@planship/fetch](https://www.npmjs.com/package/@planship/fetch).

    Using `pnpm`:
    ``` console
    pnpm install @planship/fetch
    ```

    Using `yarn`:
    ``` console
    yarn add @planship/fetch
    ```

=== "JavaScript Axios"

    The Planship [Axios](https://github.com/axios/axios) client is part of the planship-js SDK codebase hosted at <https://github.com/planship/planship-js> and published to NPM as [@planship/fetch](https://www.npmjs.com/package/@planship/axios).

    Using `pnpm`:
    ``` console
    pnpm install @planship/axios
    ```

    Using `yarn`:
    ``` console
    yarn add @planship/axios
    ```

=== "Python"

    The Planship Python SDK code is hosted at <https://github.com/planship/planship-python> and published to PyPi at <https://pypi.org/project/planship/>.

    ``` console
    pip install planship
    ```

=== "Java"

    The Planship Java SDK code is hosted at <https://github.com/planship/planship-java> and available from Maven Central at <https://pypi.org/project/planship/>.

    **Maven users**

    Add this dependency to your project's POM:

    ```xml
    <dependency>
      <groupId>io.planship</groupId>
      <artifactId>planship-java</artifactId>
      <version>0.2.0</version>
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

=== "React"

    The Planship client-side SDK for React uses the [React Context API](https://react.dev/learn/passing-data-deeply-with-context) to make consuming Planship data and functionality in [React](https://react.dev) and [Next.js](https://nextjs.org/) apps easier.
    The React SDK code is hosted at <https://github.com/planship/planship-react> and published to NPM as [@planship/react](https://www.npmjs.com/package/@planship/react).

    Using `pnpm`:
    ``` console
    pnpm install @planship/react
    ```

    Using `yarn`:
    ``` console
    yarn add @planship/react
    ```

Then, import and initialize it:

=== "JavaScript Fetch"

    ``` js
    import { Planship } from '@planship/fetch'

    const planship = new Planship(
      'clicker-demo', // your Planship product slug
      {
        clientId: '273N1SQ3GQFZ8JSFKIOK', // Planship API client ID
        clientSecret: 'GDSfzPD2NEM5PEzIl1JoXFRJNZm3uAhX' // Planship API client secret
      }
    )
    ```

    **Client-side (browser) code**

    In client code, **the use of application secrets like your Planship API client secret should be avoided at all times**. Instead, you should retrieve a Planship access token from the server using your existing application API, and pass the token to the Planship client class constructor via an asynchronous getter function.

    ``` js
    const planship = new Planship(
      'clicker-demo', // your Planship product slug
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
      'clicker-demo',   // your Planship product slug
      {
        clientId: '273N1SQ3GQFZ8JSFKIOK', // Planship API client ID
        clientSecret: 'GDSfzPD2NEM5PEzIl1JoXFRJNZm3uAhX' // Planship API client secret
      }
    )
    ```

    **Client-side (browser) code**

    In client code, **the use of application secrets like your Planship API client secret should be avoided at all times**. Instead, you should retrieve a Planship access token from the server using your existing application API, and pass the token to the Planship client class constructor via an asynchronous getter function.

    ``` js
    const planship = new Planship(
      'clicker-demo', // your Planship product slug
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
        "clicker-demo", # your Planship product slug
        "https://api.planship.io", # Planship API endpoint URL
        "273N1SQ3GQFZ8JSFKIOK", # Planship API client ID
        "GDSfzPD2NEM5PEzIl1JoXFRJNZm3uAhX" # Planship API client secret
    )
    ```

=== "Java"

    ``` java
    import io.planship;

    Planship planship = new Planship(
        "clicker-demo", // your Planship product slug
        "https://api.planship.io", // Planship API endpoint URL
        "273N1SQ3GQFZ8JSFKIOK", //Planship API client ID
        "GDSfzPD2NEM5PEzIl1JoXFRJNZm3uAhX" // Planship API client secret
    )
    ```


=== "React"

    Import and call `withPlanshipProvider` to create a Planship context provider and wrap your components with it.

    ``` js
    import { withPlanshipProvider } from '@planship/react'

    function App() {
      const PlanshipProvider = withPlanshipProvider(
        {
          slug: 'clicker-demo', // your Planship product slug
          getAccessToken: getAccessToken, // function that returns a valid Planship token
        }
      )

      return (
        <PlanshipProvider>
          <Page />
        </PlanshipProvider>
      )
    }
    ```

    Then, import and call `usePlanship` inside your components to access the Planship API client.

    ```js
    import { usePlanship } from '@planship/react'

    export default function YourComponent({ children }) {
      const { planship } = usePlanship()

      useEffect(() => {
        // use planship API instance to call the Planship API
      }, [])

      return (
        // Render your component using data retrieved from the Planship API
      )
    }
    ```
