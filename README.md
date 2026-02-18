# LocalStack Cursor Plugin

The official [LocalStack](https://localstack.cloud) plugin for [Cursor](https://cursor.com) — brings local AWS cloud development directly into your IDE.

## What's included

### MCP Server

The plugin bundles the [LocalStack MCP Server](https://github.com/localstack/localstack-mcp-server) (`@localstack/localstack-mcp-server`), giving the AI agent direct access to:

| Tool | Description |
|------|-------------|
| **Container management** | Start, stop, restart, and check status of LocalStack |
| **Infrastructure deployment** | Deploy CDK, Terraform, and CloudFormation stacks to LocalStack |
| **Log analysis** | Analyze LocalStack logs, filter by service, and identify errors |
| **AWS CLI** | Run AWS CLI commands against LocalStack |
| **IAM Policy Analyzer** | Enforce and auto-generate least-privilege IAM policies (Pro) |
| **Cloud Pods** | Save and load state snapshots for reproducible environments (Pro) |
| **Chaos Engineering** | Inject faults and latency into AWS services (Pro) |

### Skills

Six skills provide contextual knowledge for common LocalStack workflows:

| Skill | Description |
|-------|-------------|
| **localstack** | Container lifecycle management (start, stop, status, config) |
| **localstack-deploy** | IaC deployment with Terraform, CDK, CloudFormation, and Pulumi |
| **localstack-state** | State management with local snapshots and Cloud Pods |
| **localstack-logs** | Log analysis, debugging, and health checks |
| **localstack-iam** | IAM policy enforcement, analysis, and least-privilege generation |
| **localstack-extensions** | Extension management and custom extension development |

## Installation

Install from the [Cursor Marketplace](https://cursor.com/marketplace) by searching for **LocalStack**. You can also install it via Cursor CLI:

```bash
cursor plugins install localstack-cursor-plugin
```

## Configuration

### LocalStack Auth Token

To enable Pro features (IAM Policy Analyzer, Cloud Pods, Chaos Engineering), set your `LOCALSTACK_AUTH_TOKEN` as an environment variable with your MCP server configuration.

### LocalStack-specific configuration

To configure any other LocalStack-specific configuration, set the corresponding environment variable in your MCP server configuration. Refer to the [LocalStack configuration documentation](https://docs.localstack.cloud/aws/capabilities/config/configuration/) for more details.

## Project structure

```
localstack-cursor-plugin/
├── .cursor-plugin/
│   └── plugin.json          # Plugin manifest
├── skills/
│   ├── localstack-lifecycle/ # Container lifecycle management
│   ├── iac-deployment/       # Terraform, CDK, CloudFormation, Pulumi
│   ├── state-management/     # Snapshots and Cloud Pods
│   ├── logs-analysis/        # Log analysis and debugging
│   ├── iam-policy-analyzer/  # IAM enforcement and policy generation
│   └── localstack-extensions/# Extension management
├── assets/
│   └── logo.svg              # Plugin logo
├── mcp.json                  # MCP server configuration
└── README.md
```

## License

Apache-2.0
