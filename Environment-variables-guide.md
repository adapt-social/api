## Environment variables
Environment variables are used to store app secrets and configuration data, which are retrieved by your running app when needed. They can include Environment Type, Domain Name, API URLs, Private Keys, etc.
## In GitHub 
All necessary sensitive values and secrets can be found in the settings -> security section of the repository under 'Secrets and Variables'.

##### Secrets vs variables
*Environment variables* have values that can be revealed, while *secrets* have hidden values.
Once a secret is created you cannot access its value again, only rewrite it, so you should save it somewhere safe, for example in a password manager.
https://www.howtogeek.com/devops/what-are-github-secrets-and-how-do-you-use-them/

## Defining environment variables in Nx: 

**Nx will automatically pick up the variables in .env file.**
All custom variables (not HOST, PORT etc.) should be prefixed with `NX_` otherwise they will not be read by Nx and will be `undefined`.
https://nx.dev/recipes/tips-n-tricks/define-environment-variables

##### Nx configuration variables:
https://nx.dev/reference/environment-variables