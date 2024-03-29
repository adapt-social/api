**About arc42**

arc42, the template for documentation of software and system
architecture.

Template Version 8.2 EN. (based upon AsciiDoc version), January 2023

Created, maintained and © by Dr. Peter Hruschka, Dr. Gernot Starke and
contributors. See <https://arc42.org>.

# Introduction and Goals

We want to build an app for developers and tech loving people where
you can make post and and check up on other users and see what they are posting.

## Requirements Overview

**What is AdaPt?**

- Its a versatile social network that has no UI
- Its simple but has all the features you need for a good social network
- Build for developers or tech loving people

**Essential Features**

- Create a user
- Post text messages in a global feed
- Be able to comment under any other post
- Tag other users
- Entertainment feature to receive a random cat fact, joke or activity

**Additional features:**

- Text posts can be translated from any language

## Quality Goals

1. Client Agnostic (Compatibility)

   It is not build with a specific client in mind. New clients can be developed and use our application, using only mainstream protocols and technologies.

2. Simplicity and Operability

   Because of the basic features and simplicity the network is easy to understand and quickly to manage

3. New features without design (Maintainability + time saving)

   New features can be implemented without the need of a detailed UI design for the feature

## Stakeholders

| Role/Name            | Contact | Expectations |
| :------------------- | :------ | :----------- |
| Tobias (Developer)   | /       | /            |
| Masha (Developer)    | /       | /            |
| Isabelle (Developer) | /       | /            |

# Architecture Constraints

| Constraints                            | Motivation/Description                                                                                                                                                                                                                                    |
| :------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Build a Web Application Backend        | Gain deeper knowledge of building web applications, especially the backend part of a web app.                                                                                                                                                             |
| Use TypeScript                         | Gain deeper knowledge of TypeScript.                                                                                                                                                                                                                      |
| Learn Fundamentals                     | Gain deeper knowledge of the web, Node.js & architecture fundamentals. Choosing a framework which provides a lot of architectural structures out of the box or abstracts too many of the web/Node.js fundamentals away, would therefore be a poor choice. |
| Integrate at least one external system | To challenge our architecture and learn more                                                                                                                                                                                                              |

# System Scope and Context

## Business Context

//Add Diagram here when assets are in repository

**Clients**

Anyone can use **AdaPt** if they wish to use it as an API for their Frontend based project or provide other clients and interfaces for the API consumption (e.g. webclient, mobileclient, etc).

Possible inputs:

1. Register/login
2. Posting in the general feed
3. Commenting on posts
4. Generate my username (output: random string, **external**)

**Translation (external system: Google)**

Any text should have a translation option. It will be translated to English by default
Uses Cloud Translation API

**Activity suggestions (external system)**
Activity generated by type with modifications my accessibility and type

**Cat facts** **(external system)**
Get a random cat fact.

**Random jokes** **(external system)**
Generate jokes by type: general and programming jokes.

The client calls our endpoint and chooses which API to use

## Technical Context

//Add missing diagram when repository exists

**Clients**
Any client that speaks HTTP can use our system. (e.g. webclient, mobileclient, curl in the terminal, postman etc.).

**Translation (external system: Google)**
Uses Cloud Translation API by Google to translate text posts by users.

# Solution Strategy

| Quality Goals                                              | Scenario                                 | Solution / Architectural Approach                                                                         |
| :--------------------------------------------------------- | :--------------------------------------- | :-------------------------------------------------------------------------------------------------------- |
| CLient Agnostic                                            | User uses Postman as a client            | Postman can be used with a Http protocol which is supproted by our system                                 |
| Simplictiy & Operability                                   | New user wants to start using our system | Well documented API ith examples for usage                                                                |
| New features without design                                | We add a new feature to our application  | All the old features can be used as they were so new features can be added without any problems. Untested |
| features are hidden behind feature flags to avoid downtime |

# Building Block View

# Cross-cutting Concepts

# Architecture Decisions

| Title                                           | Context                                                                                                                                                                                                                                                                                           | Desicion                                                                                                                                                                                                                                        | Status                                                                                                                                                    | Consequences                                                                                                                                                                                                                                                                                                                                                         |
| :---------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Express.js: Set a Framework for the our Backend | We need to make a decisions for this project what framework we are going to use . With consideration of what we want to learn and what works best with our project idea. In this case we want to learn more about the basics to understand features better that we already use in other projects. | Suggestion is to use express.js as our backend Framework. It gives us the possibilty to get a deeper understanding of the features that other frameworks are using. It also has more freedom of choosing which architecture path we want to go. | The status is that we already agreed to use express after comparing it with different frameworks and presenting the advantages and disadvantages of them. | More freedom of the implementation of the architecture we are going to chooseBetter understanding of the features that we are just using in other frameworks without really understanding themWe have to make more desicions on how we wanna proceed or solve different problems. In other framework there is just one or two solutions given that we can easily use |

| Title                          | Context                                                                                                                                             | Desicion                                                       | Status                                          | Consequences                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| :----------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------- | :---------------------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Backend Architecture: Modulith | Only one deployable ApplicationApplication is separated into microservice-like modules (component-based architecture / vertical-slice architecture) | Agreed to use one Monolith application separated into modules. | We agreed on the Modulith backend architecture. | All communication is within a single processSingle binary for deployment and managment with logical separation of featuresDatabase is logically split between features with no-cross-feature joinsOne benefit of the modular monolith is that the logic encapsulation enables high reusability, while data remains consistent and communication patterns simple. It is easier to manage a modular monolith than tens or hundreds of microservices, which keeps underlying infrastructural complexity and operational costs low.Not able to write it in different languages because its monolith |

| Title    | Context                                                                                                                                                                                                                                                                                                           | Desicion               | Status           | Consequences                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| :------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------------------- | :--------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| MonoRepo | We thought of using monorepo to get more familiar with it. Using a monorepo for a single project might introduce complexities that are unnecessary for smaller projects, but we will use a monorepo tool for learning and introducing more constraints that can help us be more consistent and write better code. | Agreed to use monorepo | Agreed to use Nx | Benefits of using a monorepo tool: Local computation caching: Fast Local task orchestration: Fast Distributed computation caching: Fast Distributed task execution: Fast Transparent remote execution: Fast Detecting affected projects/packages: Fast Workspace analysis: Understandable Dependency graph visualization: Understandable Code sharing: Manageable Consistent tooling: Manageable Code generation: Manageable Project constraints and visibility |

# Glossary

| Term        | Definition        |
| :---------- | :---------------- |
| _\<Term-1>_ | _\<definition-1>_ |
| _\<Term-2>_ | _\<definition-2>_ |
