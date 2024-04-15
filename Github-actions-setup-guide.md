# GitHub Actions

GitHub Actions is a continuous integration and continuous delivery (CI/CD) platform that allows you to automate your build, test, and deployment pipeline. You can create workflows that build and test every pull request to your repository, or deploy merged pull requests to production.

*This guide is based on this project, building a pipeline for Nodejs environment.*

### How to create a workflow
1. Go to your project on GitHub inside the "Actions" tab
2. You should see `Get started with GitHub Actions` page and a search bar, search for `Node.js` and click the "Configure" button.
3. You will be redirected to an automatically crated `.yml` file with an example workflow in `.github/workflows` folder of your project. If it didn't work, create `.github/workflows` directory in your project manually and repeat the above steps.

### Explaining our workflow
###### Open `ci.yaml` in this project to see the pipeline config.
Name of the workflow.
```yaml
name: Node.js CI
```
When to run the pipeline - on pull to main and when creating the pull request.
```yaml
on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]
```

At the start of each workflow job, GitHub automatically creates a unique `GITHUB_TOKEN` secret to use in your workflow. You can use the `GITHUB_TOKEN` to authenticate in the workflow job.
These lines add permissions to `GITHUB_TOKEN` to be able to authenticate in github container registry etc.

```yaml
permissions: 
  contents: read
  packages: write
```
Then we list all the jobs we want to execute and give them an id (e.g. our `build` job)
```yaml
jobs:
  build:
```
Use `jobs.<job_id>.runs-on` to define the type of machine to run the job on. We used the default one from the template. [Choosing the runner for a job.](https://docs.github.com/en/actions/using-jobs/choosing-the-runner-for-a-job)

```yaml
    runs-on: ubuntu-latest
```

A matrix strategy lets you use variables in a single job definition to automatically create multiple job runs that are based on the combinations of the variables. You can use a matrix strategy to test your code in multiple versions of a language or on multiple operating systems. For example, you can run your pipeline on multiple node versions `node-version: ['10', 14', '20.x']`
[Using a matrix for your jobs.](https://docs.github.com/en/actions/using-jobs/using-a-matrix-for-your-jobs)
```yaml
    strategy:
      matrix:
        node-version: ['20.x']
        pnpm-version: [8]
```
#### Steps of your job:
You can look up actions and their roles on the [GitHub marketplace](https://github.com/marketplace?type=actions). 
##### Actions we used:
1. Checkout [(docs)](https://github.com/marketplace/actions/checkout)
This action checks-out your repository under `$GITHUB_WORKSPACE`, so your workflow can access it.
```yaml
    steps:
    - uses: actions/checkout@v4
```
2. Setup pnpm [(docs)](https://github.com/marketplace/actions/setup-pnpm)
Allows us to use pnpm in the pipeline as we do in our project.

```yaml
    - uses: pnpm/action-setup@v3
      with:
        version: ${{ matrix.pnpm-version }}
```
3. Docker login [(docs marketplace)](https://github.com/marketplace/actions/build-and-push-docker-images)
GitHub Action to login against a Docker registry. Since we want to use Docker in the pipeline we need to login first. [(action used)](https://github.com/docker/login-action)
This actions is called with the variables for login: registry to log into, username, password. Here we use the [`github` context](https://docs.github.com/en/actions/learn-github-actions/contexts#github-context) to access the username of the latest user who triggered the workflow.


```yaml
    - uses: docker/login-action@v2
      with:
        registry: ghcr.io # github registry
        username: ${{ github.actor }}
        password: ${{ secrets.GITHUB_TOKEN }} # token is created automatically by github
```
4. Setup Node.js environment [(docs)](https://github.com/marketplace/actions/setup-node-js-environment)
Here it is used to specify which Node version to use and cache pnpm dependencies.

```yaml
    - name: Use Node.js ${{ matrix.node-version }}
      uses: actions/setup-node@v4
      with:
        node-version: ${{ matrix.node-version }}
        cache: 'pnpm'
```
#### After setting up actions we run the following commands:
1. Install all pnpm dependencies from `package.json`
[--frozen-lockfile](https://pnpm.io/cli/install#--frozen-lockfile) - If true, pnpm doesn't generate a lockfile and fails to install if the lockfile is out of sync with the manifest / an update is needed or no lockfile is present.

```yaml
- run: pnpm install --frozen-lockfile
``` 
2. Run the production build.
```yaml
- run: pnpm build
``` 
3. Run tests
```yaml
- run: pnpm test
``` 
4. Run docker build and push the created image to the github registry.
Here we use the [`github` context](https://docs.github.com/en/actions/learn-github-actions/contexts#github-context) again to access `repository_owner` variable to be able to push the image to the correct URL in the registry. When the image is created, the old one with the same name is deleted automatically and replaced.
```yaml
    - run: |
        docker build . -t ghcr.io/${{ github.repository_owner }}/api_docker_image_name:latest
        docker push ghcr.io/${{ github.repository_owner }}/api_docker_image_name:latest
```
        

### Additional resources
[Learn GitHub Actions](https://docs.github.com/en/actions/learn-github-actions)
[Using starter workflows](https://docs.github.com/en/actions/learn-github-actions/using-starter-workflows)
[Working with the GitHub Container registry (using Docker in GitHub Actions)](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry)