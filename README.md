# imiexer - Intelligent Mocking Interface for EXpected Execution and Recording.

Pronounced: `im-ee-ex-er`

“A lightweight, Python-native mocking engine designed for intelligent testing, seamless integration, and future-ready extensibility.”

## What is imiexer?

imiexer is a flexible, pluggable mock server framework for Python services — designed to bridge the feature gaps left by traditional mocking tools across languages and ecosystems.

While imiexer is not a port or rewrite of existing tools, we acknowledge the excellence of Java-based tools like WireMock, Hoverfly, and others that have set strong foundations in the service mocking domain. imiexer draws inspiration from these tools and aims to bring their best ideas into the Python ecosystem — with an emphasis on simplicity, integration, extensibility, and a true shift-left approach.

It delivers a clean developer experience, deep test integration, and smart OpenAPI-aware mocking, while remaining fully extensible for advanced use cases like:

1. Mocking services during unit testing
1. Acting as a recorder during contract testing
1. Supporting component-level testing
1. Enabling behavior-driven service emulation

## Why imiexer?

`Lightweight Python simplicity and powerful mocking — with a true shift-left approach.`

- ✔️ **Lightweight & Python-native** — No Java, no containers, and zero external runtimes required
- ✔️ **Multi-service mocking** — Run multiple providers in parallel with isolated behaviors
- ✔️ **Plugin support** — Extend for contract testing, component testing, recording, and even AI integration
- ✔️ **OpenAPI-first & Shift-Left Ready** — Unlike WireMock, imiexer embraces shift-left practices by supporting OpenAPI-driven mocking, validation, and test scaffolding directly from your service contracts
- ✔️ **Developer-Friendly Interface** — Supports decorators, YAML configuration, fluent API (planned), and CLI integration for flexible test orchestration

## Our Inspirations

| Tool             | Language | Core Focus                        | Description / Purpose                                                                                   | Limitations / Caveats                            | Best Suited For                                                            | Features Influencing imiexer                            |
| ---------------- | -------- | --------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------ | -------------------------------------------------------------------------- | ------------------------------------------------------- |
| **WireMock**     | Java     | HTTP Mocking for CI               | Java-based HTTP stubbing tool used widely in enterprise CI with expectations and scenario-based setups. | Requires Java, not OpenAPI-aware                 | Java teams and backend CI pipelines needing mature HTTP stubbing.          | Request matching, fault simulation, response templating |
| **MockServer**   | Java     | Advanced HTTP Mocking             | Rich Java mock server with support for expectations, validation, and contracts.                         | Heavyweight, not easily CI/test integrated       | Backend systems needing strict validation logic for contract matching.     | Expectation validation, contract-focused design         |
| **Karate**       | Java     | API Test + Mocking Framework      | DSL-based test suite for API testing with built-in mocking, validation, and contract testing.           | DSL-heavy, Java-based                            | QA and integration teams needing expressive API test scenarios with mocks. | Integrated test + mock design, BDD support              |
| **Microcks**     | Java     | API Mocking + Governance          | Contract and example-based mocking platform with OpenAPI/AsyncAPI support and test coverage dashboards. | Heavy to self-host, platform-focused             | API platform teams that manage contracts, examples, and mocking at scale.  | Contract-driven mocking, API governance approach        |
| **Dredd**        | Node.js  | OpenAPI Conformance Testing (CLI) | CLI tool to test whether a backend API implementation conforms to an OpenAPI specification.             | No mocks, validator only                         | Verifying implementation against spec, often integrated into CI.           | OpenAPI validation, CI-oriented spec checks             |
| **Prism**        | Node.js  | OpenAPI Mocking                   | Mock server that simulates APIs directly from OpenAPI documents, ideal for design-first workflows.      | Not programmable, no test-runner tie-in          | Mocking APIs early in design phases to help frontend/backend integration.  | OpenAPI-first mocking, shift-left design thinking       |
| **Schemathesis** | Python   | OpenAPI-based Test Generation     | Generates property-based tests from OpenAPI definitions to fuzz and validate endpoints.                 | No mocking, test-only tool                       | Testing APIs for correctness, conformance, and edge case handling.         | Schema validation, fuzz testing, spec-first coverage    |
| **Mockintosh**   | Python   | YAML-based Mock Server            | Declarative mock server configured with YAML, suitable for simulating RESTful services.                 | Static, lacks runtime logic and extensibility    | Lightweight REST mocking with readable configuration.                      | YAML-based config patterns, simplified service mocks    |
| **Mountebank**   | Node.js  | Multi-protocol Simulation         | Flexible JSON-based mock server supporting HTTP, TCP, SMTP, etc. with easy config.                      | Not Python-native, lacks test-runner integration | Quick simulations of diverse protocols with minimal setup.                 | Multi-protocol simulation, JSON-driven mocks            |
| **Hoverfly**     | Go       | Proxy-based Simulation            | Captures and simulates traffic through proxying, with scripting support for dynamic behavior.           | Requires Go, scripting knowledge                 | Integrating traffic replay/mirroring into integration tests or CI.         | Proxy mode, scripting, dynamic traffic replay           |

## Feature Comparison Table

### Test Framework Support

| Feature          | WireMock | MockServer | Karate      | Microcks | Dredd | Prism | Schemathesis | Mountebank | Hoverfly | Mockintosh | imiexer |
| ---------------- | -------- | ---------- | ----------- | -------- | ----- | ----- | ------------ | ---------- | -------- | ---------- | ------- |
| PyTest support   | ❌       | ❌         | ⚠️ Indirect | ❌       | ❌    | ❌    | ❌           | ❌         | ❌       | ✅         | ✅      |
| UnitTest support | ❌       | ❌         | ❌          | ❌       | ❌    | ❌    | ❌           | ❌         | ❌       | ❌         | ✅      |
| CLI support      | ❌       | ❌         | ⚠️ Custom   | ✅       | ✅    | ❌    | ✅           | ⚠️ Manual  | ❌       | ✅         | ✅      |

### OpenAPI Compatibility

| Feature              | WireMock | MockServer | Karate      | Microcks | Dredd | Prism | Schemathesis | Mountebank | Hoverfly   | Mockintosh | imiexer |
| -------------------- | -------- | ---------- | ----------- | -------- | ----- | ----- | ------------ | ---------- | ---------- | ---------- | ------- |
| Swagger/JSON support | ❌       | ✅         | ⚠️ Indirect | ✅       | ✅    | ✅    | ✅           | ⚠️ Partial | ⚠️ Partial | ❌         | ✅      |
| Spec validation      | ❌       | ✅         | ⚠️ Partial  | ✅       | ✅    | ✅    | ✅           | ⚠️ Basic   | ⚠️ Basic   | ❌         | ✅      |

### Protocol Support

| Feature           | WireMock | MockServer | Karate | Microcks | Dredd | Prism | Schemathesis | Mountebank | Hoverfly | Mockintosh | imiexer    |
| ----------------- | -------- | ---------- | ------ | -------- | ----- | ----- | ------------ | ---------- | -------- | ---------- | ---------- |
| HTTP support      | ✅       | ✅         | ✅     | ✅       | ✅    | ✅    | ✅           | ✅         | ✅       | ✅         | ✅         |
| HTTPS support     | ✅       | ✅         | ✅     | ✅       | ✅    | ✅    | ✅           | ✅         | ✅       | ⚠️ Partial | ✅ Planned |
| TCP support       | ❌       | ❌         | ❌     | ❌       | ❌    | ❌    | ❌           | ✅         | ✅       | ❌         | ❌         |
| WebSocket support | ❌       | ❌         | ❌     | ❌       | ❌    | ❌    | ❌           | ⚠️ Partial | ✅       | ❌         | ⚠️ Planned |
| gRPC support      | ❌       | ❌         | ❌     | ❌       | ❌    | ❌    | ❌           | ❌         | ❌       | ❌         | ⚠️ Planned |
| GraphQL support   | ❌       | ❌         | ❌     | ✅       | ❌    | ✅    | ❌           | ❌         | ❌       | ❌         | ⚠️ Planned |

### Dynamic Response Templating

| Feature            | WireMock  | MockServer | Karate     | Microcks  | Dredd | Prism | Schemathesis | Mountebank   | Hoverfly   | Mockintosh | imiexer    |
| ------------------ | --------- | ---------- | ---------- | --------- | ----- | ----- | ------------ | ------------ | ---------- | ---------- | ---------- |
| Templating engine  | ✅ DSL    | ⚠️ Static  | ✅ DSL     | ⚠️ Static | ❌    | ❌    | ❌           | ✅ Lua/Go    | ✅ Lua     | ⚠️ Basic   | ✅ Jinja2  |
| Conditional logic  | ✅ Rules  | ⚠️ Partial | ✅ If/Else | ⚠️ Basic  | ❌    | ❌    | ❌           | ✅ Scripts   | ✅ Scripts | ❌         | ✅ Full    |
| Response injection | ✅ Params | ⚠️ Tokens  | ✅ Vars    | ⚠️ Limit  | ❌    | ❌    | ❌           | ✅ Templates | ✅ Templ.  | ⚠️ Static  | ✅ Dynamic |

### Matching Rules

| Feature               | WireMock  | MockServer | Karate | Microcks  | Dredd | Prism    | Schemathesis  | Mountebank  | Hoverfly  | Mockintosh | imiexer   |
| --------------------- | --------- | ---------- | ------ | --------- | ----- | -------- | ------------- | ----------- | --------- | ---------- | --------- |
| Matchers supported    | ✅ Strong | ✅ Regex   | ✅     | ✅ Rules  | ❌    | ⚠️ Basic | ⚠️ Schema     | ✅ JSONPath | ✅        | ⚠️ Basic   | ✅ Flex   |
| Matcher engine type   | ✅ Custom | ✅ Regex   | ✅ DSL | ✅ Schema | ❌    | ⚠️ Basic | ✅ Hypothesis | ✅ JSONPath | ✅        | ⚠️ Basic   | ✅ Custom |
| Matcher customization | ✅ Full   | ⚠️ Limited | ⚠️ DSL | ✅ Profs  | ❌    | ❌       | ⚠️ Schema     | ⚠️ Partial  | ⚠️ Static | ❌         | ✅ Logic  |

### Stateful Mocking

| Feature            | WireMock   | MockServer | Karate | Microcks   | Dredd | Prism | Schemathesis | Mountebank | Hoverfly   | Mockintosh | imiexer |
| ------------------ | ---------- | ---------- | ------ | ---------- | ----- | ----- | ------------ | ---------- | ---------- | ---------- | ------- |
| Scenario responses | ✅         | ✅         | ✅     | ✅         | ❌    | ❌    | ❌           | ✅         | ✅         | ❌         | ✅      |
| History tracking   | ✅         | ⚠️ Partial | ✅     | ✅         | ❌    | ❌    | ❌           | ⚠️ Partial | ⚠️ Partial | ❌         | ✅      |
| Mutable state      | ⚠️ Limited | ❌         | ✅     | ✅         | ❌    | ❌    | ❌           | ⚠️ Partial | ⚠️ Partial | ❌         | ✅      |
| Sequence mocking   | ✅         | ⚠️ Limited | ✅     | ⚠️ Partial | ❌    | ❌    | ❌           | ✅         | ⚠️ Script  | ❌         | ✅      |

### Recording Capabilities

| Feature             | WireMock  | MockServer | Karate     | Microcks | Dredd | Prism | Schemathesis | Mountebank | Hoverfly | Mockintosh | imiexer    |
| ------------------- | --------- | ---------- | ---------- | -------- | ----- | ----- | ------------ | ---------- | -------- | ---------- | ---------- |
| Interaction logging | ✅        | ✅         | ✅         | ✅       | ❌    | ❌    | ❌           | ✅         | ✅       | ❌         | ✅         |
| Replay support      | ⚠️ Manual | ⚠️ Partial | ✅         | ✅       | ❌    | ❌    | ❌           | ⚠️ Script  | ✅       | ❌         | ✅         |
| Inspection API      | ⚠️ Tools  | ⚠️ Limited | ✅ Inspect | ✅ UI    | ❌    | ❌    | ❌           | ⚠️ CLI     | ✅ UI    | ❌         | ⚠️ Planned |

### Admin & Monitoring

| Feature        | WireMock   | MockServer | Karate | Microcks | Dredd | Prism | Schemathesis | Mountebank | Hoverfly   | Mockintosh | imiexer    |
| -------------- | ---------- | ---------- | ------ | -------- | ----- | ----- | ------------ | ---------- | ---------- | ---------- | ---------- |
| Dashboard UI   | ✅         | ✅         | ❌     | ✅       | ❌    | ❌    | ❌           | ✅         | ✅         | ❌         | ⚠️ Planned |
| Admin REST API | ⚠️ Partial | ✅         | ❌     | ✅       | ❌    | ❌    | ❌           | ⚠️ Scripts | ✅ Partial | ❌         | ⚠️ Planned |
| Logs & metrics | ⚠️ Tools   | ⚠️ Logs    | ❌     | ✅       | ❌    | ❌    | ❌           | ⚠️ CLI     | ✅ Script  | ❌         | ⚠️ Planned |

### Plugin Extensibility

| Feature            | WireMock | MockServer | Karate | Microcks   | Dredd | Prism | Schemathesis | Mountebank | Hoverfly | Mockintosh | imiexer    |
| ------------------ | -------- | ---------- | ------ | ---------- | ----- | ----- | ------------ | ---------- | -------- | ---------- | ---------- |
| Plugin system      | ❌       | ❌         | ❌     | ✅         | ❌    | ❌    | ❌           | ✅         | ✅       | ❌         | ✅ Core    |
| Behavior injection | ❌       | ❌         | ⚠️ DSL | ✅         | ❌    | ❌    | ❌           | ✅ Scripts | ✅       | ❌         | ✅ Hooks   |
| Plugin ecosystem   | ❌       | ❌         | ❌     | ⚠️ Limited | ❌    | ❌    | ❌           | ⚠️ Minimal | ⚠️ Comm. | ❌         | ⚠️ Planned |

## 🛠 Use Cases

1. Simulate upstream services during local dev
1. Run unit and integration tests against predictable mocks
1. Build OpenAPI-driven mocking setups
1. Replay recorded interactions in CI pipelines
1. Extend via plugins for contract verification or stateful testing

## Features

### Execution & Integration

- [ ] PyTest support
- [ ] UnitTest support
- [ ] CLI support
- [x] Config-Based (YAML/env) support
- [x] Decorator-Based API implementation
- [ ] Fluent API (chainable methods)
- [ ] CI/CD CLI
- [ ] Shift-Left Approach
- [ ] Container Support (Not Planned)
- [ ] Standalone (Not Planned)

### Core Mocking Capabilities

- [x] Multi-Service Support
- [ ] Stubbing
- [x] Dynamic Response Templating
- [x] Fault injection / delays
- [x] Stateful Behaviors
- [x] Request logging / history
- [x] OpenAPI spec integration / validation
- [x] Interaction recording
- [ ] Fixture file support

### Advanced Features

- [ ] Proxying
- [x] http/s support
- [ ] gRPC support
- [ ] GraphQL support
- [ ] Webhooks and Callbacks
- [x] URL matching
- [x] HTTP Method matching
- [x] Query parameters matching
- [ ] Form parameters matching
- [x] Headers matching
- [ ] Basic authentication
- [ ] Cookies matching
- [x] Request body matching
- [ ] Multipart/form-data matching
- [x] Lifecycle events
- [ ] Admin API and UI
- [ ] Artificial Intelligence
- [ ] Multi-Domain support
- [ ] Behavior-Driven Development (BDD)

### Plugin & Extensibility

- [x] Extensibility
- [ ] Plugin system
- [ ] Behavior injection
- [ ] Plugin ecosystem

### Monitoring & Administration

- [ ] Dashboard UI
- [ ] Admin REST API
- [ ] Logs & metrics

### OpenAPI Compatibility

- [ ] Swagger/JSON support
- [ ] Spec validation

### Protocol Support

- [x] HTTP support
- [x] HTTPS support
- [ ] TCP support
- [ ] WebSocket support
- [ ] gRPC support
- [ ] GraphQL support

### Dynamic Response Templating

- [ ] Templating engine
- [ ] Conditional logic
- [ ] Response injection

### Matching Rules

- [ ] Matchers supported
- [ ] Matcher engine type
- [ ] Matcher customization

### Stateful Mocking

- [ ] Scenario responses
- [ ] History tracking
- [ ] Mutable state
- [ ] Sequence mocking

### Recording Capabilities

- [ ] Interaction logging
- [ ] Replay support
- [ ] Inspection API
