# Stop-SFOperation
Cancels a user-induced fault operation.
## Description

The following APIs start fault operations that may be cancelled by using CancelOperation: StartDataLoss, 
StartQuorumLoss, StartPartitionRestart, StartNodeTransition.
                
                If force is false, then the specified user-induced operation will be gracefully stopped and cleaned 
up.  If force is true, the command will be aborted, and some internal state
                may be left behind.  Specifying force as true should be used with care.  Calling this API with force 
set to true is not allowed until this API has already
                been called on the same test command with force set to false first, or unless the test command already 
has an OperationState of OperationState.RollingBack.
                Clarification: OperationState.RollingBack means that the system will be/is cleaning up internal system 
state caused by executing the command.  It will not restore data if the
                test command was to cause data loss.  For example, if you call StartDataLoss then call this API, the 
system will only clean up internal state from running the command.
                It will not restore the target partition's data, if the command progressed far enough to cause data 
loss.
                
                Important note:  if this API is invoked with force==true, internal state may be left behind.



## Required Parameters
#### -OperationId

A GUID that identifies a call of this API.  This is passed into the corresponding GetProgress API



#### -Force

Indicates whether to gracefully roll back and clean up internal system state modified by executing the user-induced 
operation.



