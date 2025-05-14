# Standard Messaging

An open source API standard for integrating with messaging platforms in a platform-agnostic way.

## Introduction

Many application developers wish to make use of messaging solutions such as RabbitMQ, Azure Service Bus, Amazon SQS, etc., but don't want to be locked into any one solution.  The purpose of this repo is to support the development of a standard API that developers can use to add messaging to their applications without needing to decide ahead of time which messaging infrastructure they are going to use.

For those coming from the .NET world, the ambition is to define something like the `ILogger` interface in `Microsoft.Extensions.Logging`.  This interface is supported natively by .NET through libraries such as `Microsoft.Extensions.Logging.Console` but it is also supported by open-source solutions like `Serilog`, `Log4net` and `NLog`, as well as many commercial immplementations.

Whilst the example given is from the .NET world, there seems no reason why the approach can't be applied to languages other than C#, as long as those languages support interface definitions.  As the initial authors primarily come from a C#/.NET background, the initial focus is on the C# language binding, but contributions for other language bindings are encouraged.

## Ambition

The ambition of this project is deliver an API that can be used with a wide range of messaging platforms.  But in isolation, this would be just an academic exercise.  So, the project aims to deliver sample code showing how to implement the API's features across a number of messaging platforms.  The intention is not to deliver concrete solutions (there will be no Nuget packages or equivalents) but to encourage the open source community to deliver and support implementations for individual (or multiple) platforms.  (To use a .NET analogy, similar to the way PostgreSQL is supported in EF Core.)

One inevitable danger of such an abstraction exercise is that it becomes "lowest common denominator", with the value-add of individual platforms being lost. However, this is almost part of the ambition; to provide a basic messaging API that can be used for inter-process/inter-service communication, without being concerned about platform specifics.  Where developers require access to platform-specific features, then direct use of the relevant platform APIs is likely more appropriate.

## Charter

The intention is that all work documented here will be published under the MIT licence.  As such, contributions and feedback are encouraged by all comers, subject to that constraint.

As far as possible, decisions will be taken on a consultative, collaborative basis by participants and contributors.  However, it would seem that most successful open-source projects (ones that are not commercially driven) operate best using a Benevolent Dictator for Life (BDFL) model, at least until they well established, mainly to avoid potential deadlock between competing approaches.  As creator of this project, I (@stevecwilkinson) hold that role for now; as such, I commit to acting in the best interests of the wider community and not to be a complete (*insert your favourite derogatory term here*).

## Inspiration

Inspiration has been taken from a number of sources, including:

- [Standard Webhooks](https://github.com/standard-webhooks/standard-webhooks)
- [Open Telemetry](https://opentelemetry.io/)
- [`Microsoft.Extensions.Logging`](https://learn.microsoft.com/en-us/dotnet/api/microsoft.extensions.logging)
- [Foundatio](https://github.com/FoundatioFx/Foundatio?tab=readme-ov-file#messaging)

## Additional Background

This work was triggered by two main events.  The first was [Microsoft's announcement in January 2024](https://github.com/dotnet/aspnetcore/issues/53219) that it was considering adding an "eventing framework" to .NET 9; it was subsequently dropped from .NET 9 followed by @davidfowl confirming that [there is no eventing framework coming in .NET 10](https://github.com/dotnet/aspnetcore/issues/53219#issuecomment-2789937139).  (It's worth mentioning that Microsoft clarified the focus of this issue was very much on Azure Webjobs and Azure Functions, and not on the broader issue of messaging.)

The second trigger for this work was the decision by the authors of [MassTransit](https://masstransit.io/) to move to a commercial basis, with licence fees that are in most cases beyond the means of the smaller development outfits.  If it wasn't for this transition, as MassTransit provides an excellent abstraction to messaging platforms, it is unlikely this project would have been established.