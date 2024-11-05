
# Argo CD CLI Guide

This guide provides an overview of how to use the Argo CD CLI for creating and managing applications in Argo CD, a declarative GitOps continuous delivery tool for Kubernetes.

---

## Table of Contents

- [Installation](#installation)
- [Login to Argo CD CLI](#login-to-argo-cd-cli)
- [Creating an Argo CD Application](#creating-an-argo-cd-application)
- [Common CLI Commands](#common-cli-commands)
  - [Syncing an Application](#syncing-an-application)
  - [Viewing Application Status](#viewing-application-status)
  - [Deleting an Application](#deleting-an-application)

---

## Installation

To install the Argo CD CLI, visit the [Argo CD installation documentation](https://argo-cd.readthedocs.io/en/stable/getting_started/).

For Linux/macOS:
```bash
curl -sSL -o /usr/local/bin/argocd https://github.com/argoproj/argo-cd/releases/download/<VERSION>/argocd-linux-amd64
chmod +x /usr/local/bin/argocd
```

For Windows, download the `.exe` file from the [release page](https://github.com/argoproj/argo-cd/releases).

---

## Login to Argo CD CLI

First, log in to your Argo CD instance using the Argo CD CLI:

```bash
argocd login <ARGOCD_SERVER> --username <USERNAME> --password <PASSWORD>
```

Replace `<ARGOCD_SERVER>` with your Argo CD server's address, `<USERNAME>` with your Argo CD username, and `<PASSWORD>` with your Argo CD password.

---

## Creating an Argo CD Application

To create an application in Argo CD using the CLI, use the following command:

```bash
argocd app create my-app   --repo https://gitlab.sananetco.com/devops-scenarios/gitops-example02.git   --path manifests   --dest-server https://kubernetes.default.svc   --dest-namespace default   --project default   --revision main   --sync-policy automated   --self-heal   --auto-prune
```

### Explanation of Flags

- `my-app`: The name of the application within Argo CD.
- `--repo`: Git repository URL containing the application manifests.
- `--path`: Path within the repository where the manifests are located.
- `--dest-server`: Kubernetes API server to which the app will be deployed.
- `--dest-namespace`: The namespace in Kubernetes where the application should be deployed.
- `--project`: Argo CD project to which the application belongs.
- `--revision`: Branch or tag to deploy (e.g., `main`).
- `--sync-policy automated`: Enables automatic synchronization of the application.
- `--self-heal`: Enables self-healing to revert manual changes.
- `--auto-prune`: Deletes resources not defined in the Git repository



# Argo CD CLI Guide

This guide provides an overview of how to use the Argo CD CLI for creating and managing applications in Argo CD, a declarative GitOps continuous delivery tool for Kubernetes.

---

## Table of Contents

- [Installation](#installation)
- [Login to Argo CD CLI](#login-to-argo-cd-cli)
- [Creating an Argo CD Application](#creating-an-argo-cd-application)
- [Common CLI Commands](#common-cli-commands)
  - [Syncing an Application](#syncing-an-application)
  - [Viewing Application Status](#viewing-application-status)
  - [Deleting an Application](#deleting-an-application)

---

## Installation

To install the Argo CD CLI, visit the [Argo CD installation documentation](https://argo-cd.readthedocs.io/en/stable/getting_started/).

For Linux/macOS:
```bash
curl -sSL -o /usr/local/bin/argocd https://github.com/argoproj/argo-cd/releases/download/<VERSION>/argocd-linux-amd64
chmod +x /usr/local/bin/argocd
```

For Windows, download the `.exe` file from the [release page](https://github.com/argoproj/argo-cd/releases).

---

## Login to Argo CD CLI

First, log in to your Argo CD instance using the Argo CD CLI:

```bash
argocd login <ARGOCD_SERVER> --username <USERNAME> --password <PASSWORD>
```

Replace `<ARGOCD_SERVER>` with your Argo CD server's address, `<USERNAME>` with your Argo CD username, and `<PASSWORD>` with your Argo CD password.

---

## Creating an Argo CD Application

To create an application in Argo CD using the CLI, use the following command:

```bash
argocd app create my-app   --repo https://gitlab.sananetco.com/devops-scenarios/gitops-example02.git   --path manifests   --dest-server https://kubernetes.default.svc   --dest-namespace default   --project default   --revision main   --sync-policy automated   --self-heal   --auto-prune
```

### Explanation of Flags

- `my-app`: The name of the application within Argo CD.
- `--repo`: Git repository URL containing the application manifests.
- `--path`: Path within the repository where the manifests are located.
- `--dest-server`: Kubernetes API server to which the app will be deployed.
- `--dest-namespace`: The namespace in Kubernetes where the application should be deployed.
- `--project`: Argo CD project to which the application belongs.
- `--revision`: Branch or tag to deploy (e.g., `main`).
- `--sync-policy automated`: Enables automatic synchronization of the application.
- `--self-heal`: Enables self-healing to revert manual changes.
- `--auto-prune`: Deletes resources not defined in the Git repository

## Common CLI Commands

Here are some common Argo CD CLI commands for managing applications:

### Listing Applications

To list all applications managed by Argo CD:

```bash
argocd app list
```

This command displays a list of applications with details like the name, project, and sync status.

### Syncing an Application

To manually sync an application to ensure its state matches the Git repository:

```bash
argocd app sync my-app
```

Replace `my-app` with the name of your application. This command will pull the latest manifests from the Git repository and apply them to the cluster.

### Viewing Application Status

To view the current status of an application:

```bash
argocd app get my-app
```

This command provides detailed information about the application, including its health, sync status, and resources.

### Deleting an Application

To delete an application from Argo CD:

```bash
argocd app delete my-app
```

Replace `my-app` with the name of your application. This will remove the application from Argo CD, but it won’t delete the actual Kubernetes resources by default unless you specify `--cascade`.

---

These commands provide basic functionality for managing applications in Argo CD via the CLI. For more details, refer to the [Argo CD CLI documentation](https://argo-cd.readthedocs.io/en/stable/user-guide/commands/argocd/).
