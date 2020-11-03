---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-LocalGroupMember
ms.openlocfilehash: 06993c8f6618472f4809e37fbf83d298d13ae515
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202250"
---
# <span data-ttu-id="6d6bf-103">Add-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="6d6bf-103">Add-LocalGroupMember</span></span>

## <span data-ttu-id="6d6bf-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="6d6bf-104">SYNOPSIS</span></span>
<span data-ttu-id="6d6bf-105">Ajoute des membres à un groupe local.</span><span class="sxs-lookup"><span data-stu-id="6d6bf-105">Adds members to a local group.</span></span>

## <span data-ttu-id="6d6bf-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6d6bf-106">SYNTAX</span></span>

### <span data-ttu-id="6d6bf-107">Groupe</span><span class="sxs-lookup"><span data-stu-id="6d6bf-107">Group</span></span>

```
Add-LocalGroupMember [-Group] <LocalGroup> [-Member] <LocalPrincipal[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="6d6bf-108">Default</span><span class="sxs-lookup"><span data-stu-id="6d6bf-108">Default</span></span>

```
Add-LocalGroupMember [-Member] <LocalPrincipal[]> [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6d6bf-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="6d6bf-109">SecurityIdentifier</span></span>

```
Add-LocalGroupMember [-Member] <LocalPrincipal[]> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="6d6bf-110">Description</span><span class="sxs-lookup"><span data-stu-id="6d6bf-110">DESCRIPTION</span></span>

<span data-ttu-id="6d6bf-111">L' `Add-LocalGroupMember` applet de commande ajoute des utilisateurs ou des groupes à un groupe de sécurité local.</span><span class="sxs-lookup"><span data-stu-id="6d6bf-111">The `Add-LocalGroupMember` cmdlet adds users or groups to a local security group.</span></span> <span data-ttu-id="6d6bf-112">Tous les droits et les autorisations affectés à un groupe sont attribués à tous les membres de ce groupe.</span><span class="sxs-lookup"><span data-stu-id="6d6bf-112">All the rights and permissions that are assigned to a group are assigned to all members of that group.</span></span>

<span data-ttu-id="6d6bf-113">Les membres du groupe Administrateurs sur un ordinateur local possèdent l’autorisation Contrôle total sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6d6bf-113">Members of the Administrators group on a local computer have Full Control permissions on that computer.</span></span> <span data-ttu-id="6d6bf-114">Limitez le nombre d’utilisateurs dans le groupe Administrateurs.</span><span class="sxs-lookup"><span data-stu-id="6d6bf-114">Limit the number of users in the Administrators group.</span></span>

<span data-ttu-id="6d6bf-115">Si l’ordinateur est joint à un domaine, vous pouvez ajouter sur un ordinateur local des comptes d’utilisateurs, d’ordinateurs et de groupes à partir de ce domaine et de domaines approuvés.</span><span class="sxs-lookup"><span data-stu-id="6d6bf-115">If the computer is joined to a domain, you can add user accounts, computer accounts, and group accounts from that domain and from trusted domains to a local group.</span></span>

> [!NOTE]
> <span data-ttu-id="6d6bf-116">Si l’ordinateur est joint à un domaine et que vous essayez d’ajouter un utilisateur local qui porte le même nom qu’un membre du domaine, il ajoute le membre du domaine.</span><span class="sxs-lookup"><span data-stu-id="6d6bf-116">If the computer is joined to a domain and you try to add a local user that has the same name as a member of the domain it adds the domain member.</span></span>

## <span data-ttu-id="6d6bf-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="6d6bf-117">EXAMPLES</span></span>

### <span data-ttu-id="6d6bf-118">Exemple 1 : ajouter des membres au groupe administrateurs</span><span class="sxs-lookup"><span data-stu-id="6d6bf-118">Example 1: Add members to the Administrators group</span></span>

<span data-ttu-id="6d6bf-119">Cette commande ajoute plusieurs membres au groupe Administrateurs local.</span><span class="sxs-lookup"><span data-stu-id="6d6bf-119">This command adds several members to the local Administrators group.</span></span> <span data-ttu-id="6d6bf-120">Les nouveaux membres incluent un compte d’utilisateur local, un compte Microsoft, un compte Azure Active Directory et un groupe de domaine.</span><span class="sxs-lookup"><span data-stu-id="6d6bf-120">The new members include a local user account, a Microsoft account, an Azure Active Directory account, and a domain group.</span></span> <span data-ttu-id="6d6bf-121">Cet exemple utilise une valeur d’espace réservé pour le nom d’utilisateur d’un compte sur Outlook.com.</span><span class="sxs-lookup"><span data-stu-id="6d6bf-121">This example uses a placeholder value for the user name of an account at Outlook.com.</span></span>

```powershell
Add-LocalGroupMember -Group "Administrators" -Member "Admin02", "MicrosoftAccount\username@Outlook.com", "AzureAD\DavidChew@contoso.com", "CONTOSO\Domain Admins"
```

## <span data-ttu-id="6d6bf-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6d6bf-122">PARAMETERS</span></span>

### <span data-ttu-id="6d6bf-123">-Group</span><span class="sxs-lookup"><span data-stu-id="6d6bf-123">-Group</span></span>

<span data-ttu-id="6d6bf-124">Spécifie le groupe de sécurité auquel cette applet de commande ajoute des membres.</span><span class="sxs-lookup"><span data-stu-id="6d6bf-124">Specifies the security group to which this cmdlet adds members.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup
Parameter Sets: Group
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6d6bf-125">-Membre</span><span class="sxs-lookup"><span data-stu-id="6d6bf-125">-Member</span></span>

<span data-ttu-id="6d6bf-126">Spécifie un tableau d’utilisateurs ou de groupes que cette applet de commande ajoute à un groupe de sécurité.</span><span class="sxs-lookup"><span data-stu-id="6d6bf-126">Specifies an array of users or groups that this cmdlet adds to a security group.</span></span> <span data-ttu-id="6d6bf-127">Vous pouvez spécifier des utilisateurs ou des groupes par nom, ID de sécurité (SID) ou objets **LocalPrincipal** .</span><span class="sxs-lookup"><span data-stu-id="6d6bf-127">You can specify users or groups by name, security ID (SID), or **LocalPrincipal** objects.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalPrincipal[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6d6bf-128">-Name</span><span class="sxs-lookup"><span data-stu-id="6d6bf-128">-Name</span></span>

<span data-ttu-id="6d6bf-129">Spécifie le nom du groupe de sécurité auquel cette applet de commande ajoute des membres.</span><span class="sxs-lookup"><span data-stu-id="6d6bf-129">Specifies the name of the security group to which this cmdlet adds members.</span></span>

```yaml
Type: System.String
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6d6bf-130">-SID</span><span class="sxs-lookup"><span data-stu-id="6d6bf-130">-SID</span></span>

<span data-ttu-id="6d6bf-131">Spécifie l’ID de sécurité du groupe de sécurité auquel cette applet de commande ajoute des membres.</span><span class="sxs-lookup"><span data-stu-id="6d6bf-131">Specifies the security ID of the security group to which this cmdlet adds members.</span></span>

```yaml
Type: System.Security.Principal.SecurityIdentifier
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6d6bf-132">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6d6bf-132">-Confirm</span></span>

<span data-ttu-id="6d6bf-133">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6d6bf-133">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6d6bf-134">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6d6bf-134">-WhatIf</span></span>

<span data-ttu-id="6d6bf-135">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6d6bf-135">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="6d6bf-136">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="6d6bf-136">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6d6bf-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6d6bf-137">CommonParameters</span></span>

<span data-ttu-id="6d6bf-138">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6d6bf-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6d6bf-139">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6d6bf-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6d6bf-140">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="6d6bf-140">INPUTS</span></span>

### <span data-ttu-id="6d6bf-141">System. Management. Automation. SecurityAccountsManager. LocalGroup, System. String, System. Security. principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="6d6bf-141">System.Management.Automation.SecurityAccountsManager.LocalGroup, System.String, System.Security.Principal.SecurityIdentifier</span></span>

<span data-ttu-id="6d6bf-142">Vous pouvez diriger un principal local, une chaîne ou un SID vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6d6bf-142">You can pipe a local principal, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="6d6bf-143">SORTIES</span><span class="sxs-lookup"><span data-stu-id="6d6bf-143">OUTPUTS</span></span>

### <span data-ttu-id="6d6bf-144">Aucun</span><span class="sxs-lookup"><span data-stu-id="6d6bf-144">None</span></span>

<span data-ttu-id="6d6bf-145">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="6d6bf-145">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="6d6bf-146">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="6d6bf-146">NOTES</span></span>

<span data-ttu-id="6d6bf-147">Le module Microsoft. PowerShell. LocalAccounts n’est pas disponible dans PowerShell 32 bits sur un système 64 bits.</span><span class="sxs-lookup"><span data-stu-id="6d6bf-147">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

<span data-ttu-id="6d6bf-148">La propriété **PrincipalSource** est une propriété des objets **LocalUser** , **LocalGroup** et **LocalPrincipal** qui décrit la source de l’objet.</span><span class="sxs-lookup"><span data-stu-id="6d6bf-148">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="6d6bf-149">Les sources possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="6d6bf-149">The possible sources are as follows:</span></span>

- <span data-ttu-id="6d6bf-150">Local</span><span class="sxs-lookup"><span data-stu-id="6d6bf-150">Local</span></span>
- <span data-ttu-id="6d6bf-151">Active Directory</span><span class="sxs-lookup"><span data-stu-id="6d6bf-151">Active Directory</span></span>
- <span data-ttu-id="6d6bf-152">Groupe Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="6d6bf-152">Azure Active Directory group</span></span>
- <span data-ttu-id="6d6bf-153">Compte Microsoft</span><span class="sxs-lookup"><span data-stu-id="6d6bf-153">Microsoft Account</span></span>

<span data-ttu-id="6d6bf-154">**PrincipalSource** est pris en charge uniquement par Windows 10, windows server 2016 et les versions ultérieures du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="6d6bf-154">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="6d6bf-155">Pour les versions antérieures, la propriété est vide.</span><span class="sxs-lookup"><span data-stu-id="6d6bf-155">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="6d6bf-156">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="6d6bf-156">RELATED LINKS</span></span>

[<span data-ttu-id="6d6bf-157">Get-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="6d6bf-157">Get-LocalGroupMember</span></span>](Get-LocalGroupMember.md)

[<span data-ttu-id="6d6bf-158">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="6d6bf-158">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="6d6bf-159">Remove-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="6d6bf-159">Remove-LocalGroupMember</span></span>](Remove-LocalGroupMember.md)
