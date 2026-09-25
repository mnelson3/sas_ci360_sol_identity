# sas_ci360_sol_identity

Historical Python client for SAS Customer Intelligence 360 **identity and SCIM** APIs, retained as a reference. It is part of the `sas-ci360` family of solution packages, alongside packages for planning, execution, data, content delivery, and workflow.

> This package is superseded by [`sas-ci360-sdk`](https://github.com/mnelson3/sas-ci360-sdk), which holds the maintained implementation. Use this repository for reference only.

<br>

### Table of Contents

- <a href="#overview">Overview</a>
- <a href="#prerequisites">Prerequisites</a>
- <a href="#installation">Installation</a>
- <a href="#getting-started">Getting Started</a>
- <a href="#solutions-code">Solutions Code</a>
- <a href="#contributing">Contributing</a>
- <a href="#license">License</a>
- <a href="#additional-resources">Additional Resources</a>

<br>

### Overview

`sasci360solidentity` wraps the CI 360 SCIM (System for Cross-domain Identity Management) API with a thin `Identity` class built on top of the shared `sasci360apicore` (connection, encryption, logging) and `sasci360apiscim` packages. It's meant to be dropped into automation scripts or scheduled jobs that need to manage CI 360 users/identities programmatically rather than through the UI.

<br>

### Prerequisites

- Python 3.6+
- A SAS CI 360 tenant with API credentials (host, tenant ID, and a secret key/algorithm for token signing)
- Network access to the CI 360 REST endpoints from wherever the client runs

<br>

### Installation

```bash
pip install -r requirements.txt
```

Key dependencies: `pandas`, `PyJWT`, `requests`, `saspy`, `schedule`, `DateTime`, `urllib3`, plus the sibling `sasci360apicore` and `sasci360apiscim` packages.

<br>

### Getting Started

```python
from sasci360solidentity import Identity

identity = Identity(
    algorithm="HS256",
    api="scim",
    encoding="utf-8",
    host="https://your-ci360-tenant.example.com",
    secret_key="<supplied via env var / secrets manager, never hardcoded>",
    tenant_id="<your-tenant-id>",
)
```

Credentials should always come from environment variables or a secrets manager — never commit them to source.

<br>

### Solutions Code

The package builds on the shared `sasci360apicore` primitives:

1. **Connection** — session and auth token management
1. **Encryption** — JWT signing/encoding for API auth
1. **Logger** — structured logging for client operations

<br>

### Contributing

We welcome your contributions! Please read [CONTRIBUTING](CONTRIBUTING.md) for details on how to submit contributions to this project.

<br>

### License

This project is licensed under the [Apache 2.0 License](LICENSE).

<br>

### Additional Resources

For more information, see [REST APIs](https://go.documentation.sas.com/doc/en/cintcdc/production.a/cintapis/ch-rest-apis.htm).
