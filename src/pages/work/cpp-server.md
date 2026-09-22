---
layout: ../../layouts/CaseStudy.astro
title: A modular C++ HTTP server
category: Backend engineering · UCLA CS130
summary: A team-built HTTP server with configurable request handling, tests, deployment tooling, and a development process modeled on professional engineering teams.
role: Team contributor · Rotating technical leadership
period: April–June 2025
team: The Boolean Brotherhood
tools: [C++, Boost.Asio, Boost.Beast, Google Test, Google Mock, CMake, Docker, Gerrit, Google Cloud]
note: The source and commit history are preserved in a local clone. The course Gerrit remote and previous cloud deployment are no longer accessible.
---

## Building the service and the workflow

For UCLA’s software engineering capstone, our team built a C++ HTTP server with configurable routing, static file serving, CRUD endpoints, and extensible request handlers. The project also included multithreading, logging, health checks, automated tests, and Docker-based deployment on Google Cloud.

The course deliberately modeled an engineering team’s workflow. Each assignment had a rotating technical lead responsible for task delegation and coordination. We developed incrementally and reviewed changes through Gerrit.

## My contribution

My recorded changes span the core server structure, testability, and application extensions:

- Separated server and session components and extracted configuration logic from the application entry point.
- Introduced dependency injection and tests for server, session, and configuration behavior.
- Separated routing into its own module and implemented short-lived handler logic.
- Updated the request-handler interface and its callers and tests to a shared API that returned response objects.
- Implemented a Gemini API client and example handler, with tests for payload construction, response parsing, and failure cases.

These changes involved both new functionality and refactoring existing components as the project’s interfaces evolved.

## Making behavior easier to test

Networking code can be difficult to exercise in isolation when setup, connection handling, and application behavior are tightly coupled. My changes introduced places where tests could substitute dependencies and moved configuration and routing behavior into separate modules.

The resulting tests could target smaller pieces of behavior. Later, the Gemini client used a similar approach: tests could supply controlled API responses to check successful parsing, malformed JSON, missing fields, and failed calls.

## Working in another team’s codebase

In a repository-exchange assignment, we cloned another team’s server, contributed changes, and reviewed each other’s code. My recorded work in that repository included CRUD URI parsing, request dispatch, create/update/delete operations, and HTTP status behavior.

The exercise required understanding another implementation’s conventions and fitting changes into its existing interfaces. It was a distinct part of the same course project.

## Scope and current status

The server uses a detached thread per accepted connection. A next iteration could introduce a bounded worker pool and coordinated shutdown, providing tighter control over resource use and connection lifetimes.

The local source and history remain available, although the original Gerrit service is no longer accessible and the paid cloud deployment has been taken down.
