<details open>
    <summary style="font-size: 16px; font-weight: bold; cursor: pointer;">
        Table of Contents
    </summary>
  
  [[_TOC_]]
</details>

## 📝 Changelog

<br>

| Author                            | Modification Date       | Changes                                       |
|-----------------------------------|-------------------------|-----------------------------------------------|
|                 | 25/02/2025              | First Version Created                         |

<br>

---

We may find sometimes that CNAPPs do not offer some feature that we need for a requisite we may have.

For example, we might want to create:

- Specific type of **report** that contains specific information
- Create some type **automation** that leverages all data provided by CNAPPs, like autoremediation of alerts or sending emails to stakeholders based on some advanced criteria
- Create a **dashboard** with PowerBI
- Any other functionality. Here your imagination is the limit

But for creating any of these, we need data. (It's no coincidence that Google, Meta, Amazon, and others love collecting as much data from us as they can.) This is where APIs come into play.

APIs allow us to communicate with CNAPPs and obtain, download and process all data they have available (As long as they have created an API endpoint that allows for downloading all data. This is not always the case).

Prisma Cloud and Wiz use different types of APIs, so we will need to learn both in order to create automations that can integrate both data streams.

## Understading APIs

For understanding how to use and manage APIs, we will start using an IDE to make petitions. There are several options available.

Postman is the least recommended because it needs an account. Hoppscotch is a web based editor and Yaak is the best offline editor.

1. [Hoppscotch (Online)](https://hoppscotch.io/)
2. [Yaak (Best Offline Editor)](https://github.com/mountain-loop/yaak)
3. [Postman (Requires creating account)](https://www.postman.com/downloads/)

Please, install any of the above options since we will use them going forward in this lesson.

## REST (Prisma Cloud)

We will start by learning how the Prisma Cloud API works, as it is easier to understand and use than Wiz's. Prisma Cloud uses a REST API. Rest APIs lets clients and servers communicate over HTTP using predictable, resource-based URLs. It’s lightweight, stateless, and widely used for web services. This is the type of API used in Prisma Cloud.

In rest API, each request is independent, the server does not remember past interactions. Also, everyting (users, files, alerts) is a resource with a unique URL. To determine what URL to query to obtain some resource, we use the [API documentation](https://pan.dev/prisma-cloud/api/).

This documentation contains all resources available, the HTTP methods required and parameters or body options that are accepted for each URL.

Let's review what data is available for one request from the documentation. All requests are organized by security contexts, like cloud security, application security or runtime security. Each group contains all petitions organized by resources, like access keys, or alerts. The following image shows the petition **List Alerts V2 - Post** from the **Alerts** resource group, inside the **Cloud Security** context. The first useful information that we obtain from the petition documentation is the HTTP method used and the URL.

<div style="text-align: center; width: 600px; margin: auto;">
    <img src="https://imgur.com/joIgoSU.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="GraphQL Logo">
    <div style="color: gray; font-size: small; font-style: italic;">Resource prototype in the Prisma API documentation</div>
</div>

All URLs that are displayed in the documentation will not work out of the box. This is because Prisma Cloud does not provide an unified endpoint or the same endpoints for all its clients. This is why, before creating any petition, we must modify the URL and include our tennant URL to the petition URL that appears in the documentation.

For doing this we must first identify what part of the URL corresponds to the tennant and which part corresponds to the resource. We can, therefore, identify three different sections in any URL in the context of API calls:

- Prisma Tennant selector
- Resource selector
- Petition parameters

For the petition URL in the screenshot:

`https://api.prismacloud.io/v2/alert`

- Prisma Tennant selector: `api.prismacloud.io`. This is the part of the URL we need to modify and include our tennant endpoint.
- Resource selector: `/v2/alert`
- Petition parameters: This part of the URL will never appear included in the petition URL. Its used to modify what data is returned by the server and always starts by the character `?`. One example URL where petition parameters are used: `https://api.prismacloud.io/v2/alert?detailed=true`. The petition parameters part of the URL is: `?detailed=true`

Now, to modify the Prisma Tennant selector part of the URL, we need to know what is our endpoint. For this, enter your Prisma Cloud web console and memorize the URL. Then, enter this [link](https://pan.dev/prisma-cloud/api/cspm/api-urls/) or use the following image to identify in the first column of table, the URL that you memorized. Your API URL or Prisma Tennant selector will be at the same row as the value you found in the first column.

<div style="text-align: center; width: 600px; margin: auto;">
    <img src="https://imgur.com/jkdPP9e.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="GraphQL Logo">
    <div style="color: gray; font-size: small; font-style: italic;">Table of equivalencies for API endpoints</div>
</div>

Now, lets try to make the API call with the modified URL:

`https://<INSERT HERE YOUR API URL>/v2/alert`

<div style="text-align: center; width: 600px; margin: auto;">
    <img src="https://imgur.com/SKXuWjR.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="GraphQL Logo">
    <div style="color: gray; font-size: small; font-style: italic;">We get an 401 unauthorized error</div>
</div>

We are getting this error because this API is private and requires the use of credentials, specifically a token. Lets do that first:

Using the following [login](https://pan.dev/prisma-cloud/api/cspm/app-login/) API endpoint, we can obtain a token that we will use to call all other endpoints in the CSPM module. Other modules may need other login endpoints, and therefore, another token.

The CSPM login endpoint `https://<INSERT HERE YOUR API URL>/login` requires passing a username and password (Access key) in the body of the petition to obtain the token. These values need to be created from the web console.

To create the access key, in the web console, go to Settings > Access Control. Access keys can be associated with a **user** or a **service account**.

![text](https://imgur.com/ZnWx1wH.png)

A **service account** in Prisma Cloud is a special identity designed for programmatic access via API, whereas a **user** represents a real person. Both identity types are assigned a role, which defines their access scope.

Access in Prisma Cloud is governed by **permission groups**—collections of rules that determine what actions an identity can perform. These permission groups are created independently of roles and can be reused across different roles.

For our example, we will create a service account, with it's own role. This role will be associated with a built-in [permission group](https://docs.prismacloud.io/en/enterprise-edition/content-collections/administration/prisma-cloud-administrator-roles). We only want read permissions for this Access key, so we will use the *Account Group read only* permission group.

Click on the add button and create a new role:

<div style="text-align: center; width: 600px; margin: auto;">
    <img src="https://imgur.com/MzAVp37.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;">
    <div style="color: gray; font-size: small; font-style: italic;">The most important setting here is the "Account group" option</div>
</div>

Now, click again the add button and create a new service account:

<div style="text-align: center; width: 600px; margin: auto;">
    <img src="https://imgur.com/Nn1zz2W.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;">
    <div style="color: gray; font-size: small; font-style: italic;">Select the role we created previously</div>
</div>

Create the access key and store the secrets in a password manager like [KeepassXC](https://keepassxc.org/) or [Bitwarden](https://bitwarden.com/es-la/):

<div style="text-align: center; width: 600px; margin: auto;">
    <img src="https://imgur.com/t1MM8fF.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;">
    <div style="color: gray; font-size: small; font-style: italic;">It is recomended to enable an expiration date</div>
</div>

<div style="text-align: center; width: 600px; margin: auto;">
    <img src="https://imgur.com/7yy12xf.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;">
    <div style="color: gray; font-size: small; font-style: italic;">Copy both values in a secret manager before closing the pop-up</div>
</div>

Now that we have the access key, we can finally call the API login endpoint. In the body of the request, use the keys username and password. Username corresponds to "Access key ID" and password corresponds to "Secret Access Key".

<div style="text-align: center; width: 600px; margin: auto;">
    <img src="https://imgur.com/byz73ze.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;">
    <div style="color: gray; font-size: small; font-style: italic;">We get a token</div>
</div>

Use the token to call any CSPM endpoints including the "x-redlock-auth" key and the value of the token we received previously.

<div style="text-align: center; width: 600px; margin: auto;">
    <img src="https://imgur.com/8Sjrc8l.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;">
    <div style="color: gray; font-size: small; font-style: italic;">Now, the request is working </div>
</div>

<div style="text-align: center; width: 600px; margin: auto;">
    <img src="https://imgur.com/wromMyx.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;">
    <div style="color: gray; font-size: small; font-style: italic;">The token will expire after some time </div>
</div>

Certain API endpoints, such as the Runtime Security endpoints, require a different login and authentication token than those used previously. To access these endpoints, use the following login method: [Login CWPP](https://pan.dev/prisma-cloud/api/cwpp/post-authenticate/)

## GraphQL (Wiz)

You're developing an app, and you need some data from a server. You want just a small slice of information—no extra fluff, no unnecessary API calls. What do you do? Enter GraphQL, a query language that lets you shape your data the way you need it, no more, no less.

This lesson will take you through GraphQL’s power and flexibility using examples from the Star Wars API and some general tips and tricks that apply to any GraphQL server. Let’s dive into the power of precise queries, real-time data, and easy-to-understand schemas.

<div style="text-align: center; width: 200px; margin: auto;">
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/17/GraphQL_Logo.svg/1024px-GraphQL_Logo.svg.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="GraphQL Logo">
    <div style="color: gray; font-size: small; font-style: italic;">GraphQL Logo</div>
</div>

### Why graphql?

Features:

- Single Endpoint URL
- Flexible Response Structure: Returns data in a structure defined by the client.
- Solves Overfetching & Underfetching: Prevents retrieving more or less data than needed, a common issue in REST APIs.
- Reduces Data Post-Processing: Allows combining multiple calls to streamline workflows.
- JSON Output Only: Does not support CSV format.
- Steeper Learning Curve: More complex to learn compared to a REST API.

### Getting Started: GraphiQL Playground

GraphiQL is like your sandbox for experimenting with GraphQL queries. It's a great way to start learning and see immediate results. Head over to the [Star Wars GraphQL Playground](https://community.postman.com/t/how-to-run-a-request-multiple-times/10476), where you can explore the Star Wars universe through GraphQL.

Once you’re in the playground, you’ll notice two panels:

- Left side: Where you write your queries.
- Right side: Where you see the documentation for the GraphQL schema, including all types, fields, and arguments you can use.

### The First Queries

Imagine you’re creating a Star Wars movie app. You’re starting small: a homepage that shows a list of Star Wars films. If you’ve used REST APIs before, you know this usually means calling a URL like /films, getting back a large payload, and then digging through it to extract what you want. Often, you’ll end up with extra data you don’t need.

GraphQL flips that idea around. You describe exactly what you want from the server—and nothing more. That’s because GraphQL is a query language for APIs that lets the client shape the response.

Let’s begin with a basic query that asks for film titles:

```graphql
{
  allFilms {
    films {
      title
    }
  }
}
```

#### 🧰 What is happening here?

In GraphQL, every query starts from something called a root type. These root types define the available entry points into the API. There are three standard root types:

- Query: for reading data (like asking for films or people)
- Mutation: for writing or modifying data
- Subscription: for real-time data streams

In the Star Wars API, we're working with queries. The Query root type defines fields you can start your queries with. These fields are called entry points.

In this query, allFilms is an entry point defined on the Query root type. It's like the front door into film data.

From allFilms, you access the films field, which is a list of film objects. Then, you ask each film to give you its title.

#### 📚 Why this matters

GraphQL gives you predictable, shaped responses. If you only need a title, ask for only the title. That means less data transferred, faster performance, and cleaner code on the client.

Let’s now expand the request to get more details about each film:

```graphql
{
  allFilms {
    films {
      title
      director
      releaseDate
    }
  }
}
```

Each additional field you add deepens the structure of the response. You’re shaping your data exactly how your UI wants it. This is one of the major benefits of GraphQL over REST.

Want to know what other entry points are available in the Star Wars API? Use this query:

```graphql
{
  __schema {
    queryType {
      fields {
        name
      }
    }
  }
}
```

This will return all the query entry points like allFilms, allPeople, film, person, allPlanets, etc. Each one is a doorway into the data graph.

The query returns the following entry points:

```graphql
{
  "data": {
    "__schema": {
      "queryType": {
        "fields": [
          {
            "name": "allFilms"
          },
          {
            "name": "film"
          },
          {
            "name": "allPeople"
          },
          {
            "name": "person"
          },
          {
            "name": "allPlanets"
          },
          {
            "name": "planet"
          },
          {
            "name": "allSpecies"
          },
          {
            "name": "species"
          },
          {
            "name": "allStarships"
          },
          {
            "name": "starship"
          },
          {
            "name": "allVehicles"
          },
          {
            "name": "vehicle"
          },
          {
            "name": "node"
          }
        ]
      }
    }
  }
}
```

### Following Relationships

Now your app shows films. But users love characters. Let’s start showing those too.

We’ll begin by asking for all characters and their basic info:

```graphql
{
  allPeople {
    people {
      name
      birthYear
    }
  }
}
```

Here, allPeople is another root field available on the Query type. It gives us a paginated list of people. Under people, we request specific fields for each person: name and birthYear.

Characters in the Star Wars universe have relationships, like a home planet. In REST, you'd need to make a second request to fetch planet info. In GraphQL, you just follow the relationship:

```grapql
{
  allPeople {
    people {
      name
      homeworld {
        name
        climate
      }
    }
  }
}
```

This works because each Person type has a homeworld field that links to a Planet type. You can query that type in place, pulling out nested information. This pattern is what gives GraphQL its name: it's a graph of types connected to each other, and you traverse it with your query.

### Zooming In with IDs and Reusing Structures

Sometimes you don’t want the whole list. Suppose a user clicks on a specific character—Luke Skywalker. You want just Luke's data.

You can use the person root field with an id argument:

```grapql
{
  person(id: "cGVvcGxlOjE=") {
    name
    eyeColor
    birthYear
    homeworld {
      name
    }
  }
}
```

This tells GraphQL: "Give me the person with that ID, and here are the fields I want from them." In the Star Wars API, all IDs are base64 encoded. You'll usually get these IDs from a previous query, like allPeople.

This pattern is helpful for detail views, where you're loading content dynamically based on a unique identifier.

Now imagine you're using the same character fields in multiple queries. Instead of repeating yourself, GraphQL gives you fragments.

```grapql
fragment CharacterDetails on Person {
  name
  birthYear
  gender
  eyeColor
}

{
  allPeople {
    people {
      ...CharacterDetails
    }
  }
}
```

Fragments are like reusable templates. You define a fragment once and include it wherever you need that same structure. If the structure changes, you update it in one place.

### Parallel Queries and Schema Introspection

Sometimes you need to fetch multiple things at once. For example, let’s get both Luke and Leia in the same query. But both use the same field: person.

To avoid naming collisions in the response, use aliases:

```grapql
{
  luke: person(id: "cGVvcGxlOjE=") {
    name
    birthYear
  }
  leia: person(id: "cGVvcGxlOjI=") {
    name
    birthYear
  }
}
```

Now you get a response with luke and leia as separate top-level keys.

But how do you know what’s even possible to query? GraphQL has built-in introspection, which allows you to ask the API about itself.

```grapql
{
  __schema {
    types {
      name
      fields {
        name
      }
    }
  }
}
```

This gives you a list of all types and their fields. It's like asking the API for its own documentation. Tools like GraphiQL use this under the hood to show docs and autocomplete.

You can even dig deeper to explore a specific type:

```grapql
{
  __type(name: "Film") {
    name
    fields {
      name
      type {
        name
      }
    }
  }
}
```

This lets you discover the full structure of types like Film, Person, or Planet so you can plan better queries.

### Endpoints, Authorization, and Real-World Considerations

So far, we’ve focused on what GraphQL lets you ask. But to build real-world apps, you also need to understand where and how to ask—and what kinds of doors might be locked until you have the key.

Let’s step back and talk about the machinery behind a GraphQL API. This chapter explores important topics like endpoints, tokens, and how your queries stay safe and organized.

#### The GraphQL Endpoint

Unlike REST APIs (where each resource usually has its own URL like /films or /people), GraphQL has a single endpoint—typically something like:

`https://api.example.com/graphql`

That’s it. One URL.

From there, all queries, mutations, and subscriptions go through the same door. This single endpoint acts like a universal interpreter. It reads your query and figures out what parts of the data graph you’re trying to reach.

👉 In the Star Wars API, the endpoint is available here, although it's provided as a demo interface, not a production API. If you were calling it from code, you'd use a GraphQL client (like Apollo or Relay) to send queries to that endpoint.

#### Authentication and Authorization

Just like in the Star Wars universe, not everyone gets to access the Jedi Archives. Real-world APIs often have sensitive data or operations that are restricted to certain users.

This is where authentication and authorization come in.

- Authentication answers: Who are you?
- Authorization answers: What are you allowed to do?

Most GraphQL APIs use Bearer tokens, sent in the HTTP headers. These tokens are usually issued after a login or OAuth process. Here's what it looks like when you send a query from a tool like curl or Postman:

```http
POST /graphql HTTP/1.1
Host: api.example.com
Authorization: Bearer YOUR_TOKEN_HERE
Content-Type: application/json

{
  "query": "{ me { name email } }"
}
```

If the token is valid, the server processes the query. If not, it may return an error or empty result.

Even with a token, you might not be allowed to access every field. The GraphQL server might enforce permissions like:

- Only admins can run certain mutations
- Users can only read their own profiles
- Sensitive data like payment info is locked down

In code, this is often enforced through resolvers—the server-side functions that handle each field. These can check permissions before resolving data.

#### Versioning: Why GraphQL Doesn’t Need /v1, /v2, etc.

In REST, you often see APIs versioned like /api/v1/users. That’s because changing one endpoint can break clients.

GraphQL is different. Clients only ask for the fields they need. So if the server adds new fields (or even new entry points), existing queries keep working as long as their fields stay valid.

This means GraphQL evolves more smoothly, and you don’t need to maintain as many versioned endpoints.

### API Explorer

Wiz provides an API Explorer, included in the web interface, that allows users to create queries easily. The API Explorer is an integrated IDE.

It is useful for creating new queries or exploring available data, as it offers:

- Auto-completion of attributes
- Integrated documentation
- Call history
- Code snippets

<div style="text-align: center; width: 600px; margin: auto;">
    <img src="https://imgur.com/SsMIjaa.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="GraphQL Logo">
    <div style="color: gray; font-size: small; font-style: italic;">GraphQL Logo</div>
</div>

### API Console

This tool logs all API calls made by the Wiz's web frontend.

It is useful for identifying values displayed on the web and to easily find what API call retreives that information.

The API Console displays both the web API call and its response.

<div style="text-align: center; width: 600px; margin: auto;">
    <img src="https://imgur.com/dajxiE3.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="GraphQL Logo">
    <div style="color: gray; font-size: small; font-style: italic;">GraphQL Logo</div>
</div>

## cURL

[Tutorial](https://curl.se/docs/tutorial.html)