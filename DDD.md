# DOMAIN DRIVEN DESIGN & MICROSERVICES - Notes
How Domain-Driven Design will help us to structure and model our Microservices in terms of granularity, business context, and interface design.
These notes are based on the seminal book "Domain-Driven Design" authored by Eric Evans.

## Strategic Design 

### Context Map
Puts all Bounded Contexts in relation to each other.
The Bounded Context by itself does not deliver an overview of the system.
By introducing a Concept Map we describe the contact between models/contexts.
The Concept Map is also a great starting point for future transformations.

### Bounded Context
Every sophisticated business domain consists of a bunch of Bounded Contexts.
Each Bounded Conext contains models and maybe other contexts
The Bounded Context is also a boundary for the meaning of a given model.

### Shared Kernel Pattern
Two teams share a subset of the domain model including code and maybe the database. The shared kernel is often referred to as the core domain.

### Customer/Supplier Pattern
There is a customer/supplier relationship between the two teams.
The downstream team is considered to be the customer, sometimes with veto rights.

### Conformist Pattern
The downstream team conforms to the model of the upstream team.
There is no translation of models and no vetoing.
If the upstream model is a mess, it propagates to the downstream model.

### Anticorruption Layer Pattern
The anti-corruption layer isolates a client's model from another system's model by translation.

### Separate Ways Pattern
There is no connection between the bounded contexts of a system.
This allows teams to find their solutions in their domain.

### Open/Host Service Pattern
Each Bounded Context offers a defined set of services that expose functionality for other systems. Any downstream system can then implement their integration. This is especially useful for integration requirements with many systems.

### Published Language Pattern
Published Langage is quite similar to Open/Host Service. However, it goes as far as to model a Domain as a common language between bounded contexts.

## Building Blocks
Help to design the internals of Bounded Contexts

### Entities
Entities represent the core business objects of a bounded context's model.
Each Entity has a constant identity and its own lifecycle.

### Value Objects
Value Objects derive their identity from their values.
They do not have their own lifecycle, they inherit it from Entities that are referencing

If an object can be considered an Entity or a Value Object always depends on the Bounded Context it resides in.

### Aggregates
Aggregates group Entities. The Root Entity is the lead in terms of access to the object graph and lifecycle.

### Factories
Entity and AggregatesInstantiations

### Repositories
Encapsulates and represent data access.

### Services
Implements the business logic that relates to multiple entities and aggregates.

## Large Scale Structure
Helps evolving our Microservice landscape.

### Evolving Order
"Let large structures evolve don't overconstrain design principles"
These large structures should be applicable across bounded contexts.
However, there should be some practical constraints.

### Responsibility Layers
Each Microservices is structured according to a bounded context.
In these contexts, developers have the chance to use building blocks.
However, we could structure our bounded context according to responsibilities.

## Destillation
Helps extracting Microservices out of an existing monolithic application.

### Identify the Core Domain

Vision Statement: Defines what is in the core domain and what is not in the core domain.

Destillation Document: Describes all the details of the core domain.

### Extract Subdomains
* Identification of the subdomain
* Extraction from the core
* Clean separation
* Internal refactoring
