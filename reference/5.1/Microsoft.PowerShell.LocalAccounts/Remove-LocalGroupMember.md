---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/remove-localgroupmember?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-LocalGroupMember
ms.openlocfilehash: 6e6264a65c343657c2f2f87384d76cc3f1554d3d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203626"
---
# <span data-ttu-id="b2ab8-103">Remove-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="b2ab8-103">Remove-LocalGroupMember</span></span>

## <span data-ttu-id="b2ab8-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b2ab8-104">SYNOPSIS</span></span>
<span data-ttu-id="b2ab8-105">Supprime des membres d’un groupe local.</span><span class="sxs-lookup"><span data-stu-id="b2ab8-105">Removes members from a local group.</span></span>

## <span data-ttu-id="b2ab8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b2ab8-106">SYNTAX</span></span>

### <span data-ttu-id="b2ab8-107">Groupe</span><span class="sxs-lookup"><span data-stu-id="b2ab8-107">Group</span></span>

```
Remove-LocalGroupMember [-Group] <LocalGroup> [-Member] <LocalPrincipal[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="b2ab8-108">Default</span><span class="sxs-lookup"><span data-stu-id="b2ab8-108">Default</span></span>

```
Remove-LocalGroupMember [-Member] <LocalPrincipal[]> [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b2ab8-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="b2ab8-109">SecurityIdentifier</span></span>

```
Remove-LocalGroupMember [-Member] <LocalPrincipal[]> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="b2ab8-110">Description</span><span class="sxs-lookup"><span data-stu-id="b2ab8-110">DESCRIPTION</span></span>
<span data-ttu-id="b2ab8-111">L’applet de commande **Remove-LocalGroupMember** supprime les utilisateurs ou les groupes d’un groupe local.</span><span class="sxs-lookup"><span data-stu-id="b2ab8-111">The **Remove-LocalGroupMember** cmdlet removes users or groups from a local group.</span></span>

> [!NOTE]
> <span data-ttu-id="b2ab8-112">Le module Microsoft. PowerShell. LocalAccounts n’est pas disponible dans PowerShell 32 bits sur un système 64 bits.</span><span class="sxs-lookup"><span data-stu-id="b2ab8-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="b2ab8-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b2ab8-113">EXAMPLES</span></span>

### <span data-ttu-id="b2ab8-114">Exemple 1 : supprimer des membres du groupe administrateurs</span><span class="sxs-lookup"><span data-stu-id="b2ab8-114">Example 1: Remove members from the Administrators group</span></span>

```
PS C:\> Remove-LocalGroupMember -Group "Administrators" -Member "Admin02", "MicrosoftAccount\username@Outlook.com", "AzureAD\DavidChew@contoso.com", "CONTOSO\Domain Admins"
```

<span data-ttu-id="b2ab8-115">Cette commande supprime plusieurs membres du groupe Administrateurs local.</span><span class="sxs-lookup"><span data-stu-id="b2ab8-115">This command removes several members from the local Administrators group.</span></span>
<span data-ttu-id="b2ab8-116">Les membres que cette applet de commande supprime incluent un compte d’utilisateur local, un compte Microsoft, un compte Azure Active Directory et un groupe de domaine.</span><span class="sxs-lookup"><span data-stu-id="b2ab8-116">The members that this cmdlet removes include a local user account, a Microsoft account, an Azure Active Directory account, and a domain group.</span></span>
<span data-ttu-id="b2ab8-117">Cet exemple utilise une valeur d’espace réservé pour le nom d’utilisateur d’un compte sur Outlook.com.</span><span class="sxs-lookup"><span data-stu-id="b2ab8-117">This example uses a placeholder value for the user name of an account at Outlook.com.</span></span>

## <span data-ttu-id="b2ab8-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b2ab8-118">PARAMETERS</span></span>

### <span data-ttu-id="b2ab8-119">-Group</span><span class="sxs-lookup"><span data-stu-id="b2ab8-119">-Group</span></span>
<span data-ttu-id="b2ab8-120">Spécifie le groupe de sécurité à partir duquel cette applet de commande supprime les membres.</span><span class="sxs-lookup"><span data-stu-id="b2ab8-120">Specifies the security group from which this cmdlet removes members.</span></span>

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

### <span data-ttu-id="b2ab8-121">-Membre</span><span class="sxs-lookup"><span data-stu-id="b2ab8-121">-Member</span></span>
<span data-ttu-id="b2ab8-122">Spécifie un tableau d’utilisateurs ou de groupes que cette applet de commande supprime d’un groupe de sécurité.</span><span class="sxs-lookup"><span data-stu-id="b2ab8-122">Specifies an array of users or groups that this cmdlet removes from a security group.</span></span>
<span data-ttu-id="b2ab8-123">Vous pouvez spécifier des utilisateurs ou des groupes par nom, ID de sécurité (SID) ou objets **LocalPrincipal** .</span><span class="sxs-lookup"><span data-stu-id="b2ab8-123">You can specify users or groups by name, security ID (SID), or **LocalPrincipal** objects.</span></span>
<span data-ttu-id="b2ab8-124">Spécifiez les chaînes SID dans S-R-I-S-S.</span><span class="sxs-lookup"><span data-stu-id="b2ab8-124">Specify SID strings in S-R-I-S-S .</span></span>
<span data-ttu-id="b2ab8-125">.</span><span class="sxs-lookup"><span data-stu-id="b2ab8-125">.</span></span> <span data-ttu-id="b2ab8-126">.</span><span class="sxs-lookup"><span data-stu-id="b2ab8-126">.</span></span>
<span data-ttu-id="b2ab8-127">HH:MM:SS.</span><span class="sxs-lookup"><span data-stu-id="b2ab8-127">format.</span></span>

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

### <span data-ttu-id="b2ab8-128">-Name</span><span class="sxs-lookup"><span data-stu-id="b2ab8-128">-Name</span></span>
<span data-ttu-id="b2ab8-129">Spécifie le nom du groupe de sécurité à partir duquel cette applet de commande supprime des membres.</span><span class="sxs-lookup"><span data-stu-id="b2ab8-129">Specifies the name of the security group from which this cmdlet removes members.</span></span>

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

### <span data-ttu-id="b2ab8-130">-SID</span><span class="sxs-lookup"><span data-stu-id="b2ab8-130">-SID</span></span>
<span data-ttu-id="b2ab8-131">Spécifie l’ID de sécurité du groupe de sécurité à partir duquel cette applet de commande supprime des membres.</span><span class="sxs-lookup"><span data-stu-id="b2ab8-131">Specifies the security ID of the security group from which this cmdlet removes members.</span></span>

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

### <span data-ttu-id="b2ab8-132">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b2ab8-132">-Confirm</span></span>
<span data-ttu-id="b2ab8-133">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b2ab8-133">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b2ab8-134">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b2ab8-134">-WhatIf</span></span>
<span data-ttu-id="b2ab8-135">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b2ab8-135">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="b2ab8-136">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="b2ab8-136">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b2ab8-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b2ab8-137">CommonParameters</span></span>
<span data-ttu-id="b2ab8-138">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b2ab8-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b2ab8-139">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b2ab8-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b2ab8-140">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="b2ab8-140">INPUTS</span></span>

### <span data-ttu-id="b2ab8-141">System. Management. Automation. SecurityAccountsManager. LocalPrincipal, System. String, System. Security. principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="b2ab8-141">System.Management.Automation.SecurityAccountsManager.LocalPrincipal, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="b2ab8-142">Vous pouvez diriger un principal local, une chaîne ou un SID vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b2ab8-142">You can pipe a local principal, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="b2ab8-143">SORTIES</span><span class="sxs-lookup"><span data-stu-id="b2ab8-143">OUTPUTS</span></span>

### <span data-ttu-id="b2ab8-144">Aucun</span><span class="sxs-lookup"><span data-stu-id="b2ab8-144">None</span></span>
<span data-ttu-id="b2ab8-145">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="b2ab8-145">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="b2ab8-146">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="b2ab8-146">NOTES</span></span>

* <span data-ttu-id="b2ab8-147">La propriété **PrincipalSource** est une propriété des objets **LocalUser** , **LocalGroup** et **LocalPrincipal** qui décrit la source de l’objet.</span><span class="sxs-lookup"><span data-stu-id="b2ab8-147">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="b2ab8-148">Les sources possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="b2ab8-148">The possible sources are as follows:</span></span>

- <span data-ttu-id="b2ab8-149">Local</span><span class="sxs-lookup"><span data-stu-id="b2ab8-149">Local</span></span>
- <span data-ttu-id="b2ab8-150">Active Directory</span><span class="sxs-lookup"><span data-stu-id="b2ab8-150">Active Directory</span></span>
- <span data-ttu-id="b2ab8-151">Groupe Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="b2ab8-151">Azure Active Directory group</span></span>
- <span data-ttu-id="b2ab8-152">Compte Microsoft</span><span class="sxs-lookup"><span data-stu-id="b2ab8-152">Microsoft Account</span></span>

<span data-ttu-id="b2ab8-153">**PrincipalSource** est pris en charge uniquement par Windows 10, windows server 2016 et les versions ultérieures du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="b2ab8-153">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="b2ab8-154">Pour les versions antérieures, la propriété est vide.</span><span class="sxs-lookup"><span data-stu-id="b2ab8-154">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="b2ab8-155">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="b2ab8-155">RELATED LINKS</span></span>

[<span data-ttu-id="b2ab8-156">Add-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="b2ab8-156">Add-LocalGroupMember</span></span>](Add-LocalGroupMember.md)

[<span data-ttu-id="b2ab8-157">Get-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="b2ab8-157">Get-LocalGroupMember</span></span>](Get-LocalGroupMember.md)

[<span data-ttu-id="b2ab8-158">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="b2ab8-158">New-LocalGroup</span></span>](New-LocalGroup.md)
