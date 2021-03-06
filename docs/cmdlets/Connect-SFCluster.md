# Connect-SFCluster

## Description
Connects to a Service Fabric Cluster.
### Connecting to Cluster
#### Connecting to unsecured cluster
```PowerShell
Connect-SFCluster -ConnectionEndpoint http://<cluster_fqdn>:19080
```

#### Connecting to cluster secured with X509 certificate
##### Connect using Server Certificate thumbprint and Client Certificate from a file.
```PowerShell
# Get the client certificate
$cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2("<Path to .pfx file>", "password")
Connect-SFCluster -ConnectionEndpoint https://<cluster_fqdn>:19080 -ServerCertThumbprint "server_cert_thumbprint" -ClientCertificate $cert
```

##### Connect using Server Certificate thumbprint and Client Certificate from certificate store
```PowerShell
Connect-SFCluster -ConnectionEndpoint https://amanserver02:19080 -X509Credential -ServerCertThumbprint "server_cert_thumbprint" -FindType FindByThumbprint -FindValue <client_cert_thumbprint> -StoreLocation LocalMachine -StoreName My
```

##### Connect using Server Certificate Common Name and Client Certificate from certificate store
Note: For Self-signed certificates used with Common name, chain validation of the cert must succeed.
```PowerShell
Connect-SFCluster -ConnectionEndpoint https://amanserver02:19080 -X509Credential -ServerCommonName "server_common_name" -FindType FindByThumbprint -FindValue <client_cert_thumbprint> -StoreLocation LocalMachine -StoreName My
```


#### Connecting to cluster secured with Azure Active Directory
There are different ways to connect to the cluster secured with Azure Active Directory depending on if you already have the AAD Token. If you have the AAD Token, use the option 1 below, if you don't have the AAD Token, use the option 2 below.
##### 1. You have the AAD token from Azure Active Directory.
If you have the AAD token, you can use it directly as shown below.
###### Connect using Server Certificate thumbprint
```powershell
Connect-SFCluster -ConnectionEndpoint https://amanserver02:19080 -AzureActiveDirectory -ServerCertThumbprint "server_cert_thumbprint" -SecurityToken "Token"
```
###### Connect using Server Certificate Common Name
Note: For Self-signed certificates used with Common name, chain validation of the cert must succeed.
```powershell
Connect-SFCluster -ConnectionEndpoint https://amanserver02:19080 -AzureActiveDirectory -ServerCommonName "server_common_name" -SecurityToken "Token"
```
##### 2. You don't have the AAD token.
If you don't have the AAD token, use the following option to allow AAD login.
###### Connect using Server Certificate thumbprint
```powershell
Connect-SFCluster -ConnectionEndpoint https://amanserver02:19080 -AzureActiveDirectory -ServerCertThumbprint "server_cert_thumbprint"
```
###### Connect using Server Certificate Common Name
Note: SelfSigned certificates will only be verified with Common name when chain build succeeds (On WIndows it must be copied to TrustedRoot or TrustedPeople)
```powershell
Connect-SFCluster -ConnectionEndpoint https://amanserver02:19080 -AzureActiveDirectory -ServerCommonName "server_common_name"
