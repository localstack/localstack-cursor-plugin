# LocalStack Cursor Plugin

The official [LocalStack](https://localstack.cloud) plugin for [Cursor](https://cursor.com) — brings local cloud development with the LocalStack emulators for AWS, Snowflake, and Azure directly into your IDE.

## What's included

### MCP Server

The plugin bundles the [LocalStack MCP Server](https://github.com/localstack/localstack-mcp-server) (`@localstack/localstack-mcp-server`), giving the AI agent direct access to:

| Tool | Description |
|------|-------------|
| `localstack-management` | Start, stop, restart, and check status of the AWS, Snowflake, and Azure emulators |
| `localstack-deployer` | Deploy CDK, Terraform, SAM, and CloudFormation projects through `lstk` |
| `localstack-logs-analysis` | Summarize logs, group errors, and filter by service and operation |
| `localstack-aws-client` | Run AWS CLI v2 commands against LocalStack through `lstk aws` |
| `localstack-app-inspector` | Inspect traces, spans, events, payloads, and IAM evaluations with suggested fixes |
| `localstack-iam-policy-analyzer` | Switch IAM enforcement and generate policies from access failures |
| `localstack-chaos-injector` | Inject service faults and network latency |
| `localstack-cloud-pods` | Save, load, and delete remote Cloud Pods |
| `localstack-state-management` | Export, import, inspect, and reset state with local files |
| `localstack-extensions` | Install, uninstall, list, and discover LocalStack Extensions |
| `localstack-ephemeral-instances` | Create and manage cloud-hosted Ephemeral Instances |
| `localstack-aws-replicator` | Replicate resources from a real AWS account into LocalStack |
| `localstack-docs` | Search the LocalStack documentation |
| `localstack-snowflake-client` | Run SQL against the Snowflake emulator with the `snow` CLI |
| `localstack-azure-client` | Run Azure CLI (`az`) commands against the Azure emulator |

The server also provides the `infrastructure-tester` prompt, which deploys an IaC project, validates every declared resource against live state, and writes integration tests.

### Skills

The plugin ships the [LocalStack AI Skills](https://github.com/localstack/skills), which give the agent contextual knowledge for common workflows using the [`lstk`](https://docs.localstack.cloud/aws/developer-tools/running-localstack/lstk/) CLI:

| Skill | Description |
|-------|-------------|
| **localstack** | Emulator lifecycle with `lstk` (start, stop, status, restart, reset, doctor) |
| **localstack-deploy** | Deploy with `lstk deploy`, Terraform, CDK, CloudFormation, SAM, and Pulumi |
| **localstack-infra-test** | Deploy IaC, validate every resource against live state, and write integration tests |
| **localstack-state** | Save, load, inspect, and reset state with snapshots and Cloud Pods |
| **localstack-logs** | Analyze logs, identify errors, and debug issues |
| **localstack-iam** | Switch IAM enforcement and generate least-privilege policies from denials |
| **localstack-app-inspector** | Trace requests across services with App Inspector |
| **localstack-chaos** | Inject faults and latency to test resilience |
| **localstack-replicator** | Replicate resources from a real AWS account into LocalStack |
| **localstack-extensions** | Install, list, and discover LocalStack Extensions |
| **localstack-snowflake** | Run the Snowflake emulator and execute SQL with the `snow` CLI |
| **localstack-azure** | Run the Azure emulator and drive it with `lstk az` |

## Installation

Install from the [Cursor Marketplace](https://cursor.com/marketplace) by searching for **LocalStack**. You can also install it via Cursor CLI:

```bash
cursor plugins install localstack-cursor-plugin
```

## Prerequisites

- Docker running on your machine
- [Node.js](https://nodejs.org/) v20 or newer (for the MCP server)
- A [LocalStack Auth Token](https://docs.localstack.cloud/aws/getting-started/auth-token/), set as `LOCALSTACK_AUTH_TOKEN` — **required for all MCP tools**
- The [`lstk` CLI](https://docs.localstack.cloud/aws/developer-tools/running-localstack/lstk/):

  ```bash
  brew install localstack/tap/lstk   # or: npm install -g @localstack/lstk
  lstk login
  ```

- The tools you want to use, on your `PATH`: [AWS CLI v2](https://aws.amazon.com/cli/), `terraform`, `cdk` (2.177.0+), or `sam` (1.95.0+). Optionally `snow` for Snowflake, `az` for Azure, and `pulumilocal` for Pulumi.

## Configuration

### LocalStack Auth Token

The plugin declares a required `LOCALSTACK_AUTH_TOKEN` variable. Set it in Cursor under **Plugins** → **LocalStack** → **Configure**; Cursor passes it to the MCP server.
### LocalStack-specific configuration

To set any other LocalStack configuration, add the corresponding environment variable to the MCP server configuration. See the [MCP server configuration reference](https://github.com/localstack/localstack-mcp-server#localstack-configuration) and the [LocalStack configuration documentation](https://docs.localstack.cloud/aws/capabilities/config/configuration/).

## Project structure

```
localstack-cursor-plugin/
├── .cursor-plugin/
│   └── plugin.json              # Plugin manifest
├── skills/                      # Synced from github.com/localstack/skills
│   ├── localstack-lifecycle/    # Emulator lifecycle
│   ├── iac-deployment/          # Terraform, CDK, CloudFormation, SAM, Pulumi
│   ├── infrastructure-testing/  # Validate deployments and write tests
│   ├── state-management/        # Snapshots and Cloud Pods
│   ├── logs-analysis/           # Log analysis and debugging
│   ├── iam-policy-analyzer/     # IAM enforcement and policy generation
│   ├── app-inspector/           # Request tracing
│   ├── chaos-engineering/       # Fault and latency injection
│   ├── aws-replicator/          # Replicate resources from real AWS
│   ├── localstack-extensions/   # Extension management
│   ├── snowflake/               # Snowflake emulator
│   └── azure/                   # Azure emulator
├── assets/
│   └── logo.svg                 # Plugin logo
├── mcp.json                     # MCP server configuration
└── README.md
```

## License

Apache-2.0
