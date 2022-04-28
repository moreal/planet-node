planet-node
===========

planet-node is a [.NET] CLI application as example for [Libplanet].
This application was developed as an example of blockchain node configuration using Libplanet, and is not suitable for production environment operation.

[Libplanet]: https://libplanet.io
[.NET]: https://docs.microsoft.com/en-US/dotnet/

Prerequisites
-------------

You need to install [.NET SDK] 6+. Read and follow the instruction to install
 .NET SDK on the [.NET download page][1].

[.NET SDK]: https://docs.microsoft.com/en-US/dotnet/core/sdk
[1]: https://dotnet.microsoft.com/en-us/download


Build
-----

```
dotnet build
```

TODO: Docker build

How to Run
----------

```
dotnet run --project PlanetNode
```

### About configuration
Currently, planet-node produces and uses storage and settings via
`appsettings.json` and `PN_` prefixed environment variables. if you want to
change settings, please edit that files or set environment variables.

```
PN_StorePath="/tmp/planet-node" dotnet run --project PlanetNode
```

### GraphQL
planet-node runs [GraphQL] server and [GraphQL Playground] automatically.
(backed by [GraphQL.NET]) you can check the current chain status on playground. (default endpoint is http://localhost:38080/ui/playground)

The following query is a GraphQL query that returns the last 10 blocks and
transactions.

```graphql
query
{
  blockQuery
  {
    blocks (limit: 10 desc: true)
    {
      index
      hash
      timestamp

      transactions
      {
        id
        actions
        {
          inspection
        }
      }
    }
  }
}
```
![image](https://user-images.githubusercontent.com/128436/165905463-3d9abe81-5642-40ee-820d-6cae3837095d.png)

Also, you can find supported GraphQL query in playground as like bellow.

<img width="478" alt="image" src="https://user-images.githubusercontent.com/128436/165906186-fc361126-f8f8-456a-bd28-fca938e60be1.png">

See the [Libplanet.Explorer] project for more details.

[GraphQL]: https://graphql.org/
[GraphQL Playground]: https://github.com/graphql/graphql-playground
[GraphQL.NET]: https://graphql-dotnet.github.io/
[Libplanet.Explorer]: https://github.com/planetarium/libplanet/tree/main/Libplanet.Explorer