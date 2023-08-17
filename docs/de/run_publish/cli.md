# SubQuery CLI

**Most customers use the [@subql/cli](https://github.com/subquery/subql/tree/main/packages/cli) to just initialise, build, and run their projects locally, however the CLI can be used to do a whole lot more!**

You can use the CLI to do the following:

- [Create a new project](#create-a-new-project) on the SubQuery Managed Service
- [Deploy a new version](#deploy-a-new-version-of-your-project) of your SubQuery project to the Managed Service
- [Promote a staging deployment](#promote-a-staging-deployment-to-production-slot) to the production slot in the SubQuery Managed Service
- and more! Type `subql help` to read the docs

::: warning This document may be outdated
The commands and parameters shown here may change, we suggest reviewing the current command and parameter list by using the `--help` command with your CLI
:::

## Installation

Install SubQuery CLI globally on your terminal by using Yarn or NPM:

::: code-tabs
@tab:active npm

```bash
npm install -g @subql/cli
```

@tab yarn

```shell
yarn global add @subql/cli
```

:::

You can then run help to see available commands and usage provided by CLI:

```shell
subql help
```

### Bereiten Sie Ihr SUBQL_ACCESS_TOKEN vor

- Step 1: Go to [SubQuery Managed Service](https://managedservice.subquery.network/) and log in.
- Schritt 2: Klicken Sie oben rechts im Navigationsmenü auf Ihr Profil und dann auf **_Token aktualisieren_**.
- Schritt 3: Kopieren Sie das generierte Token.
- Schritt 4: So verwenden Sie dieses Token:
  - Variante 1: Fügen Sie SUBQL_ACCESS_TOKEN zu Ihren Umgebungsvariablen hinzu. `EXPORT SUBQL_ACCESS_TOKEN=<token>` (Windows) oder `export SUBQL_ACCESS_TOKEN=<token>` (Mac/Linux)
  - Variante 2: Demnächst wird `subql/cli` das lokale Speichern Ihres SUBQL_ACCESS_TOKEN unterstützen.

## Usage in GitHub Actions

With the introduction of the deployment feature for the CLI, we've added a **Default Action Workflow** to [the starter project in GitHub](https://github.com/subquery/subql-starter/blob/main/Polkadot/Polkadot-starter/.github/workflows/cli-deploy.yml) that will allow you to publish and deploy your changes automatically:

Please review the documentation on how to [deploy a new version of your project using GitHub actions](./publish.md#using-github-actions).

## Erstellen Sie ein neues Projekt

The CLI allows you to create a brand new project in the SubQuery Managed Service. It supports both interactive and non-interactive methods.

```shell
// Creating a project using the interactive method of the CLI
$ subql project:create-project

// OR using non-interactive method of the CLI, it will prompt you if the required fields are missing
$ subql project:create-project
    --apiVersion=apiVersion    [default: 2] Enter api version
    --description=description  Enter description
    --gitRepo=gitRepo          Enter git repository
    --logoURL=logoURL          Enter logo URL
    --org=org                  Enter organization name
    --projectName=projectName  Enter project name
    --subtitle=subtitle        Enter subtitle
```

## Deploy a New Version of your Project

Using the CLI, you can deploy a new version of your SubQuery project to the Managed Service. It supports both interactive and non-interactive methods. You may want to run this command after you delete the target deployment slot (staging or primary).

::: tip Note
We suggest using the `--useDefaults` command for best results.
:::

```shell
// Deploy using the interactive method of the CLI
$ subql deployment:deploy

// OR using non-interactive method of the CLI, it will prompt you if the required fields are missing
$ subql deployment:deploy
  -d, --useDefaults                Use default values for indexerVersion, queryVersion, dictionary, endpoint
  --dict=dict                      Enter dictionary
  --endpoint=endpoint              Enter endpoint
  --indexerVersion=indexerVersion  Enter indexer-version
  --ipfsCID=ipfsCID                Enter IPFS CID
  --org=org                        Enter organization name
  --projectName=projectName        Enter project name
  --queryVersion=queryVersion      Enter query-version
  --type=(stage|primary)           [default: primary]
```

## Promote a Staging Deployment to Production Slot

This command will promote a staging deployment to the production slot in the SubQuery Managed Service.

```shell
// Promote using the interactive method of the CLI
$ subql deployment:promote

// OR using non-interactive method of the CLI, it will prompt you if the required fields are missing
$ subql deployment:promote
  --deploymentID=deploymentID  Enter deployment ID
  --org=org                    Enter organization name
  --project_name=project_name  Enter project name
```

## Delete an Existing Deployment of your Project

This is a command commonly run to clear out data from an existing deployment slot (e.g. the staging slot) before you do a fresh deployment.

```shell
// Delete slot using the interactive method of the CLI
$ subql deployment:delete

// OR using non-interactive method of the CLI, it will prompt you if the required fields are missing
$ subql deployment:delete
  --deploymentID=deploymentID  Enter deployment ID
  --org=org                    Enter organization name
  --project_name=project_name  Enter project name
```
