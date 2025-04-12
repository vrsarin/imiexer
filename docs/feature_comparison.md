# Feature Comparison Table

## Test Framework Support

| Feature          | WireMock | MockServer | Karate      | Microcks | Dredd | Prism | Schemathesis | Mountebank | Hoverfly | Mockintosh |
| ---------------- | -------- | ---------- | ----------- | -------- | ----- | ----- | ------------ | ---------- | -------- | ---------- |
| PyTest support   | ❌       | ❌         | ⚠️ Indirect | ❌       | ❌    | ❌    | ❌           | ❌         | ❌       | ✅         |
| UnitTest support | ❌       | ❌         | ❌          | ❌       | ❌    | ❌    | ❌           | ❌         | ❌       | ❌         |
| CLI support      | ❌       | ❌         | ⚠️ Custom   | ✅       | ✅    | ❌    | ✅           | ⚠️ Manual  | ❌       | ✅         |

## OpenAPI Compatibility

| Feature              | WireMock | MockServer | Karate      | Microcks | Dredd | Prism | Schemathesis | Mountebank | Hoverfly   | Mockintosh |
| -------------------- | -------- | ---------- | ----------- | -------- | ----- | ----- | ------------ | ---------- | ---------- | ---------- |
| Swagger/JSON support | ❌       | ✅         | ⚠️ Indirect | ✅       | ✅    | ✅    | ✅           | ⚠️ Partial | ⚠️ Partial | ❌         |
| Spec validation      | ❌       | ✅         | ⚠️ Partial  | ✅       | ✅    | ✅    | ✅           | ⚠️ Basic   | ⚠️ Basic   | ❌         |

## Protocol Support

| Feature           | WireMock | MockServer | Karate | Microcks | Dredd | Prism | Schemathesis | Mountebank | Hoverfly | Mockintosh |
| ----------------- | -------- | ---------- | ------ | -------- | ----- | ----- | ------------ | ---------- | -------- | ---------- |
| HTTP support      | ✅       | ✅         | ✅     | ✅       | ✅    | ✅    | ✅           | ✅         | ✅       | ✅         |
| HTTPS support     | ✅       | ✅         | ✅     | ✅       | ✅    | ✅    | ✅           | ✅         | ✅       | ⚠️ Partial |
| TCP support       | ❌       | ❌         | ❌     | ❌       | ❌    | ❌    | ❌           | ✅         | ✅       | ❌         |
| WebSocket support | ❌       | ❌         | ❌     | ❌       | ❌    | ❌    | ❌           | ⚠️ Partial | ✅       | ❌         |
| gRPC support      | ❌       | ❌         | ❌     | ❌       | ❌    | ❌    | ❌           | ❌         | ❌       | ❌         |
| GraphQL support   | ❌       | ❌         | ❌     | ✅       | ❌    | ✅    | ❌           | ❌         | ❌       | ❌         |

## Dynamic Response Templating

| Feature            | WireMock  | MockServer | Karate     | Microcks  | Dredd | Prism | Schemathesis | Mountebank   | Hoverfly   | Mockintosh |
| ------------------ | --------- | ---------- | ---------- | --------- | ----- | ----- | ------------ | ------------ | ---------- | ---------- |
| Templating engine  | ✅ DSL    | ⚠️ Static  | ✅ DSL     | ⚠️ Static | ❌    | ❌    | ❌           | ✅ Lua/Go    | ✅ Lua     | ⚠️ Basic   |
| Conditional logic  | ✅ Rules  | ⚠️ Partial | ✅ If/Else | ⚠️ Basic  | ❌    | ❌    | ❌           | ✅ Scripts   | ✅ Scripts | ❌         |
| Response injection | ✅ Params | ⚠️ Tokens  | ✅ Vars    | ⚠️ Limit  | ❌    | ❌    | ❌           | ✅ Templates | ✅ Templ.  | ⚠️ Static  |

## Matching Rules

| Feature               | WireMock  | MockServer | Karate | Microcks  | Dredd | Prism    | Schemathesis  | Mountebank  | Hoverfly  | Mockintosh |
| --------------------- | --------- | ---------- | ------ | --------- | ----- | -------- | ------------- | ----------- | --------- | ---------- |
| Matchers supported    | ✅ Strong | ✅ Regex   | ✅     | ✅ Rules  | ❌    | ⚠️ Basic | ⚠️ Schema     | ✅ JSONPath | ✅        | ⚠️ Basic   |
| Matcher engine type   | ✅ Custom | ✅ Regex   | ✅ DSL | ✅ Schema | ❌    | ⚠️ Basic | ✅ Hypothesis | ✅ JSONPath | ✅        | ⚠️ Basic   |
| Matcher customization | ✅ Full   | ⚠️ Limited | ⚠️ DSL | ✅ Profs  | ❌    | ❌       | ⚠️ Schema     | ⚠️ Partial  | ⚠️ Static | ❌         |

## Stateful Mocking

| Feature            | WireMock   | MockServer | Karate | Microcks   | Dredd | Prism | Schemathesis | Mountebank | Hoverfly   | Mockintosh |
| ------------------ | ---------- | ---------- | ------ | ---------- | ----- | ----- | ------------ | ---------- | ---------- | ---------- |
| Scenario responses | ✅         | ✅         | ✅     | ✅         | ❌    | ❌    | ❌           | ✅         | ✅         | ❌         |
| History tracking   | ✅         | ⚠️ Partial | ✅     | ✅         | ❌    | ❌    | ❌           | ⚠️ Partial | ⚠️ Partial | ❌         |
| Mutable state      | ⚠️ Limited | ❌         | ✅     | ✅         | ❌    | ❌    | ❌           | ⚠️ Partial | ⚠️ Partial | ❌         |
| Sequence mocking   | ✅         | ⚠️ Limited | ✅     | ⚠️ Partial | ❌    | ❌    | ❌           | ✅         | ⚠️ Script  | ❌         |

## Recording Capabilities

| Feature             | WireMock  | MockServer | Karate     | Microcks | Dredd | Prism | Schemathesis | Mountebank | Hoverfly | Mockintosh |
| ------------------- | --------- | ---------- | ---------- | -------- | ----- | ----- | ------------ | ---------- | -------- | ---------- |
| Interaction logging | ✅        | ✅         | ✅         | ✅       | ❌    | ❌    | ❌           | ✅         | ✅       | ❌         |
| Replay support      | ⚠️ Manual | ⚠️ Partial | ✅         | ✅       | ❌    | ❌    | ❌           | ⚠️ Script  | ✅       | ❌         |
| Inspection API      | ⚠️ Tools  | ⚠️ Limited | ✅ Inspect | ✅ UI    | ❌    | ❌    | ❌           | ⚠️ CLI     | ✅ UI    | ❌         |

## Admin & Monitoring

| Feature        | WireMock   | MockServer | Karate | Microcks | Dredd | Prism | Schemathesis | Mountebank | Hoverfly   | Mockintosh |
| -------------- | ---------- | ---------- | ------ | -------- | ----- | ----- | ------------ | ---------- | ---------- | ---------- |
| Dashboard UI   | ✅         | ✅         | ❌     | ✅       | ❌    | ❌    | ❌           | ✅         | ✅         | ❌         |
| Admin REST API | ⚠️ Partial | ✅         | ❌     | ✅       | ❌    | ❌    | ❌           | ⚠️ Scripts | ✅ Partial | ❌         |
| Logs & metrics | ⚠️ Tools   | ⚠️ Logs    | ❌     | ✅       | ❌    | ❌    | ❌           | ⚠️ CLI     | ✅ Script  | ❌         |

## Plugin Extensibility

| Feature            | WireMock | MockServer | Karate | Microcks   | Dredd | Prism | Schemathesis | Mountebank | Hoverfly | Mockintosh |
| ------------------ | -------- | ---------- | ------ | ---------- | ----- | ----- | ------------ | ---------- | -------- | ---------- |
| Plugin system      | ❌       | ❌         | ❌     | ✅         | ❌    | ❌    | ❌           | ✅         | ✅       | ❌         |
| Behavior injection | ❌       | ❌         | ⚠️ DSL | ✅         | ❌    | ❌    | ❌           | ✅ Scripts | ✅       | ❌         |
| Plugin ecosystem   | ❌       | ❌         | ❌     | ⚠️ Limited | ❌    | ❌    | ❌           | ⚠️ Minimal | ⚠️ Comm. | ❌         |
