# Start-SFClusterConfigurationUpgrade
Start upgrading the configuration of a Service Fabric standalone cluster.
## Description

Validate the supplied configuration upgrade parameters and start upgrading the cluster configuration if the parameters 
are valid.



## Optional Parameters
#### -HealthCheckRetryTimeout

The length of time between attempts to perform health checks if the application or cluster is not healthy.



#### -HealthCheckWaitDurationInSeconds

The length of time to wait after completing an upgrade domain before starting the health checks process.



#### -HealthCheckStableDurationInSeconds

The length of time that the application or cluster must remain healthy before the upgrade proceeds to the next upgrade 
domain.



#### -UpgradeDomainTimeoutInSeconds

The timeout for the upgrade domain.



#### -UpgradeTimeoutInSeconds

The upgrade timeout.



#### -MaxPercentUnhealthyApplications

The maximum allowed percentage of unhealthy applications during the upgrade. Allowed values are integer values from 
zero to 100.



#### -MaxPercentUnhealthyNodes

The maximum allowed percentage of unhealthy nodes during the upgrade. Allowed values are integer values from zero to 
100.



#### -MaxPercentDeltaUnhealthyNodes

The maximum allowed percentage of delta health degradation during the upgrade. Allowed values are integer values from 
zero to 100.



#### -MaxPercentUpgradeDomainDeltaUnhealthyNodes

The maximum allowed percentage of upgrade domain delta health degradation during the upgrade. Allowed values are 
integer values from zero to 100.



#### -ApplicationHealthPolicyMap

The wrapper that contains the map with application health policies used to evaluate specific applications in the 
cluster.



#### -ServerTimeout

The server timeout for performing the operation in seconds. This timeout specifies the time duration that the client 
is willing to wait for the requested operation to complete. The default value for this parameter is 60 seconds.



