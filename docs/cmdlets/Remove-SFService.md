# Remove-SFService
Deletes an existing Service Fabric service.
## Description

A service must be created before it can be deleted. By default, Service Fabric will try to close service replicas in a 
graceful manner and then delete the service. However, if the service is having issues closing the replica gracefully, 
the delete operation may take a long time or get stuck. Use the optional ForceRemove flag to skip the graceful close 
sequence and forcefully delete the service.



## Optional Parameters
#### -ForceRemove

Remove a Service Fabric application or service forcefully without going through the graceful shutdown sequence. This 
parameter can be used to forcefully delete an application or service for which delete is timing out due to issues in 
the service code that prevents graceful close of replicas.



#### -ServerTimeout

The server timeout for performing the operation in seconds. This timeout specifies the time duration that the client 
is willing to wait for the requested operation to complete. The default value for this parameter is 60 seconds.



