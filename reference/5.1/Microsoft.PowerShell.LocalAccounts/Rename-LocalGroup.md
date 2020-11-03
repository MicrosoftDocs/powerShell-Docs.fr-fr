---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/rename-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-LocalGroup
ms.openlocfilehash: 566d33bdeb52323cca41fa9757d36334b40f1654
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204098"
---
# <span data-ttu-id="dd9d3-103">Rename-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="dd9d3-103">Rename-LocalGroup</span></span>

## <span data-ttu-id="dd9d3-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="dd9d3-104">SYNOPSIS</span></span>
<span data-ttu-id="dd9d3-105">Renomme un groupe de sécurité local.</span><span class="sxs-lookup"><span data-stu-id="dd9d3-105">Renames a local security group.</span></span>

## <span data-ttu-id="dd9d3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dd9d3-106">SYNTAX</span></span>

### <span data-ttu-id="dd9d3-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="dd9d3-107">InputObject</span></span>

```
Rename-LocalGroup [-InputObject] <LocalGroup> [-NewName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="dd9d3-108">Default</span><span class="sxs-lookup"><span data-stu-id="dd9d3-108">Default</span></span>

```
Rename-LocalGroup [-Name] <String> [-NewName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="dd9d3-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="dd9d3-109">SecurityIdentifier</span></span>

```
Rename-LocalGroup [-NewName] <String> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="dd9d3-110">Description</span><span class="sxs-lookup"><span data-stu-id="dd9d3-110">DESCRIPTION</span></span>
<span data-ttu-id="dd9d3-111">L’applet de commande **Rename-LocalGroup** renomme un groupe de sécurité local.</span><span class="sxs-lookup"><span data-stu-id="dd9d3-111">The **Rename-LocalGroup** cmdlet renames a local security group.</span></span>

> [!NOTE]
> <span data-ttu-id="dd9d3-112">Le module Microsoft. PowerShell. LocalAccounts n’est pas disponible dans PowerShell 32 bits sur un système 64 bits.</span><span class="sxs-lookup"><span data-stu-id="dd9d3-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="dd9d3-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="dd9d3-113">EXAMPLES</span></span>

### <span data-ttu-id="dd9d3-114">Exemple 1 : modifier le nom d’un groupe</span><span class="sxs-lookup"><span data-stu-id="dd9d3-114">Example 1: Change the name of a group</span></span>

```
PS C:\> Rename-LocalGroup -Name "SecurityGroup" -NewName "SecurityGroup04"
```

<span data-ttu-id="dd9d3-115">Cette commande renomme un groupe de sécurité nommé SecurityGroup.</span><span class="sxs-lookup"><span data-stu-id="dd9d3-115">This command renames a security group named SecurityGroup.</span></span>

## <span data-ttu-id="dd9d3-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="dd9d3-116">PARAMETERS</span></span>

### <span data-ttu-id="dd9d3-117">-InputObject</span><span class="sxs-lookup"><span data-stu-id="dd9d3-117">-InputObject</span></span>
<span data-ttu-id="dd9d3-118">Spécifie le groupe de sécurité que cette applet de commande renomme.</span><span class="sxs-lookup"><span data-stu-id="dd9d3-118">Specifies the security group that this cmdlet renames.</span></span>
<span data-ttu-id="dd9d3-119">Pour obtenir un groupe de sécurité, utilisez l’applet de commande Get-LocalGroup.</span><span class="sxs-lookup"><span data-stu-id="dd9d3-119">To obtain a security group, use the Get-LocalGroup cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="dd9d3-120">-Name</span><span class="sxs-lookup"><span data-stu-id="dd9d3-120">-Name</span></span>
<span data-ttu-id="dd9d3-121">Spécifie le nom du groupe de sécurité que cette applet de commande renomme.</span><span class="sxs-lookup"><span data-stu-id="dd9d3-121">Specifies the name of the security group that this cmdlet renames.</span></span>

```yaml
Type: System.String
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="dd9d3-122">-NewName</span><span class="sxs-lookup"><span data-stu-id="dd9d3-122">-NewName</span></span>
<span data-ttu-id="dd9d3-123">Spécifie un nouveau nom pour le groupe de sécurité.</span><span class="sxs-lookup"><span data-stu-id="dd9d3-123">Specifies a new name for the security group.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dd9d3-124">-SID</span><span class="sxs-lookup"><span data-stu-id="dd9d3-124">-SID</span></span>
<span data-ttu-id="dd9d3-125">Spécifie l’ID de sécurité (SID) d’un groupe de sécurité que cette applet de commande renomme.</span><span class="sxs-lookup"><span data-stu-id="dd9d3-125">Specifies the security ID (SID) of a security group that this cmdlet renames.</span></span>

```yaml
Type: System.Security.Principal.SecurityIdentifier
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="dd9d3-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="dd9d3-126">-Confirm</span></span>
<span data-ttu-id="dd9d3-127">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="dd9d3-127">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="dd9d3-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="dd9d3-128">-WhatIf</span></span>
<span data-ttu-id="dd9d3-129">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="dd9d3-129">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="dd9d3-130">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="dd9d3-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="dd9d3-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dd9d3-131">CommonParameters</span></span>
<span data-ttu-id="dd9d3-132">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="dd9d3-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dd9d3-133">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="dd9d3-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="dd9d3-134">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="dd9d3-134">INPUTS</span></span>

### <span data-ttu-id="dd9d3-135">System. Management. Automation. SecurityAccountsManager. LocalGroup, System. String, System. Security. principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="dd9d3-135">System.Management.Automation.SecurityAccountsManager.LocalGroup, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="dd9d3-136">Vous pouvez diriger un groupe de sécurité, une chaîne ou un SID vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="dd9d3-136">You can pipe a security group, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="dd9d3-137">SORTIES</span><span class="sxs-lookup"><span data-stu-id="dd9d3-137">OUTPUTS</span></span>

### <span data-ttu-id="dd9d3-138">Aucun</span><span class="sxs-lookup"><span data-stu-id="dd9d3-138">None</span></span>
<span data-ttu-id="dd9d3-139">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="dd9d3-139">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="dd9d3-140">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="dd9d3-140">NOTES</span></span>

* <span data-ttu-id="dd9d3-141">La propriété **PrincipalSource** est une propriété des objets **LocalUser** , **LocalGroup** et **LocalPrincipal** qui décrit la source de l’objet.</span><span class="sxs-lookup"><span data-stu-id="dd9d3-141">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="dd9d3-142">Les sources possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="dd9d3-142">The possible sources are as follows:</span></span>

- <span data-ttu-id="dd9d3-143">Local</span><span class="sxs-lookup"><span data-stu-id="dd9d3-143">Local</span></span>
- <span data-ttu-id="dd9d3-144">Active Directory</span><span class="sxs-lookup"><span data-stu-id="dd9d3-144">Active Directory</span></span>
- <span data-ttu-id="dd9d3-145">Groupe Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="dd9d3-145">Azure Active Directory group</span></span>
- <span data-ttu-id="dd9d3-146">Compte Microsoft</span><span class="sxs-lookup"><span data-stu-id="dd9d3-146">Microsoft Account</span></span>

<span data-ttu-id="dd9d3-147">**PrincipalSource** est pris en charge uniquement par Windows 10, windows server 2016 et les versions ultérieures du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="dd9d3-147">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="dd9d3-148">Pour les versions antérieures, la propriété est vide.</span><span class="sxs-lookup"><span data-stu-id="dd9d3-148">For earlier  versions, the property is blank.</span></span>

## <span data-ttu-id="dd9d3-149">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="dd9d3-149">RELATED LINKS</span></span>

[<span data-ttu-id="dd9d3-150">Get-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="dd9d3-150">Get-LocalGroup</span></span>](Get-LocalGroup.md)

[<span data-ttu-id="dd9d3-151">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="dd9d3-151">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="dd9d3-152">Remove-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="dd9d3-152">Remove-LocalGroup</span></span>](Remove-LocalGroup.md)

[<span data-ttu-id="dd9d3-153">Set-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="dd9d3-153">Set-LocalGroup</span></span>](Set-LocalGroup.md)
