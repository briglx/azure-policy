# azure-policy
Sample Policy to test enabling ddos protection on a vnet

Azure DDoS basic protection is integrated into the Azure platform by default and at no additional cost. Azure DDoS standard protection is a premium paid service that offers enhanced DDoS mitigation capabilities via adaptive tuning, attack notification, and telemetry to protect against the impacts of a DDoS attack for all protected resources within this virtual network.

The DDoS Protection service will have a fixed monthly charge, as well as a charge for data processed. The fixed monthly charge includes protection for 100 resources. Protection for additional resources will be charged on a monthly per-resource basis.

Monthly price for DDoS Protection (includes protection for 100 resources): $2,944/month *

Overage charges (more than 100 resources): $30 per resource per month *

A policy that modifies resources has to have an identity and role based access in order to make the necessary changes.

You may only want to enable ddos standard protection if there are resources that have public IPs and not all vnets

# Notes

- a vnet needs a a ddos protection plan before it can be enabled
- Required Role: Network Contributor

# Deploy

Deploy arm template with

```powershell
New-AzResourceGroupDeployment -ResourceGroupName PolicyArmTest -TemplateFile .\simplearm.json
```

# References

- Azure Policy Examples on Github https://github.com/Azure/azure-policy
- deployifnotexist details https://docs.microsoft.com/en-us/azure/governance/policy/concepts/effects#deployifnotexists
- Deploymnents details https://docs.microsoft.com/en-us/rest/api/resources/deployments
- vnet arm details https://docs.microsoft.com/en-us/rest/api/virtualnetwork/virtualnetworks/createorupdate
- vnet ddos protection plan details https://docs.microsoft.com/en-us/rest/api/virtualnetwork/ddosprotectionplans
- Network Contributor role https://docs.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#network-contributor