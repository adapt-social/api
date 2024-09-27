####For this project we are using Nx to help with the following struggles:

- **Run Tasks Efficiently**: Nx [runs tasks in parallel](https://nx.dev/features/run-tasks) and orders the tasks based on the dependencies between them.
- **Cache Locally & Remotely**: With [local](https://nx.dev/features/cache-task-results) and [remote caching](https://nx.dev/ci/features/remote-cache), Nx prevents unnecessary re-runs of tasks, saving you valuable dev time.
- **Automate Dependency Updates**: if you leverage Nx plugins you gain additional features such as [code generation](https://nx.dev/features/generate-code) and tools to [automatically upgrade](https://nx.dev/features/automate-updating-dependencies) your codebase and dependencies.
- **Enforce Module Boundaries**

The **Nx** package provides fundamental technology-agnostic capabilities such as: [workspace analysis](https://nx.dev/features/explore-graph), [task running](https://nx.dev/features/run-tasks), [caching](https://nx.dev/features/cache-task-results), [distribution](https://nx.dev/ci/features/distribute-task-execution), [code generation](https://nx.dev/features/generate-code) and [automated code migrations](https://nx.dev/features/automate-updating-dependencies).

**Plugins** are NPM packages that build on top of the fundamental capabilities provided by the Nx package. Nx plugins contain [code generators](https://nx.dev/features/generate-code), [executors](https://nx.dev/concepts/executors-and-configurations) and automated code migrations
for keeping your tools up to date. Plugins are usually
technology specific. For instance, `@nx/react` adds support for building React apps and libs, `@nx/cypress`
adds e2e testing capabilities with Cypress.

# How to use Nx in your projects

## Installation

#### In a new project:

To create a new nx workspace simply run `npx create-nx-workspace@latest` and it will guide you through all the setup. This project is build with Express which comes with TypeScript automatically, if you want to use another framework with TypeScript you can run `npx create-nx-workspace@latest --preset=ts`.

#### In an existing project:

run `npx nx@latest init`

Or install Nx globally:
`npm add --global nx@latest`

The advantage of a **global installation** is that you **don't have to prefix your commands with npx, yarn or pnpm**. The global Nx installation hands off the process execution to the local Nx installation in your repository, which eliminates any issues with outdated globally installed packages.

**Nx Console** is an extension for **VSCode, IntelliJ and VIM**. It provides code autocompletion, interactive generators, workspace visualizations, powerful refactorings and more. You can [install it here](https://nx.dev/features/integrate-with-editors).

#### CI configuration

When you create a new workspace you've given an option to create a configuration with **Nx Cloud**. It's free and can be disabled at any time.
If you choose it your Nx Cloud workspace will be **public**.
To restrict access, connect it to your Nx Cloud account:

- Push your changes
- Login at [https://cloud.nx.app](https://cloud.nx.app/) to connect your repository

## Running Tasks

Once you've created your workspace, you can

- run single tasks with `npx nx <target> <project>`
- run multiple tasks with `npx nx run-many -t <target1> <target2>`

#### Define Cacheable Tasks

To enable caching for build and test, edit the targetDefaults property in `nx.json` to include the build and test tasks:

```json
{
  "targetDefaults": {
    "build": {
      "cache": true
    },
    "test": {
      "cache": true
    }
  }
}
```

## Explore your Workspace

Look at the **Projects** pane in [Nx Console](https://nx.dev/features/integrate-with-editors) or run `nx show projects` to show a list of projects in your terminal. You can also see more details about a specific project in Nx Console or by running `npx nx show project <project-name> --web`.

**Launching the Project Graph**

To launch the project graph visualization for your workspace, use [Nx Console](https://nx.dev/features/integrate-with-editors) or run `npx nx graph`

This will open a browser window with an interactive view of the project graph of your workspace.

Nx understands the projects in your workspace as a graph. Exploring this graph visually is vital to understanding how your code is structured and how Nx behaves. It always stays up to date without having to actively maintain a document as it is [calculated by analyzing your source code](https://nx.dev/concepts/more-concepts/how-project-graph-is-built#how-the-project-graph-is-built).
