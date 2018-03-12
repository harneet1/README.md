# Prerequisites
- VirtualBox 5.0 or higher
- Install the CF CLI
- Install PCF Dev

# Deployment types
The following deployments are currently supported
	1) MSGW (Quickstart Startup Mode)

### Configure variables:
The folder consists of manifest.yml file
	1) manifest.yml file consist of docker image and all environment variable that are required to deploy microgateway 

### Deploy
- Accept the license

  To accept the license agreement [Microservices Gateway Pre-Release Agreement], set the value of "ACCEPT_LICENSE" to true. This variable is present in manifest.yml file.

- Start
```
cf dev start
```
```
cf login -a api.local.pcfdev.io --skip-ssl-validation
Email> admin
Password> admin
press enter to skip
```
```
cf create-org <org-name>
```
```
cf target -o <org-name>
```
```
cf create-space <space-name>
```
```
cf target -o <org-name> -s <space-name>
```
```
cf push <app-name>
```
```
cf create-route <space-name> tcp.local.pcfdev.io --random-port
```
```
cf map-route <app-name> tcp.local.pcfdev.io --port <port-number from previous step>
```
- To check status of app
```
cf apps
```
- To check logs
```
cf logs <app-name> --recent
```
- To see dashboard
```
Go to URL: https://apps.local.pcfdev.io
Email> admin
Password> admin
```
