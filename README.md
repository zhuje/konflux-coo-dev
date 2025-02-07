# About
This is a staging application for testing new components before they are onboarded to the offical COO release pipeline. 

## Konflux IU
1. Go to https://console.redhat.com/application-pipeline
2. Sign in with Red Hat credentials 
3. Click 'Create Aplication' follow the prompts 

## Adding a component 
1. git submodule add <my-new-component.git>
2. Update `.gitmodule` file to point at the URL and branch of your component 
3. Create a Dockerfile for Konflux to build your component. The base images must be red hat certified (e.g. visit https://catalog.redhat.com/ to see list of certified images like https://catalog.redhat.com/software/containers/rhel8/go-toolset/5b9c810add19c70b45cbd666)

Note: This repo has already installed the "Red Hat Konflux" GitHub App which allows Konflux to make pull requests.
Go to this repo's "Settings" > "Integrations" > "Github Apps" and "Red Hat Konflux" should be listed. 

### Demo of Konflux UI 
https://www.youtube.com/watch?v=hms-mKLksvw


## Creating a shared workplace for public instances 
https://konflux.pages.redhat.com/docs/users/getting-started/getting-access.html#_team_access_to_the_public_instance



