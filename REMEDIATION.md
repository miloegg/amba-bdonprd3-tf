## From Documentation

https://azure.github.io/azure-monitor-baseline-alerts/patterns/alz/HowTo/deploy/Remediate-Policies/

By default, the policies are set to deploy-if-not-exists. This configuration affects any new deployments. In a greenfield scenario, where new resources and subscriptions are deployed, the policies will automatically create the necessary alert rules, action groups, and alert processing rules.

In a brownfield scenario, the policies will report non-compliance for existing resources within their scope. To remediate these non-compliant resources, you need to initiate remediation. This can be done through the Azure portal on a policy-by-policy basis or by running the Start-AMBA-ALZ-Remediation.ps1 script located in the .\patterns\alz\scripts folder. This script will remediate all AMBA-ALZ policies in scope as defined by the management group prefix.

To use Start-AMBA-ALZ-Remediation.ps1 first download it from https://github.com/Azure/azure-monitor-baseline-alerts/blob/main/patterns/alz/scripts/Start-AMBA-ALZ-Remediation.ps1 into local computer with at least Powershell 7.5 installed


### Connect to Azure tenant
```
Connect-AzAccount -Tenant <tenant-id>
```

### Define the parameter
```
$pseudoRootManagementGroup = "mg-alz-root-npd"
$platformManagementGroup = "mg-platform-npd"
$managementManagementGroup = "mg-platform-management-npd"
$connectivityManagementGroup = "mg-platform-connectivity-npd"

$DevLZManagementGroup="mg-landingzones-dev"
$PpdLZManagementGroup="mg-landingzones-ppd"
$SitLZManagementGroup="mg-landingzones-sit"
$UatLZManagementGroup="mg-landingzones-uat"

```

### Run the following remediation commands, only required if there are non-compliances otherwise skip
```
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $pseudoRootManagementGroup -policyName Notification-Assets
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $pseudoRootManagementGroup -policyName Alerting-ServiceHealth
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $platformManagementGroup -policyName Alerting-HybridVM
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $platformManagementGroup -policyName Alerting-VM
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $connectivityManagementGroup -policyName Alerting-Connectivity
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $managementManagementGroup -policyName Alerting-Management


./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $DevLZManagementGroup -policyName Alerting-KeyManagement
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $DevLZManagementGroup -policyName Alerting-LoadBalancing
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $DevLZManagementGroup -policyName Alerting-NetworkChanges
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $DevLZManagementGroup -policyName Alerting-RecoveryServices
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $DevLZManagementGroup -policyName Alerting-Storage
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $DevLZManagementGroup -policyName Alerting-HybridVM
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $DevLZManagementGroup -policyName Alerting-VM
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $DevLZManagementGroup -policyName Alerting-Web

./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $PpdLZManagementGroup -policyName Alerting-KeyManagement
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $PpdLZManagementGroup -policyName Alerting-LoadBalancing
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $PpdLZManagementGroup -policyName Alerting-NetworkChanges
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $PpdLZManagementGroup -policyName Alerting-RecoveryServices
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $PpdLZManagementGroup -policyName Alerting-Storage
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $PpdLZManagementGroup -policyName Alerting-HybridVM
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $PpdLZManagementGroup -policyName Alerting-VM
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $PpdLZManagementGroup -policyName Alerting-Web


./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $SitLZManagementGroup -policyName Alerting-KeyManagement
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $SitLZManagementGroup -policyName Alerting-LoadBalancing
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $SitLZManagementGroup -policyName Alerting-NetworkChanges
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $SitLZManagementGroup -policyName Alerting-RecoveryServices
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $SitLZManagementGroup -policyName Alerting-Storage
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $SitLZManagementGroup -policyName Alerting-HybridVM
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $SitLZManagementGroup -policyName Alerting-VM
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $SitLZManagementGroup -policyName Alerting-Web


./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $UatLZManagementGroup -policyName Alerting-KeyManagement
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $UatLZManagementGroup -policyName Alerting-LoadBalancing
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $UatLZManagementGroup -policyName Alerting-NetworkChanges
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $UatLZManagementGroup -policyName Alerting-RecoveryServices
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $UatLZManagementGroup -policyName Alerting-Storage
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $UatLZManagementGroup -policyName Alerting-HybridVM
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $UatLZManagementGroup -policyName Alerting-VM
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $UatLZManagementGroup -policyName Alerting-Web
```


Note if there is Identity management group, the following will need to be included 

```
$identityManagementGroup = "The management group ID for Identity"
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $identityManagementGroup -policyName Alerting-Identity
```

Misc - the following policy seems to be absent
```
./Start-AMBA-ALZ-Remediation.ps1 -managementGroupName $connectivityManagementGroup -policyName Alerting-Connectivity-2
```
