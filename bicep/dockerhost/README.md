# Bicep Deployment for docker single-host and multi-host architectures

In this section you will find bicep code to deploy the single and multihost foundational platforms as described in the AKS learning series.

This code can be deployed using `az cli` or `powershell` as detailed [here](https://docs.microsoft.com/en-us/azure/azure-resource-manager/bicep/deploy-cli)  

For convenience you can also follow the quickstart deployment below to get started. 

# Quickstart deployment

### Task 1: clone the repository and deploy

1. Open cloud shell and clone this repository 

``` 
git clone https://github.com/nehalineogi/azure-cross-solution-network-architectures 
```

2. Navigate to the bicep location that contains the code

```
cd azure-cross-solution-network-architectures/bicep/dockerhost/
```

3. Retrieve your signed-in user ID below (this is used to apply access to Keyvault).

```
az ad signed-in-user show --query objectId -o tsv
```

4. (optional) If you wish to customise or change the main.bicep or related module code, you can do this now and save your changes locally.  


5.  Run the following command to deploy using az cli

```
 az deployment sub create --name docker --template-file main.bicep --location [region] --parameters adUserId=[paste-asUserId-here] 
 ```

 example : 

 ```
 az deployment sub create --name docker --template-file main.bicep --location uksouth --parameters adUserId=11111111-2222-3333-4444-555555555555
 ```

6. Once your deployment has finished you can log on to the docker VMs using Azure bastion. The username is `localadmin` and passwords can be found in the keyvault.


For further information on the deployment, setting up SSH to the hosts and advanced troubleshooting please refer to the docker series pages [here](../../aks/README-docker-singlehost.md)