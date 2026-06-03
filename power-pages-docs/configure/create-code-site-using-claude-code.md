---
title: Get started with the Power Pages plugin for GitHub Copilot CLI and Claude Code
description: This page provides a walk-through on how to create, customize, and deploy single-page applications for Microsoft Power Pages using agentic AI coding tool.
author: neerajnandwana-msft
ms.topic: tutorial
ms.date: 05/28/2026
ms.author: nenandw
ms.reviewer: smurkute
contributors:
- neerajnandwana-msft
- shwetamurkute
- joshuapartlow
---

#  Get started with the Power Pages plugin for GitHub Copilot CLI and Claude Code

The Power Pages plugin for [GitHub Copilot CLI](https://github.com/features/copilot/cli/) and [Claude Code](https://claude.ai/code) provides an AI-assisted workflow for creating, deploying, and managing modern [*single-page application (SPA)*](/power-pages/configure/create-code-sites) sites on Power Pages. Instead of manually scaffolding projects, writing boilerplate API code, and configuring permissions, describe what you want in natural language, and the plugin handles the implementation.

The plugin supports the full site development lifecycle through conversational skills, from scaffolding a new site to deploying it, setting up Dataverse data models, and configuring authentication.

> [!IMPORTANT]
> - [Review agent proposals before approving](#review-agent-proposals-before-approving)

## Prerequisites

Before you begin, verify that you have the required software and permissions.

### Software requirements

| Component | Minimum version | More information |
|-----------|-----------------|------------------|
| Node.js | 18.0 or later | [Download Node.js](https://nodejs.org/) |
| Power Platform CLI (PAC CLI) | 2.6.3 or later (required for server logic) | [Install PAC CLI](/power-platform/developer/cli/introduction) |
| Azure CLI | Latest | [Install Azure CLI](/cli/azure/install-azure-cli) |
| GitHub Copilot CLI or Claude Code | Latest | [GitHub Copilot CLI](https://github.com/features/copilot/cli/) or [Claude Code](https://claude.ai/code) |
| Visual Studio Code and Power Platform Tools extension (Optional) | Latest | [Download VS Code](https://code.visualstudio.com/) and [Install Power Platform Tools](vs-code-extension.md#visual-studio-code-extension-for-power-pages) |

You also need:

- A Power Platform environment with Power Pages enabled.
- An authenticated PAC CLI session connected to your target environment. Run [`pac auth create`](/power-platform/developer/cli/reference/auth#pac-auth-create) if you didn't connect yet.
- An Azure CLI session signed in to the same tenant. Run [`az login --allow-no-subscriptions`](/cli/azure/reference-index#az-login) to authenticate.

**Verify authentication:**

Verify you're authenticated by using the [`pac auth list`](/power-platform/developer/cli/reference/auth#pac-auth-list) command.

```powershell
pac auth list           # Should show authenticated profile
```

If you're not authenticated, run this command:

```powershell
pac auth create --environment <Instance url>        # Authenticate to Power Platform
```

> [!TIP]
> To get the instance URL, go to Power Pages home, select the **Settings** icon in the upper-right corner, and then select **Session details**.

## Install the plugin

Install the Power Pages plugin from the marketplace. If you use GitHub Copilot CLI, see the [Copilot CLI extensions documentation](https://docs.github.com/copilot/concepts/agents/copilot-cli/about-copilot-cli) for equivalent install steps. The following commands use Claude Code syntax.

### Quick install (recommended)

Run the installer to set up all plugins with autoupdate enabled:

**Windows (PowerShell)**:

```powershell
iwr https://raw.githubusercontent.com/microsoft/power-platform-skills/main/scripts/install.js -OutFile install.js; node install.js; del install.js
```

**macOS/Linux/Windows (cmd):**

```bash
curl -fsSL https://raw.githubusercontent.com/microsoft/power-platform-skills/main/scripts/install.js | node
```

The installer automatically:

- Installs the `pac` CLI if it isn't already installed.
- Detects available tools, such as Claude Code and GitHub Copilot CLI.
- Registers the plugin marketplace and installs all listed plugins.
- Enables autoupdate so plugins stay current.

After installation, restart Claude Code or GitHub Copilot CLI to access the plugin's skills as slash commands in your agent session.

### Install from marketplace

1. Open Claude Code in your terminal.

1. Add the Microsoft marketplace:

   ```bash
   /plugin marketplace add microsoft/power-platform-skills
   ```

1. Install the Power Pages plugin:

   ```bash
   /plugin install power-pages@power-platform-skills
   ```

After you install the plugin, restart Claude Code or GitHub Copilot CLI to access the plugin's skills as slash commands in your agent session.

> [!TIP]
> To automatically receive updates to the marketplace and skills, turn on auto-update. Use the `/plugin` command, go to **Marketplaces**, choose the marketplace, and turn on auto-update.

## Skills overview

The plugin provides skills that cover the full lifecycle of a Power Pages site. Invoke each skill conversationally, either as a slash command or by describing what you want to do.

| Skill | Command | What it does |
|---|---|---|
| Create site | `/create-site` | Scaffolds a site, applies your design direction, and builds pages and components |
| Deploy site | `/deploy-site` | Builds the project and uploads it to Power Pages by using PAC CLI |
| Activate site | `/activate-site` | Provisions a website record and assigns a public URL |
| Set up data model | `/setup-datamodel` | Creates Dataverse tables, columns, and relationships |
| Add sample data (optional) | `/add-sample-data` | Populates Dataverse tables with realistic test records |
| Integrate Web API | `/integrate-webapi` | Generates typed API client code, services, and table permissions |
| Set up authentication | `/setup-auth` | Adds sign-in, sign-out, and role-based access control. Supports Microsoft Entra ID, Microsoft Entra External ID, OpenID Connect, SAML 2.0, WS-Federation, Microsoft account, Facebook, Google, and local username and password authentication, including multi-provider configurations |
| Create web roles | `/create-webroles` | Generates web role YAML files for user access management |
| Add server logic | `/add-server-logic` | Generates secure server-side JavaScript endpoints for validation, external API calls, secret management, and data operations |
| Add cloud flow | `/add-cloud-flow` | Integrates existing Power Automate cloud flows into your site for approval workflows, notifications, and scheduled automation |
| Integrate backend | `/integrate-backend` | Analyzes your prototype, determines the right approach (Web API, Server Logic, or cloud flow) for each feature, and orchestrates the complete build sequence |
| Add SEO | `/add-seo` | Generates robots.txt, sitemap.xml, and meta tags |
| Run security review | `/security-review` | Orchestrates the focused security skills and consolidates every finding into a single HTML report. Covers code, dependencies, deployed-site scan, browser headers, web application firewall, table permissions, and authentication configuration |
| Scan source code | `/scan-code` | Runs static analysis and dependency scanning on local source files; surfaces findings across code patterns, vulnerable packages, hardcoded secrets, and license issues |
| Scan deployed site | `/scan-site` | Starts a server-side security scan against the live site, fetches the latest report, and groups findings by severity |
| Manage browser security headers | `/manage-headers` | Inspects and configures the HTTP security headers a site sends to browsers — Content Security Policy, frame and clickjacking protection, cross-origin sharing, cookie behavior, and related site settings |
| Manage web application firewall | `/manage-firewall` | Inspects and configures the web application firewall (WAF) on a production site: enables protection, adds or removes IP blocks, country blocks, path blocks, and rate limits |
| Audit table permissions | `/audit-permissions` | Audits existing table permissions against site code and Dataverse metadata; produces an HTML report grouped by severity with suggested fixes |
| Plan deployment | `/plan-alm` | Detects project state, gathers your promotion strategy, renders a visual plan, and orchestrates the other application lifecycle management (ALM) skills in the right order |
| Author solution | `/setup-solution` | Creates a publisher and solution, adds Power Pages components, classifies site settings, and proposes environment variables and Azure Key Vault secrets |
| Set up pipeline host | `/ensure-pipelines-host` | Provisions or detects a host environment for Power Platform Pipelines |
| Set up pipeline | `/setup-pipeline` | Registers a pipeline definition in Dataverse and binds promotion stages to target environments |
| Deploy through pipeline | `/deploy-pipeline` | Triggers a pipeline deployment for a target stage with per-stage environment variable overrides |
| Force-link environment | `/force-link-environment` | Reassigns a target environment to a new Power Platform Pipelines host when a host conflict blocks deployment |
| Export solution | `/export-solution` | Exports the solution as a managed or unmanaged zip, with a completeness check before export |
| Import solution | `/import-solution` | Imports a solution zip on a target environment, staged or direct |
| Test site | `/test-site` | Verifies a deployed site with a browser-based test: page crawl, role-based access checks, and Web API verification |
| Diagnose deployment | `/diagnose-deployment` | Matches deployment failures against a catalog of known errors and proposes a fix |

## Typical workflow

A common end-to-end workflow follows this sequence:

1. **/create-site**         :  Scaffold, design, and build pages
1. **/deploy-site**         :  Upload to your Power Pages environment
1. **/activate-site**       :  Set up a public URL
1. **/setup-datamodel**     :  Create Dataverse tables
1. **/add-sample-data**     :  Populate tables with test records
1. **/integrate-webapi**    :  Generate API client code and configure permissions
1. **/create-webroles**     :  Define access roles
1. **/setup-auth**          :  Add sign-in, sign-out, and role-based UI
1. **/add-server-logic**    :  Add secure server-side endpoints
1. **/add-cloud-flow**      :  Integrate existing Power Automate flows
1. **/add-seo**             :  Search engine optimization
1. **/deploy-site**         :  Push final changes live
1. **/security-review**     :  Run an end-to-end security review before going to production
1. **/plan-alm**            :  Promote your site to test and production environments

> [!TIP]
> - You don't need to follow this exact order. Each skill checks its own prerequisites and tells you if something is missing. For example, you can run `/setup-auth` before `/integrate-webapi` if your site needs authentication first.
> - If you're not sure which approach to use for each feature, run `/integrate-backend` instead of steps 4 through 10 individually. It analyzes your prototype, determines whether each feature needs Web API, Server Logic, or a cloud flow, and orchestrates the skills in the correct order.

## Build your Power Pages site

This walkthrough covers the full lifecycle of building a Power Pages site with the plugin, from scaffolding through deployment. Each step describes what you say and what the plugin does in response.

### Step 1: Create your site

Describe the site you want in natural language: what it's for, what pages it needs, and any design preferences like color scheme, layout style, or fonts. Run `/create-site` or just describe your site and the plugin recognizes the intent.

If you don't specify a framework, the plugin asks you to pick one (React, Vue, Angular, or Astro), then:

1. Scaffolds the project from a template and applies your site name, colors, and design tokens.
1. Installs dependencies, starts a development server, and opens a live browser preview.
1. Builds out each page, component, and route you requested with relevant images.
1. Creates git commits at significant milestones so you have built-in rollback history.

### Step 2: Deploy your site

Run `/deploy-site` to upload your site to Power Pages. The plugin:

1. Verifies that PAC CLI is installed and your authentication session is active.
1. Confirms the target environment with you before proceeding.
1. Runs a production build and uploads the compiled output.
1. Creates a deployment artifacts directory if one doesn't already exist.

> [!NOTE]
> If your environment blocks certain file attachments, the plugin detects the problem and provides instructions to resolve it.

### Step 3: Activate your site

Run `/activate-site` to make the site publicly accessible. The plugin:

1. Suggests a subdomain based on your site name and lets you customize it.
1. Provisions a website record through the Power Platform API.
1. Polls until the site is live and returns the public URL.

At this point, you have a working site at a public URL. The remaining steps add data, authentication, and SEO. Skip any steps that don't apply to your site.

### Step 4: Set up your data model

Run `/setup-datamodel` to create the Dataverse tables your site needs. If you already have an ER diagram or specific schema, provide it directly instead of having the agent analyze your code.

The plugin spawns a **Data Model Architect** agent that:

1. Analyzes your site's code to determine what data the pages and components require.
1. Queries your Dataverse environment for existing tables to avoid duplicates.
1. Proposes a data model with tables, columns, data types, and relationships, visualized as an ER diagram.

**You review and approve the proposal.** The plugin doesn't create anything until you confirm. After approval, the plugin creates the tables and columns through API calls and saves a manifest file that Steps 5 and 6 use.

### Step 5: Add sample data (Optional)

Run `/add-sample-data` to populate your tables with test records. This step requires the data model from Step 4.

The plugin performs the following actions:

1. Reads the manifest to understand your tables, columns, and relationships.
1. Generates contextually appropriate values for each column type, such as realistic emails, plausible dates, and formatted currency amounts.
1. Inserts records in dependency order (parent tables before child tables) and refreshes authentication tokens automatically during bulk inserts.

### Step 6: Integrate with the Dataverse Web API

Run `/integrate-webapi` to replace mock data with live Dataverse queries. This step requires the data model from Step 4.

The plugin performs the following actions:

1. Scans your codebase for components that use mock data, placeholder fetch calls, or hardcoded arrays. It maps these components to your Dataverse tables.
1. Spawns a **Web API Integration** agent for each table that generates:
   - A shared API client with anti-forgery token management and retry logic.
   - TypeScript entity types and domain mappers.
   - A CRUD service layer.
   - Framework-specific patterns, such as React hooks, Vue composables, or Angular services.
1. Spawns a **Permissions Architect** agent that proposes table permissions and site settings.

**You review and approve the permissions proposal.** The plugin doesn't create any configuration files until you confirm.

### Step 7: Create web roles

Run `/create-webroles` to define user access roles. The plugin:

1. Queries your environment for existing web roles to avoid duplicates.
1. Generates role definitions with unique identifiers.
1. Enforces that each site has at most one anonymous role and one authenticated role.

### Step 8: Set up authentication

Run `/setup-auth` to add sign-in, sign-out, and role-based access control to your site. The plugin supports the following identity providers, and you can configure one provider or several at the same time.

| Provider | Best for |
|---|---|
| Microsoft Entra External ID (recommended for customer-facing sites) | Public sites and customer portals with self-service sign-up. |
| Microsoft Entra ID | Internal employee portals or business-to-business (B2B) partner sites. Power Pages automatically configures the site's parent tenant, so you don't need to enter tenant information. |
| Microsoft, Facebook, Google | Social sign-in for consumer audiences. |
| Local authentication | Username and password sign-in. Not recommended and is configured only when you explicitly request it. |

For more information about supported providers, including protocols and configuration considerations, see [Overview of authentication in Power Pages](../security/authentication/index.md).

The plugin:

1. Analyzes your site (purpose, pages, audience) and proposes a sensible default. For example, the plugin proposes Microsoft Entra External ID with open registration for a customer-facing site, or Microsoft Entra ID with invitation-only registration for an internal portal. You accept the recommendation or pick your own providers.
1. For each provider, walks you through every prerequisite step in the identity provider's admin center, such as creating tenants, registering apps, creating user flows, and capturing client IDs and redirect URIs. The plugin validates each value you paste back into the conversation, and computes the exact redirect URI for your site so that the value pasted into the app registration matches the value written into site settings.
1. Asks how user profile data should flow from the identity provider into the Dataverse contact record (claims mapping), whether to sync on every sign-in or first sign-in only, and whether to auto-link external sign-ins to existing contacts by email.
1. Generates the authentication service, type declarations, role-based authorization utilities (`hasRole`, `RequireAuth`, `RequireRole`), a session keepalive hook that prevents SPA sessions from silently expiring, and a sign-in/sign-out UI component integrated with your site layout. The plugin uses your framework's patterns throughout, such as React hooks, Vue composables, Angular services, or Astro components.
1. When more than one provider is configured, generates a `/login` page rendered in your chosen layout: horizontal row, vertical stack, primary spotlight, or tabbed.
1. Writes the matching site settings under `.powerpages-site/site-settings/` for each provider, registration mode, claims mapping, and optional feature.

The plugin also configures the following optional features when you turn them on:

- **Terms and conditions**: A `/terms` SPA page users must accept before completing sign-in, plus the matching site setting and content snippets.
- **User profile page**: A `/user-profile` SPA page where signed-in users edit their contact information through the Power Pages Web API.
- **Federated sign-out**: Also signs out the user at the identity provider when they sign out of the site, for shared-device or regulated scenarios.

> [!TIP]
> To add a second identity provider to an existing site, run `/setup-auth` again. The plugin detects what's already configured and offers to add a new provider without overwriting the existing ones. This approach is useful for incremental scenarios, such as starting with Microsoft Entra External ID and later adding Google for social sign-in.

> [!NOTE]
> Client-side authorization (`RequireAuth`, `RequireRole`, `hasRole`) is for user experience only. It controls what the user sees. Server-side table permissions configured by `/integrate-webapi` enforce actual security.

### Step 9: Add server logic

Run `/add-server-logic` to add secure server-side endpoints to your site. Use [Server Logic](server-logic-overview.md) when your site needs logic that can't run in the browser, such as external API calls, server-side validation, secret management, or cross-entity data operations.

> [!IMPORTANT]
> Server logic support requires PAC CLI version 2.6.3 or later. Use the [quick install script](#quick-install-recommended) to update to the latest version.

Describe what you need in plain language, and the plugin:

1. Spawns a **Server Logic Architect** agent that analyzes your use case and classifies its complexity.
1. Proposes an endpoint design, security configuration, and any required table permissions for your review.
1. After you approve, generates the server-side JavaScript endpoint at `/_api/serverlogics/<name>`.
1. Creates a typed client-side service to invoke the endpoint from your components.
1. Updates your components to call the new service.
1. Configures web role assignments and table permissions for the endpoint.

**You review and approve the proposal.** No code is generated until you confirm.

Common use cases:

- **Connect to external services.** Call REST APIs, Azure Functions, or third-party services without exposing credentials. ([Tutorial: interact with external services](server-logic-external-services.md))
- **Perform secure data operations.** Query, update, or delete Dataverse records with consistent server-side validation. ([Tutorial: interact with Dataverse tables](server-logic-operations.md))
- **Run custom logic.** Aggregate data across tables, enforce business rules, or compute derived values before returning results to the client.
- **Manage secrets server-side.** Store credentials and API keys on the server, never in client code. ([Tutorial: interact with Microsoft Graph and SharePoint](server-logic-graph-sharepoint.md))

> [!NOTE]
> Run `/add-server-logic` once per use case. For example, if your site needs both an inventory validation endpoint and a global search endpoint, run the skill twice.

### Step 10: Integrate cloud flows

Run `/add-cloud-flow` to integrate existing Power Automate cloud flows into your site. This skill connects your Power Pages site to flows that you already created in Power Automate. It doesn't create new cloud flows.

The plugin:

1. Registers the existing cloud flow with your site.
1. Generates client-side code to trigger the flow from your pages.
1. Handles asynchronous workflow state and callback patterns.
1. Wires up data exchange between the page and the flow.

Use `/add-cloud-flow` for approval workflows, email notifications, scheduled jobs, and event-driven automation that are better handled by Power Automate than by server-side endpoints.

### Alternative: Use /integrate-backend to plan the full service layer

If you're not sure which features need Web API, Server Logic, or a cloud flow, run `/integrate-backend` instead of manually running steps 4 through 10. This skill acts as an orchestrator that:

1. Analyzes your prototype to identify all features that need a service layer.
1. Classifies each feature into the right approach: Web API for standard CRUD, Server Logic for server-side validation and external APIs, or cloud flow for approval workflows and automation.
1. Proposes a sequenced execution plan with all skills, dependencies, and configurations.
1. After you approve, orchestrates the skills in the correct order.

The plan is persistent, resumable, and editable. Stop after any step to review generated code or test the site, and pick up where you left off by running `/integrate-backend` again.

### Step 11: Add SEO

Run `/add-seo` to optimize your site for search engines. The plugin:

1. Discovers routes from your framework's router configuration.
1. Generates search engine directives and a sitemap for all discovered routes.
1. Adds meta tags: viewport, charset, description, Open Graph, Twitter Card, and favicon references.

### Step 12: Deploy the final site

If you perform any optional steps, run `/deploy-site` again to push the changes live. The plugin runs a production build and uploads the site along with all deployment artifacts (table permissions, site settings, web roles, server logic files) to your Power Pages environment.

### Step 13: Run a security review

Run `/security-review` to perform an end-to-end security review of your site before going to production. The skill orchestrates the focused security skills and consolidates every finding into a single HTML report at `docs/security-review-<timestamp>.html`.

The plugin asks one plain-language question about your goal and picks the matching set of focused skills:

| Goal | What it checks |
|---|---|
| **Code and config** | Source code, dependencies, table permissions, and authentication configuration. Works on local files only - no deployment required. |
| **Release readiness** (recommended) | Full review before publishing. Runs every focused skill: code and dependencies, deployed-site scan, browser security headers, web application firewall, table permissions, and authentication. |
| **Deployed site** | Live deployed-site scan only. Useful for ongoing monitoring of a published site. |

After you confirm, the plugin runs the matching focused skills in parallel and writes their findings to a single report:

- **`/scan-code`**: Runs static analysis (opengrep) and dependency scanning (trivy) on local source files. Surfaces code patterns, vulnerable packages, hardcoded secrets, and license issues. If either tool isn't installed, the skill offers a manual code review as a fallback.
- **`/scan-site`**: Starts a server-side security scan against the live site and fetches the latest report. Scan duration depends on site size - small sites finish in minutes, large sites can take hours. Findings are grouped by severity. Requires a deployed site.
- **`/manage-headers`**: Inspects the HTTP security headers configured under `.powerpages-site/site-settings/`: Content Security Policy, X-Frame-Options, CORS, cookie SameSite, and related settings. Identifies missing or weak values and proposes recommended defaults.
- **`/manage-firewall`**: Inspects the web application firewall (WAF) for the production site, including managed-rule state and custom rules (IP blocks, country blocks, path blocks, rate limits). Available only on production sites in supported regions; the skill detects and reports eligibility issues.
- **`/audit-permissions`**: Audits existing table permissions against site code and Dataverse metadata. Surfaces missing permissions, overly permissive roles, unused permissions, and YAML schema problems.

The consolidated report groups findings by section, opens in your default browser, and includes plain-language remediation guidance. From the chat, the plugin then offers to walk through fixes - choose a finding and the plugin invokes the matching focused skill interactively to apply the change.

> [!NOTE]
> The security review never applies changes automatically. Each focused skill runs in read-only review mode during the consolidated run. To apply a fix, the plugin invokes the matching skill interactively after you pick the action.

> [!TIP]
> You can also run any focused skill on its own:
>
> - Run `/scan-code` during development to catch code-level issues early.
> - Run `/manage-headers` to fix a specific Content Security Policy error or set up CORS.
> - Run `/manage-firewall` to add a rate limit on the sign-in page or block traffic by country.
> - Run `/audit-permissions` after changing table permissions to verify they still match site code.
> - Re-run `/security-review` with the **Deployed site** goal to monitor a production site over time.

### Verify your site

After you complete the skills, verify your Power Pages site works correctly.

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).
1. Locate your site in the **Active sites** list.
1. Preview your site on desktop by using the **Preview** option.
1. Test the functionality.

## Promote your site across environments

After your site works in your development environment, use the application lifecycle management (ALM) skills to promote it to test and production environments. The plugin packages your site as a [Power Platform solution](/power-platform/alm/solution-concepts-alm), identifies values that vary across environments, and deploys the solution through [Power Platform Pipelines](/power-platform/alm/pipelines) or through manual export and import.

To use the ALM skills, you also need at least one target Power Platform environment (test, production, or both). To use the optional Azure Key Vault flow for secrets, you also need permission to create a key vault in your Azure subscription.

### Plan the deployment

Run `/plan-alm` to start. `/plan-alm` is the entry point for ALM and orchestrates the other ALM skills, so you typically don't run them directly. The plugin:

1. Detects the current state of your project, solution, and target environments.
1. Asks about your promotion strategy (Power Platform Pipelines or manual export and import), the target stages, and any constraints to apply.
1. Generates a visual plan at `docs/alm-plan.html` that shows every action it intends to take.
1. Waits for your approval before running any downstream skill.

The plan persists to disk, so each downstream skill reads from and writes to the same persisted plan. If a phase fails, run `/plan-alm` again and it resumes from where it stopped.

### Author the solution

Run `/setup-solution` to package your site as a Power Platform solution. The plugin:

1. Creates a publisher and solution, then adds your Power Pages components: the site, web roles, server logic endpoints, cloud flow registrations, and OAuth provider settings.
1. Classifies each site setting by sensitivity and proposes [environment variables](environment-variables-for-site-settings.md) for values that vary across environments.
1. Offers to provision an [Azure Key Vault](/azure/key-vault/general/overview) and store credential-type values, such as connection strings and API keys, in it.
1. Runs in sync mode when a solution already exists for your site, to reconcile components without creating a new solution.

**You review and approve the proposal.** The plugin doesn't create any configuration until you confirm.

> [!TIP]
> If your solution is too large or entangled to deploy reliably, the plugin recommends a split and proposes where to split it. Confirm the split before changes apply.

### Deploy with Power Platform Pipelines

If you chose Power Platform Pipelines as your promotion strategy, the plugin runs these skills:

1. `/ensure-pipelines-host` provisions or detects a host environment for Power Platform Pipelines. The skill picks the lowest-cost option available for your tenant: a free platform host, the Pipelines app on an existing environment, or a custom host.
1. `/setup-pipeline` registers a pipeline definition in Dataverse, configures the stages you chose, and binds each stage to a target environment.
1. `/deploy-pipeline` triggers a deployment for a stage, applies per-stage environment variable overrides through `deploymentSettings.json`, and tracks state in a deployment ledger.

If a deployment fails because the target environment is already linked to a different Power Platform Pipelines host, the plugin can run `/force-link-environment` to reassign it. The action requires your explicit consent and is reversible.

### Deploy with manual export and import

If you chose the manual path, the plugin runs:

1. `/export-solution` to export the solution as a managed or unmanaged ZIP, with a completeness check before export.
1. `/import-solution` to import the ZIP on the target environment, either staged to verify dependencies first or direct.

### Activate and validate the deployed site

After a successful deployment on the target environment, the plugin:

1. Runs `/activate-site` to provision the public URL on the target environment.
1. Runs `/test-site` to verify the deployment. The plugin uses a browser to crawl representative pages, run role-based access checks, verify `/_api/` calls, and capture response shapes from `/_api/serverlogics/` endpoints. The skill reports the result as `PASS`, `WARNINGS`, or `FAIL`, with per-check details linked from the plan.

If a step fails, the plugin runs `/diagnose-deployment`. The skill matches the failure against a catalog of known deployment errors, such as a stale manifest, missing dependencies, host conflicts, blocked JavaScript, or expired authentication, and proposes a concrete fix. The plugin never applies a fix without your consent.

> [!NOTE]
> Every ALM skill reads from and writes to artifacts on disk: the solution manifest, plan data, pipeline ledger, deployment ledger, and test results. The orchestration is resumable and auditable. To see what happened at any step, inspect the artifacts.

## Tips and best practices

The following tips help you get the most out of the plugin and the AI coding agent when building Power Pages sites.

### Watch terminal output for missing tools on first run

The plugin provides the skills and workflows, but the AI coding agent - GitHub Copilot CLI or Claude Code - executes the actual commands on your machine. When you use these tools for the first time, watch the terminal output closely. The AI coding agent runs commands and scripts behind the scenes, and some of these commands depend on tools that might not be installed on your machine. If a step fails, the terminal output usually shows which tool or command it couldn't find.

If you see an error like `command not found` or `is not recognized`, install the missing tool and re-trigger the workflow. The AI coding agent picks up where it left off after the tool is available.

### Review agent proposals before approving

The Data Model Architect and Web API Permissions Architect agents present proposals before making changes. Take the time to review these proposals carefully.

- **Data model proposals**: Check that table names, column types, and relationships match your business requirements. It's easier to adjust a proposal than to rename columns after data is already inserted.
- **Permissions proposals**: Verify that each role has the correct access level (create, read, update, delete) for each table. Overly permissive table permissions are a common security risk.

### Paste errors directly with context

When something fails, whether it's a build error, a deployment failure, or a runtime exception in the browser, copy the full error output. Paste it along with a brief description of what you were doing. The more context you provide, the faster the fix.

**Example: Build error**

```
I ran npm run build and got this error. Fix it.

error TS2339: Property 'jobTitle' does not exist on type 'JobPosting'.

  src/components/JobCard.tsx:24:31
    24   <Text>{posting.jobTitle}</Text>
                                 
```

> [!TIP]
> Include the file name, the command you ran, and what you expected to happen. The plugin uses this context to locate the problem and apply a targeted fix rather than guessing.

### Share Web API errors with the full request URL

A common issue after deploying is a `403` error from the Power Pages Web API when a column isn't enabled for API access. When you encounter this error, paste the **full API URL** and the **complete JSON error response**. The error message tells you exactly which table and column need to be fixed, and the plugin can update the table permission YAML and site settings for you.

**Example: Column not enabled for Web API (403)**

```
I'm getting a 403 error when the documents page loads. Here's the API call and the response. Fix the issue so this API works.

URL:
https://my-site.powerappsportals.com/_api/crd50_documents?$select=crd50_documentid,crd50_name,crd50_documentcategory,crd50_filetype,crd50_filesize,crd50_updateddate,crd50_description,_crd50_propertyid_value

Response:
{
  "error": {
    "code": "90040101",
    "message": "Attribute _crd50_propertyid_value in table crd50_document is not enabled for Web Api.",
    "innererror": {
      "code": "90040101",
      "message": "Attribute _crd50_propertyid_value in table crd50_document is not enabled for Web Api.",
      "type": "AttributePermissionIsMissing"
    }
  }
}
```

This error (`AttributePermissionIsMissing`) means the lookup column `_crd50_propertyid_value` exists in the Dataverse table but isn't listed in the table permission configuration for the Web API. The plugin resolves this error by adding the missing column to the table permission YAML in `.powerpages-site/table-permissions/` and redeploying.

> [!NOTE]
> Power Pages Web API requires every column returned by an API call to be explicitly listed in the table permission. [Lookup properties](/power-apps/developer/data-platform/webapi/web-api-properties#lookup-properties) (prefixed with `_` and suffixed with `_value`) are easy to miss because their API name differs from the column's logical name in Dataverse. When you see `AttributePermissionIsMissing`, always add that column to the table permission. Don't change the API query.

### Be specific about what you want

Vague requests produce vague results. Tell the plugin exactly what you need, including layout preferences, data fields, and behavior.

| Instead of | Try |
|---|---|
| "Make a page for jobs" | "Create a job listings page with a search bar at the top, filter chips for location and department, and a card grid showing title, company, salary range, and a posted date for each job" |
| "Fix the styling" | "The job cards stack vertically on desktop. Make them display in a three-column grid with 16px gap on screens wider than 768px" |
| "Add some data" | "Add 20 sample job postings across four departments (Engineering, Marketing, Sales, HR) with realistic titles, salary ranges between $60k-$180k, and posted dates in the last 30 days" |
| "Set up the API" | "Connect the JobListings component to the cr_jobposting Dataverse table. Replace the hardcoded array with a real API call that fetches title, department, salary, and posted date" |
| "Add login" | "Set up Microsoft Entra External ID sign-in with open registration, plus Google as a second provider. Show them as a horizontal row on the sign-in page." |

### Use screenshots for visual problems

When the site doesn't look right in the browser, take a screenshot and paste it directly into the conversation or provide a file path. Visual context helps identify layout, spacing, and styling problems that are hard to describe in text.

```
The header overlaps the hero section on mobile. Here's a screenshot:

[paste screenshot or provide path to screenshot file]

Fix the header so it doesn't overlap. It should be a fixed header with the content starting below it.
```

### Iterate in small steps

Instead of describing an entire site in one prompt, build incrementally. Start with the structure and layout, then add features one at a time. This approach gives you a chance to review and course-correct at each step.

```
Step 1: /create-site → Get the basic scaffold and layout right
Step 2: "Add a hero section to the home page with a search bar"
Step 3: "Add a job listings page with filter and sort"
Step 4: "Add a job detail page that shows full description"
Step 5: /setup-datamodel → Create tables now that you know the data shape
Step 6: /integrate-webapi → Wire up real data

```

> [!TIP]
> After each step, check the browser preview. If something isn't right, fix it before moving on. It's easier to fix problems in one component than to untangle problems across an entire site.

### Ask for an explanation before approving

When you're unsure about a proposed change, especially for permissions, data model modifications, or authentication configuration, ask the plugin to explain what it plans to do and why before approving.

```
Before you create the table permissions, explain what access each role will have and why. I want to understand the security implications.
```

### Run skills independently to recover from problems

If a skill fails partway through, you don't need to start over. Each skill runs independently and can pick up where it left off. For example, if `/integrate-webapi` fails on the third table, you can rerun it and it detects the work already completed.

```
/integrate-webapi failed while processing the cr_applications table. Here's the error: [paste error]. Resume the integration from where it stopped.
```

### Related content

- [Create and deploy a single-page application in Power Pages](create-code-sites.md)
- [Configure authentication for a Power Pages site](../security/authentication/configure-site.md)
- [Server logic overview](server-logic-overview.md)
- [Power Pages Web API reference](web-api-overview.md)
- [PAC CLI pages command reference](power-platform-cli.md)
- [GitHub Copilot CLI](https://github.com/features/copilot/cli/)
- [Claude Code](https://claude.ai/code)
