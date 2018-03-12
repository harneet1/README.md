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

- Starting Cloud Foundry will take around 5 to 6 minutes
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
- cd to folder where manifest.yml file is present before pushing app to Cloud foundry
```
cf push microgateway
```
```
cf create-route <space-name> tcp.local.pcfdev.io --random-port
```
```
cf map-route microgateway tcp.local.pcfdev.io --port <port-number from previous step>
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

- Once CA Microgateway is up and running, you can list the APIs that have been published to it, you can check the url from cf app command:
```
curl --insecure --user "admin:password" https://tcp.local.pcfdev.io:port/quickstart/1.0/services
```

If the Microgateway image doesn't have any service, it should return an empty set:
```
[]
```

- To publish a new service you can embed them into your own custom docker image and creates new image that has your service . Change the name of docker image to name that you have given in manifest.yml file and push it again to Cloud foundry. For embeding the service into docker image follow link: https://docops.ca.com/ca-microgateway/1-0/EN/working-with-the-ca-microgateway/create-your-own-microgateway-image

```
curl --insecure --user "admin:password" https://tcp.local.pcfdev.io:port/quickstart/1.0/services
```
It should return the service that you bake in docker iamge.
