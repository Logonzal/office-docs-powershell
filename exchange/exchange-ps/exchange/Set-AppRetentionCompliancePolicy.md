---
external help file: Microsoft.Exchange.TransportMailflow-Help.xml
online version: https://learn.microsoft.com/powershell/module/exchange/set-appretentioncompliancepolicy
applicable: Security & Compliance
title: Set-AppRetentionCompliancePolicy
schema: 2.0.0
author: chrisda
ms.author: chrisda
ms.reviewer:
---

# Set-AppRetentionCompliancePolicy

## SYNOPSIS
This cmdlet is available only in Security & Compliance PowerShell. For more information, see [Security & Compliance PowerShell](https://learn.microsoft.com/powershell/exchange/scc-powershell).

Use the Set-AppRetentionCompliancePolicy to modify app retention compliance policies.

For information about the parameter sets in the Syntax section below, see [Exchange cmdlet syntax](https://learn.microsoft.com/powershell/exchange/exchange-cmdlet-syntax).

## SYNTAX

### Identity (Default)
```
Set-AppRetentionCompliancePolicy [-Identity] <PolicyIdParameter>
 [-AddExchangeLocation <MultiValuedProperty>]
 [-AddExchangeLocationException <MultiValuedProperty>]
 [-AddModernGroupLocation <MultiValuedProperty>]
 [-AddModernGroupLocationException <MultiValuedProperty>]
 [-Applications <String[]>]
 [-Comment <String>]
 [-Confirm]
 [-Enabled <Boolean>]
 [-Force]
 [-PolicyRBACScopes <MultiValuedProperty>]
 [-RemoveExchangeLocation <MultiValuedProperty>]
 [-RemoveExchangeLocationException <MultiValuedProperty>]
 [-RemoveModernGroupLocation <MultiValuedProperty>]
 [-RemoveModernGroupLocationException <MultiValuedProperty>]
 [-RestrictiveRetention <Boolean>]
 [-WhatIf]
 [<CommonParameters>]
```

### AdaptiveScopeLocation
```
Set-AppRetentionCompliancePolicy [-Identity] <PolicyIdParameter>
 [-AddAdaptiveScopeLocation <MultiValuedProperty>]
 [-Applications <String[]>]
 [-Comment <String>]
 [-Confirm]
 [-Enabled <Boolean>]
 [-Force]
 [-RemoveAdaptiveScopeLocation <MultiValuedProperty>]
 [-WhatIf]
 [<CommonParameters>]
```

### TeamLocation
```
Set-AppRetentionCompliancePolicy [-Identity] <PolicyIdParameter>
 [-Comment <String>]
 [-Confirm]
 [-Enabled <Boolean>]
 [-Force]
 [-WhatIf]
 [<CommonParameters>]
```

### InformationBarrierDefault
```
Set-AppRetentionCompliancePolicy [-Identity] <PolicyIdParameter>
 [-Confirm]
 [-Force]
 [-WhatIf]
 [<CommonParameters>]
```

### OrganizationSegmentsDefault
```
Set-AppRetentionCompliancePolicy [-Identity] <PolicyIdParameter>
 [-Confirm]
 [-WhatIf]
 [<CommonParameters>]
```

### DisableRestrictiveRetentionParameterSet
```
Set-AppRetentionCompliancePolicy [-Identity] <PolicyIdParameter>
 [-Confirm]
 [-WhatIf]
 [<CommonParameters>]
```

### RetryDistributionParameterSet
```
Set-AppRetentionCompliancePolicy [-Identity] <PolicyIdParameter>
 [-Confirm]
 [-RetryDistribution]
 [-WhatIf]
 [<CommonParameters>]
```

## DESCRIPTION
To use this cmdlet in Security & Compliance PowerShell, you need to be assigned permissions. For more information, see [Permissions in the Microsoft Purview compliance portal](https://learn.microsoft.com/microsoft-365/compliance/microsoft-365-compliance-center-permissions).

## EXAMPLES

### Example 1
```powershell
Set-AppRetentionCompliancePolicy Identity "Regulation 563 Marketing" -Applications "User:MicrosoftTeams","Group:MicrosoftTeams,Yammer" -AddExchangeLocation "Scott Smith" -Comment "Added new counsel, 9/9/21"
```

This example adds a new user to the existing static scope retention policy named Regulation 563 Marketing that's set up for Teams private channels messages.

## PARAMETERS

### -Identity
The Identity parameter specifies the app retention compliance policy that you want to modify. You can use any value that uniquely identifies the policy. For example:

- Name
- Distinguished name (DN)
- GUID

```yaml
Type: PolicyIdParameter
Parameter Sets: (All)
Aliases:
Applicable: Security & Compliance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -RetryDistribution
The RetryDistribution switch specifies whether to redistribute the policy to all locations. You don't need to specify a value with this switch.

Locations whose initial distributions succeeded aren't included in the retry. Policy distribution errors are reported when you use this switch.

**Note**: Because the process of retrying distribution is a significant operation, run it only if necessary and for one policy at a time. It is not intended to be run every time you update a policy. If you run a script to update multiple policies, wait until the policy distribution is successful before running the command again for the next policy.

```yaml
Type: SwitchParameter
Parameter Sets: RetryDistributionParameterSet
Aliases:
Applicable: Security & Compliance

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AddAdaptiveScopeLocation
The AddAdaptiveScopeLocation parameter specifies the adaptive scope location to add to the policy. You create adaptive scopes by using the New-AdaptiveScope cmdlet. You can use any value that uniquely identifies the adaptive scope. For example:

- Name
- Distinguished name (DN)
- GUID

You can enter multiple values separated by commas. If the values contain spaces or otherwise require quotation marks, use the following syntax: `"Value1","Value2",..."ValueN"`.

```yaml
Type: MultiValuedProperty
Parameter Sets: AdaptiveScopeLocation
Aliases:
Applicable: Security & Compliance

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AddExchangeLocation
The AddExchangeLocation parameter specifies the mailboxes to add to the list of included mailboxes when you aren't using the value All for the ExchangeLocation parameter. Valid values are:

- A mailbox
- A distribution group or mail-enabled security group (all mailboxes that are currently members of the group).

To specify a mailbox or distribution group, you can use any value that uniquely identifies it. For example:

- Name
- Distinguished name (DN)
- Email address
- GUID

You can enter multiple values separated by commas. If the values contain spaces or otherwise require quotation marks, use the following syntax: `"Value1","Value2",..."ValueN"`.

```yaml
Type: MultiValuedProperty
Parameter Sets: Identity
Aliases:
Applicable: Security & Compliance

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AddExchangeLocationException
The AddExchangeLocationException parameter specifies the mailboxes to add to the list of excluded mailboxes when you're using the value All for the ExchangeLocation parameter. Valid values are:

- A mailbox
- A distribution group or mail-enabled security group

To specify a mailbox or distribution group, you can use any value that uniquely identifies it. For example:

- Name
- Distinguished name (DN)
- Email address
- GUID

You can enter multiple values separated by commas. If the values contain spaces or otherwise require quotation marks, use the following syntax: `"Value1","Value2",..."ValueN"`.

```yaml
Type: MultiValuedProperty
Parameter Sets: Identity
Aliases:
Applicable: Security & Compliance

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AddModernGroupLocation
The AddModernGroupLocation parameter specifies the Microsoft 365 Groups to add to the list of included Microsoft 365 Groups when you aren't using the value All for the ModernGroupLocation parameter.

You can use any value that uniquely identifies the Microsoft 365 Group. For example:

- Name
- Distinguished name (DN)
- Email address
- GUID

You can enter multiple values separated by commas. If the values contain spaces or otherwise require quotation marks, use the following syntax: `"Value1","Value2",..."ValueN"`.

```yaml
Type: MultiValuedProperty
Parameter Sets: Identity
Aliases:
Applicable: Security & Compliance

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AddModernGroupLocationException
The AddModernGroupLocationException parameter specifies the Microsoft 365 Groups to add to the list of excluded Microsoft 365 Groups when you're using the value All for the ModernGroupLocation parameter.

You can use any value that uniquely identifies the Microsoft 365 Group. For example:

- Name
- Distinguished name (DN)
- Email address
- GUID

You can enter multiple values separated by commas. If the values contain spaces or otherwise require quotation marks, use the following syntax: `"Value1","Value2",..."ValueN"`.

```yaml
Type: MultiValuedProperty
Parameter Sets: Identity
Aliases:
Applicable: Security & Compliance

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Applications
The Applications parameter specifies the applications to include and is relevant only for the following location parameters:

- ExchangeLocation
- ModernGroupLocation
- AdaptiveScopeLocation

This parameter uses the following syntax: `"LocationtType:App1,LocationType:App2,...LocationType:AppN` where LocationType is User or Group. For example, `"User:Exchange,User:OneDriveForBusiness,Group:Exchange,Group:SharePoint"` or `"User:MicrosoftTeams","User:Yammer"`.

```yaml
Type: String[]
Parameter Sets: Identity, AdaptiveScopeLocation
Aliases:
Applicable: Security & Compliance

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Comment
The Comment parameter specifies an optional comment. If you specify a value that contains spaces, enclose the value in quotation marks ("), for example: "This is an admin note".

```yaml
Type: String
Parameter Sets: Identity, AdaptiveScopeLocation, TeamLocation
Aliases:
Applicable: Security & Compliance

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm
The Confirm switch specifies whether to show or hide the confirmation prompt. How this switch affects the cmdlet depends on if the cmdlet requires confirmation before proceeding.

- Destructive cmdlets (for example, Remove-\* cmdlets) have a built-in pause that forces you to acknowledge the command before proceeding. For these cmdlets, you can skip the confirmation prompt by using this exact syntax: `-Confirm:$false`.
- Most other cmdlets (for example, New-\* and Set-\* cmdlets) don't have a built-in pause. For these cmdlets, specifying the Confirm switch without a value introduces a pause that forces you acknowledge the command before proceeding.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf
Applicable: Security & Compliance

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Enabled
The Enabled parameter enables or disables the policy. Valid values are:

- $true: The policy is enabled. This is the default value.
- $false: The policy is disabled.

```yaml
Type: Boolean
Parameter Sets: Identity, AdaptiveScopeLocation, TeamLocation
Aliases:
Applicable: Security & Compliance

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force
The Force switch hides warning or confirmation messages. You don't need to specify a value with this switch.

You can use this switch to run tasks programmatically where prompting for administrative input is inappropriate.

```yaml
Type: SwitchParameter
Parameter Sets: Identity, AdaptiveScopeLocation, TeamLocation, InformationBarrierDefault
Aliases:
Applicable: Security & Compliance

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PolicyRBACScopes
{{ Fill PolicyRBACScopes Description }}

```yaml
Type: MultiValuedProperty
Parameter Sets: Identity
Aliases:
Applicable: Security & Compliance

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoveAdaptiveScopeLocation
The RemoveAdaptiveScopeLocation parameter specifies the adaptive scope location to remove from the policy. You create adaptive scopes by using the New-AdaptiveScope cmdlet. You can use any value that uniquely identifies the adaptive scope. For example:

- Name
- Distinguished name (DN)
- GUID

You can enter multiple values separated by commas. If the values contain spaces or otherwise require quotation marks, use the following syntax: `"Value1","Value2",..."ValueN"`.

```yaml
Type: MultiValuedProperty
Parameter Sets: AdaptiveScopeLocation
Aliases:
Applicable: Security & Compliance

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoveExchangeLocation
The RemoveExchangeLocation parameter specifies the mailboxes to remove from the list of included mailboxes when you aren't using the value All for the ExchangeLocation parameter. Valid values are:

- A mailbox
- A distribution group or mail-enabled security group

To specify a mailbox or distribution group, you can use any value that uniquely identifies it. For example:

- Name
- Distinguished name (DN)
- Email address
- GUID

You can enter multiple values separated by commas. If the values contain spaces or otherwise require quotation marks, use the following syntax: `"Value1","Value2",..."ValueN"`.

```yaml
Type: MultiValuedProperty
Parameter Sets: Identity
Aliases:
Applicable: Security & Compliance

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoveExchangeLocationException
The RemoveExchangeLocationException parameter specifies the mailboxes to remove from the list of excluded mailboxes when you use the value All for the ExchangeLocation parameter. Valid values are:

- A mailbox
- A distribution group or mail-enabled security group

To specify a mailbox or distribution group, you can use any value that uniquely identifies it. For example:

- Name
- Distinguished name (DN)
- Email address
- GUID

You can enter multiple values separated by commas. If the values contain spaces or otherwise require quotation marks, use the following syntax: `"Value1","Value2",..."ValueN"`.

```yaml
Type: MultiValuedProperty
Parameter Sets: Identity
Aliases:
Applicable: Security & Compliance

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoveModernGroupLocation
The RemoveModernGroupLocation parameter specifies the Microsoft 365 Groups to remove from the list of included groups when you aren't using the value All for the ModernGroupLocation parameter.

You can use any value that uniquely identifies the Microsoft 365 Group. For example:

- Name
- Distinguished name (DN)
- Email address
- GUID

You can enter multiple values separated by commas. If the values contain spaces or otherwise require quotation marks, use the following syntax: `"Value1","Value2",..."ValueN"`.

```yaml
Type: MultiValuedProperty
Parameter Sets: Identity
Aliases:
Applicable: Security & Compliance

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoveModernGroupLocationException
The RemoveModernGroupLocationException parameter specifies the Microsoft 365 Groups to remove from the list of excluded groups when you're using the value All for the ModernGroupLocation parameter.

You can use any value that uniquely identifies the Microsoft 365 Group. For example:

- Name
- Distinguished name (DN)
- Email address
- GUID

You can enter multiple values separated by commas. If the values contain spaces or otherwise require quotation marks, use the following syntax: `"Value1","Value2",..."ValueN"`.

```yaml
Type: MultiValuedProperty
Parameter Sets: Identity
Aliases:
Applicable: Security & Compliance

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RestrictiveRetention
The RestrictiveRetention parameter specifies whether Preservation Lock is enabled for the policy. Valid values are:

- $true: Preservation Lock is enabled for the policy. No one -- including an administrator -- can turn off the policy or make it less restrictive.
- $false: Preservation Lock isn't enabled for the policy. This is the default value.

After a policy has been locked, no one can turn off or disable it, or remove apps from the policy. The only ways that you can modify the policy are by adding apps to it, or extending its duration. A locked policy can be increased or extended, but it can't be reduced, disabled, or turned off.

Therefore, before you lock a policy, it's critical that you understand your organization's compliance requirements, and that you don't lock a policy until you are certain that it's what you need.

```yaml
Type: Boolean
Parameter Sets: Identity
Aliases:
Applicable: Security & Compliance

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
The WhatIf switch doesn't work in Security & Compliance PowerShell.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi
Applicable: Security & Compliance

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/p/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS
