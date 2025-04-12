# imiexer - Intelligent Mocking Interface for EXpected Execution and Recording.

Pronounced: `im-ee-ex-er`

“A lightweight, Python-native mocking engine designed for intelligent testing, seamless integration, and future-ready extensibility.”

## About

imiexer is a flexible, pluggable mock server framework for Python services — designed to bridge the feature gaps left by traditional mocking tools across languages and ecosystems.

While imiexer is not a port or rewrite of existing tools, we acknowledge the excellence of Java-based tools like WireMock, Hoverfly, and others that have set strong foundations in the service mocking domain. imiexer draws inspiration from these tools and aims to bring their best ideas into the Python ecosystem — with an emphasis on simplicity, integration, extensibility, and a true **Shift-Left Approach**.

It delivers a clean developer experience, deep test integration, and smart OpenAPI-aware mocking, while remaining fully extensible for advanced use cases like:

### 🛠 Use Cases

1. Simulate upstream services during local dev
1. Run unit and integration tests against predictable mocks
1. Build OpenAPI-driven mocking setups
1. Replay recorded interactions in CI pipelines
1. Mocking services during unit testing
1. Acting as a recorder during contract testing
1. Supporting component-level testing
1. Enabling behavior-driven service emulation
1. Extend via plugins for contract verification or stateful testing

> _imiexer_ is not a port or fork of any tool existing but derives its lot of inspirations from various tools to build a single tool that can fit in any python testing framework. _imiexer_ may not implement any feature that does not truly required for service mocking and dependent processes. Instead will provide ability to extend and create capabilties that may benefit from a Service Mocking Tool.

### Our Inspirations

> Lightweight Python simplicity and powerful mocking — with a true **Shift-Left Approach**.

We started with a simple goal to build a Python-Native service mocking tool that can integrate with modern testing tools like

- ✔️ **Lightweight & Python-native** — No Java, no containers, and zero external runtimes required
- ✔️ **Multi-service mocking** — Run multiple providers in parallel with isolated behaviors
- ✔️ **Plugin support** — Extend for contract testing, component testing, recording, and even AI integration
- ✔️ **OpenAPI-first & Shift-Left Ready** — Unlike WireMock, imiexer embraces shift-left practices by supporting OpenAPI-driven mocking, validation, and test scaffolding directly from your service contracts
- ✔️ **Developer-Friendly Interface** — Supports decorators, YAML configuration, fluent API (planned), and CLI integration for flexible test orchestration

### High Level Comparison

| Tool            | Language | Strength (Core Focus + Best Suited For)                                          | Description (Descr + Limitation)                                                                                                             | Feature Influencing imexer                              |
|-----------------|----------|----------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------|
| **WireMock**    | Java     | HTTP Mocking for CI; ideal for Java teams and backend CI pipelines               | Java-based HTTP stubbing tool with scenario-based setups. Requires Java and is not OpenAPI-aware.                                              | Request matching, fault simulation, response templating |
| **MockServer**  | Java     | Advanced HTTP Mocking; best for backend systems needing strict validation         | Rich mock server supporting expectations, validation, and contracts. Heavyweight and not easily integrated into CI/test pipelines.          | Expectation validation, contract-focused design         |
| **Karate**      | Java     | API Test + Mocking Framework; suited for QA and integration teams                | DSL-based test suite for API testing with built-in mocking and validation. DSL-heavy and Java-based.                                           | Integrated test + mock design, BDD support              |
| **Microcks**    | Java     | API Mocking + Governance; ideal for teams managing contracts and examples         | Provides OpenAPI/AsyncAPI support with test coverage dashboards. Heavy to self-host and platform-focused.                                      | Contract-driven mocking, API governance approach        |
| **Dredd**       | Node.js  | OpenAPI Conformance Testing (CLI); great for CI spec verification                  | CLI tool for testing backend API conformity to OpenAPI specs. Does not offer mocking capabilities.                                             | OpenAPI validation, CI-oriented spec checks             |
| **Prism**       | Node.js  | OpenAPI Mocking; best for design-first workflows aiding frontend/backend integration | Simulates APIs directly from OpenAPI documents. Not programmable and lacks test-runner integration.                                             | OpenAPI-first mocking, shift-left design thinking       |
| **Schemathesis**| Python   | OpenAPI-based Test Generation; ideal for testing correctness and edge cases       | Generates property-based tests from OpenAPI definitions to fuzz endpoints. It is a test-only tool with no mocking capability.                    | Schema validation, fuzz testing, spec-first coverage    |
| **Mockintosh**  | Python   | YAML-based Mock Server; perfect for lightweight REST mocking                     | Configured via YAML for simulating RESTful services. Static with limited runtime logic and extensibility.                                      | YAML-based config patterns, simplified service mocks    |
| **Mountebank**  | Node.js  | Multi-protocol Simulation; excels in quick simulation of diverse protocols         | JSON-based mock server supporting HTTP, TCP, SMTP, etc. Not Python-native and lacks test-runner integration.                                   | Multi-protocol simulation, JSON-driven mocks            |
| **Hoverfly**    | Go       | Proxy-based Simulation; ideal for traffic replay and dynamic integration testing   | Captures and simulates traffic through proxying with scripting support. Requires Go and scripting expertise.                                   | Proxy mode, scripting, dynamic traffic replay           |

## imiexer Features Roadmap

> Legend: ✅ Completed | 🔄 In Progress | ⏳ Planned | ❌ Not Planned |

1. **Mocking Engine**
   - **Execution & Integration**
     - ✅ Config-Based (YAML/env) support - YAML & JSON configuration files and environment variable loading.
     - ✅ Decorator-Based API implementation - Provides decorators for simple mock endpoint setup.
     - 🔄 PyTest support - Enable integration with the PyTest framework.
     - 🔄 UnitTest support - Compatibility with Python's unittest framework.
     - ⏳ Fluent API (chainable methods) - Intuitive, chainable configuration.
     - ⏳ CI/CD CLI Support - Command-line tools for CI/CD pipeline integration.
   - **Protocol Support**
     - ✅ HTTP support - Handles HTTP requests for service mocking.
     - ✅ HTTPS support - Secure HTTPS communication.
     - ⏳ TCP support - Planned support for TCP-based protocols.
     - ⏳ WebSocket support - Intended for real-time interactions.
     - ⏳ gRPC support - Planned gRPC simulation.
     - ⏳ GraphQL support - Planned GraphQL API mocking.
   - **OpenAPI Compatibility**
     - 🔄 Swagger/JSON support - Generate mocks from Swagger/JSON definitions.
     - 🔄 Spec validation - Validate mocks against OpenAPI specifications.
   - **Dynamic Response Templating**
     - ✅ Templating engine - Utilizes Jinja2 for dynamic response rendering.
     - ✅ Conditional logic - Leverages template conditions for adaptive responses.
     - ✅ Response injection - Injects dynamic content into responses.
   - **Matching Rules**
     - ✅ URL matching - Matches incoming requests by URL paths.
     - ✅ Headers matching - Uses regex-based header matching.
     - ✅ Request body matching - Implements regex matching for request bodies.
     - ⏳ Matchers supported - Additional matching options are planned.
     - ⏳ Matcher engine type - Customization of the matching engine is in planning.
     - ⏳ Matcher customization - Support for further custom matcher options is planned.
     - ⏳ HTTP Method matching - Planned enhancement for matching by HTTP verbs.
     - ⏳ Query parameters matching - Future support for regex matching of query params.
     - ⏳ Form parameters matching - Planned matching for form data.
     - ⏳ Cookies matching - Future matching based on cookies.
     - ⏳ Multipart/form-data matching - Intended for multipart request handling.
   - **Stateful Behavior Mocking**
     - 🔄 Scenario responses - Planned support for multi-step, scenario-based responses.
     - ⏳ History tracking - Maintain interaction history for stateful tests (planned).
     - ⏳ Mutable state - Enable dynamic state changes across interactions (planned).
     - ⏳ Sequence mocking - Provide sequential responses in stateful flows (planned).
   - **Recording Capabilities**
     - ✅ Interaction recording - Records all interactions for playback and analysis.
     - 🔄 Request logging - Detailed logging of incoming requests is planned.
     - 🔄 Replay support - Future support for replaying recorded interactions.
     - 🔄 Inspection API - An API to inspect and query recorded data is in planning.
   - ✅ Multi-Service Support - Manages multiple mock services concurrently.
   - ✅ Fault injection / delays - Simulates response delays and fault conditions.
   - ⏳ Fixture file support - Planned loading of predefined response fixtures.
   - ⏳ Stubbing - Mapping static responses to endpoints is planned.
2. **Plugin & Extensibility**
   - ✅ Lifecycle events - Hooks for various server lifecycle stages are supported.
   - ✅ Plugin system - Basic plugin registration and processing are implemented.
   - 🔄 Behavior injection - Future support for dynamic injection of custom behaviors.
   - 🔄 Plugin ecosystem - Community-driven plugin extensions are in planning.
3. **Advanced Support**
   - **Authentication Mocking**
     - ⏳ Basic authentication - Simulation for basic authentication is planned.
   - ⏳ Artificial Intelligence - Integration for intelligent response simulation is in planning.
   - ⏳ Proxying - Enable proxying of requests to live services (planned).
   - ⏳ Multi-Domain support - Future support for serving multiple domains.
   - ⏳ Behavior-Driven Development (BDD) - Planned support for BDD-driven testing workflows.
   - **Monitoring & Administration**
     - ⏳ Admin API and UI - Planned administrative interfaces for monitoring.
     - ⏳ Dashboard UI - A real-time system dashboard is intended.
     - ⏳ Admin REST API - REST endpoints for administrative tasks are in planning.
     - ⏳ Logs & metrics - Logging and metrics collection are planned.
   - ❌ Container Support - Enable containerized environments.
   - ❌ Standalone - Support running imiexer as a standalone server.
