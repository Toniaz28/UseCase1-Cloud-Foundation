
## Scenario 1: Preventing Public IP in DataSubnet

To prevent a VM from being created with a public IP in the DataSubnet, I would use *Azure Policy*. Azure Policy allows us to enforce rules at the subscription or resource group level, such as denying the creation of public IP addresses for resources in specific subnets or enforcing that all VMs in the DataSubnet must not have public IP enabled.

This goes beyond NSGs because NSGs only control traffic flow, not resource creation. Azure Policy ensures governance at the deployment level, preventing misconfiguration from happening in the first place.

---

## Scenario 2: Region Failure (East US Goes Offline)

If the East US region goes completely offline, the web server would become unavailable if it is deployed only in that region. To solve this, I would design a *multi-region architecture* using *Azure Traffic Manager or Azure Front Door* to route traffic between regions.

I would deploy the web application in at least two regions (e.g., East US and West US) with replication enabled using services like *Azure Site Recovery* or *Availability Zones*. This ensures high availability and disaster recovery capability.

---

## Scenario 3: Audit Trail of Resource Changes

The Azure service used to track who created or modified resources is *Azure Activity Log*.

This log records all control-plane operations such as creating, updating, or deleting resources. It can be accessed from the Azure Portal under *Monitor → Activity Log*, and it can also be exported to Log Analytics or Storage Account for long-term retention and analysis.

---

## Scenario 4: Storage Redundancy for Financial Data

To meet compliance requirements for surviving a complete datacenter failure, I would change the storage redundancy from *LRS (Locally Redundant Storage)* to *GRS (Geo-Redundant Storage)* or *GZRS (Geo-Zone-Redundant Storage)*.

This ensures that data is replicated to a secondary region, protecting against regional or datacenter-level failures. The trade-off is increased cost, as GRS and GZRS are significantly more expensive than LRS due to cross-region replication and higher durability guarantees.

---

## Scenario 5: Temporary Access to Blob Storage

To give a contractor temporary access to upload files without sharing storage account keys, I would use a *Shared Access Signature (SAS)*.

A SAS token allows granular, time-limited access to specific resources such as a blob container or file share. It is more secure than account keys because it can be restricted by permissions, expiry time, and IP address, reducing the risk of unauthorized access.