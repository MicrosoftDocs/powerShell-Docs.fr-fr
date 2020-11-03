---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/set-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-LocalGroup
ms.openlocfilehash: 471c3c7bc01bf26dfe9d8eec26e4414464cae02e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204101"
---
# <span data-ttu-id="49ebf-103">Set-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="49ebf-103">Set-LocalGroup</span></span>

## <span data-ttu-id="49ebf-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="49ebf-104">SYNOPSIS</span></span>
<span data-ttu-id="49ebf-105">Modifie un groupe de sécurité local.</span><span class="sxs-lookup"><span data-stu-id="49ebf-105">Changes a local security group.</span></span>

## <span data-ttu-id="49ebf-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="49ebf-106">SYNTAX</span></span>

### <span data-ttu-id="49ebf-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="49ebf-107">InputObject</span></span>

```
Set-LocalGroup -Description <String> [-InputObject] <LocalGroup> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="49ebf-108">Default</span><span class="sxs-lookup"><span data-stu-id="49ebf-108">Default</span></span>

```
Set-LocalGroup -Description <String> [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="49ebf-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="49ebf-109">SecurityIdentifier</span></span>

```
Set-LocalGroup -Description <String> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="49ebf-110">Description</span><span class="sxs-lookup"><span data-stu-id="49ebf-110">DESCRIPTION</span></span>
<span data-ttu-id="49ebf-111">L’applet de commande **Set-LocalGroup** modifie un groupe de sécurité local.</span><span class="sxs-lookup"><span data-stu-id="49ebf-111">The **Set-LocalGroup** cmdlet changes a local security group.</span></span>

## <span data-ttu-id="49ebf-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="49ebf-112">EXAMPLES</span></span>

### <span data-ttu-id="49ebf-113">Exemple 1 : modifier la description d’un groupe</span><span class="sxs-lookup"><span data-stu-id="49ebf-113">Example 1: Change a group description</span></span>

```
PS C:\> Set-LocalGroup -Name "SecurityGroup04" -Description "This is a sample description."
```

<span data-ttu-id="49ebf-114">Cette commande modifie la description d’un groupe local.</span><span class="sxs-lookup"><span data-stu-id="49ebf-114">This command changes the description of a local group.</span></span>

> [!NOTE]
> <span data-ttu-id="49ebf-115">Le module Microsoft. PowerShell. LocalAccounts n’est pas disponible dans PowerShell 32 bits sur un système 64 bits.</span><span class="sxs-lookup"><span data-stu-id="49ebf-115">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="49ebf-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="49ebf-116">PARAMETERS</span></span>

### <span data-ttu-id="49ebf-117">Description</span><span class="sxs-lookup"><span data-stu-id="49ebf-117">-Description</span></span>
<span data-ttu-id="49ebf-118">Spécifie un commentaire pour le groupe.</span><span class="sxs-lookup"><span data-stu-id="49ebf-118">Specifies a comment for the group.</span></span>
<span data-ttu-id="49ebf-119">La longueur maximale est de 48 caractères.</span><span class="sxs-lookup"><span data-stu-id="49ebf-119">The maximum length is 48 characters.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49ebf-120">-InputObject</span><span class="sxs-lookup"><span data-stu-id="49ebf-120">-InputObject</span></span>
<span data-ttu-id="49ebf-121">Spécifie le groupe de sécurité que cette applet de commande modifie.</span><span class="sxs-lookup"><span data-stu-id="49ebf-121">Specifies the security group that this cmdlet changes.</span></span>
<span data-ttu-id="49ebf-122">Pour obtenir un groupe de sécurité, utilisez l’applet de commande Get-LocalGroup.</span><span class="sxs-lookup"><span data-stu-id="49ebf-122">To obtain a security group, use the Get-LocalGroup cmdlet.</span></span>

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

### <span data-ttu-id="49ebf-123">-Name</span><span class="sxs-lookup"><span data-stu-id="49ebf-123">-Name</span></span>
<span data-ttu-id="49ebf-124">Spécifie le nom du groupe de sécurité que cette applet de commande modifie.</span><span class="sxs-lookup"><span data-stu-id="49ebf-124">Specifies the name of the security group that this cmdlet changes.</span></span>

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

### <span data-ttu-id="49ebf-125">-SID</span><span class="sxs-lookup"><span data-stu-id="49ebf-125">-SID</span></span>
<span data-ttu-id="49ebf-126">Spécifie l’ID de sécurité (SID) du groupe de sécurité que cette applet de commande modifie.</span><span class="sxs-lookup"><span data-stu-id="49ebf-126">Specifies the security ID (SID) of the security group that this cmdlet changes.</span></span>

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

### <span data-ttu-id="49ebf-127">-Confirm</span><span class="sxs-lookup"><span data-stu-id="49ebf-127">-Confirm</span></span>
<span data-ttu-id="49ebf-128">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="49ebf-128">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="49ebf-129">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="49ebf-129">-WhatIf</span></span>
<span data-ttu-id="49ebf-130">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="49ebf-130">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="49ebf-131">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="49ebf-131">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="49ebf-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="49ebf-132">CommonParameters</span></span>
<span data-ttu-id="49ebf-133">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="49ebf-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="49ebf-134">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="49ebf-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="49ebf-135">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="49ebf-135">INPUTS</span></span>

### <span data-ttu-id="49ebf-136">System. Management. Automation. SecurityAccountsManager. LocalGroup, System. String, System. Security. principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="49ebf-136">System.Management.Automation.SecurityAccountsManager.LocalGroup, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="49ebf-137">Vous pouvez diriger un groupe de sécurité, une chaîne ou un SID vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="49ebf-137">You can pipe a security group, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="49ebf-138">SORTIES</span><span class="sxs-lookup"><span data-stu-id="49ebf-138">OUTPUTS</span></span>

### <span data-ttu-id="49ebf-139">Aucun</span><span class="sxs-lookup"><span data-stu-id="49ebf-139">None</span></span>
<span data-ttu-id="49ebf-140">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="49ebf-140">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="49ebf-141">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="49ebf-141">NOTES</span></span>

* <span data-ttu-id="49ebf-142">La propriété **PrincipalSource** est une propriété des objets **LocalUser** , **LocalGroup** et **LocalPrincipal** qui décrit la source de l’objet.</span><span class="sxs-lookup"><span data-stu-id="49ebf-142">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="49ebf-143">Les sources possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="49ebf-143">The possible sources are as follows:</span></span>

- <span data-ttu-id="49ebf-144">Local</span><span class="sxs-lookup"><span data-stu-id="49ebf-144">Local</span></span>
- <span data-ttu-id="49ebf-145">Active Directory</span><span class="sxs-lookup"><span data-stu-id="49ebf-145">Active Directory</span></span>
- <span data-ttu-id="49ebf-146">Groupe Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="49ebf-146">Azure Active Directory group</span></span>
- <span data-ttu-id="49ebf-147">Compte Microsoft</span><span class="sxs-lookup"><span data-stu-id="49ebf-147">Microsoft Account</span></span>

<span data-ttu-id="49ebf-148">**PrincipalSource** est pris en charge uniquement par Windows 10, windows server 2016 et les versions ultérieures du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="49ebf-148">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="49ebf-149">Pour les versions antérieures, la propriété est vide.</span><span class="sxs-lookup"><span data-stu-id="49ebf-149">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="49ebf-150">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="49ebf-150">RELATED LINKS</span></span>

[<span data-ttu-id="49ebf-151">Get-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="49ebf-151">Get-LocalGroup</span></span>](Get-LocalGroup.md)

[<span data-ttu-id="49ebf-152">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="49ebf-152">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="49ebf-153">Remove-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="49ebf-153">Remove-LocalGroup</span></span>](Remove-LocalGroup.md)

[<span data-ttu-id="49ebf-154">Rename-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="49ebf-154">Rename-LocalGroup</span></span>](Rename-LocalGroup.md)
