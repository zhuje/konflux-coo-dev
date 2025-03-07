# About
This is a staging application for testing new components before they are onboarded to the offical COO release pipeline. 

## Konflux UI
1. Go to https://console.redhat.com/application-pipeline
2. Sign in with Red Hat credentials 
3. Click 'Create Aplication' follow the prompts 

## Adding a component 
1. git submodule add <my-new-component.git>
2. Update `.gitmodule` file to point at the URL and branch of your component 
3. Create a Dockerfile for Konflux to build your component. The base images must be red hat certified (e.g. visit https://catalog.redhat.com/ to see list of certified images like https://catalog.redhat.com/software/containers/rhel8/go-toolset/5b9c810add19c70b45cbd666)

Note: This repo has already installed the "Red Hat Konflux" GitHub App which allows Konflux to make pull requests the the repo. 
Go to this repo's "Settings" > "Integrations" > "Github Apps" and "Red Hat Konflux" should be listed. 

### Demo of Konflux UI 
https://www.youtube.com/watch?v=hms-mKLksvw

## Get access to brew.registry.redhat.io
```
# 1. replace `jezhu` with the commands below your red hat username. If prompted for a password with kinit enter your IPA password.
$ kinit jezhu@IPA.REDHAT.COM
# 2. Create a token 
$ curl --negotiate -k --verbose -u jezhu : -X POST -H 'Content-Type: application/json' --data '{"description":"openshift 4 testing"}' https://employee-token-manager.registry.redhat.com/v1/tokens -s | jq
# 3. the curl command will output credientials for your username and password. Use theses credientials to log into the registry. 
$ podman login brew.registry.redhat.io
```

Documentation (docs below require redhat SSO) <br/>
https://source.redhat.com/groups/public/teamnado/wiki/brew_registry 

Troubleshooting your IPA </br>
- Set up/reset your Idenity Policy Audit (IPA) password https://gitlab.cee.redhat.com/it-iam/system-configs/-/tree/master/krb5/idm (require Red Hat VPN)


## Creating registry pull secrets in Konflux 
This is needed to access private registries that require authentication like `registry.redhat.io`. 
https://konflux-ci.dev/docs/how-tos/configuring/creating-secrets/#creating-registry-pull-secrets


## TODO: Creating a shared workplace for public instances 
https://konflux.pages.redhat.com/docs/users/getting-started/getting-access.html#_team_access_to_the_public_instance
