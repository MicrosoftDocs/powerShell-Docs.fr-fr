---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/new-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-LocalGroup
ms.openlocfilehash: de66ad724d3cfee2d296d3b431618768a9cd38da
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203630"
---
# <span data-ttu-id="05988-103">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="05988-103">New-LocalGroup</span></span>

## <span data-ttu-id="05988-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="05988-104">SYNOPSIS</span></span>
<span data-ttu-id="05988-105">Crée un groupe de sécurité local.</span><span class="sxs-lookup"><span data-stu-id="05988-105">Creates a local security group.</span></span>

## <span data-ttu-id="05988-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="05988-106">SYNTAX</span></span>

```
New-LocalGroup [-Description <String>] [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="05988-107">Description</span><span class="sxs-lookup"><span data-stu-id="05988-107">DESCRIPTION</span></span>
<span data-ttu-id="05988-108">L’applet **de commande New-LocalGroup** crée un groupe de sécurité local dans le gestionnaire de comptes de sécurité.</span><span class="sxs-lookup"><span data-stu-id="05988-108">The **New-LocalGroup** cmdlet creates a local security group in the Security Account Manager.</span></span>

> [!NOTE]
> <span data-ttu-id="05988-109">Le module Microsoft. PowerShell. LocalAccounts n’est pas disponible dans PowerShell 32 bits sur un système 64 bits.</span><span class="sxs-lookup"><span data-stu-id="05988-109">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="05988-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="05988-110">EXAMPLES</span></span>

### <span data-ttu-id="05988-111">Exemple 1 : créer un groupe de sécurité</span><span class="sxs-lookup"><span data-stu-id="05988-111">Example 1: Create a security group</span></span>

```
PS C:\> New-LocalGroup -Name "SecurityGroup04"
```

<span data-ttu-id="05988-112">Cette commande crée un groupe nommé SecurityGroup04.</span><span class="sxs-lookup"><span data-stu-id="05988-112">This command creates a group named SecurityGroup04.</span></span>

## <span data-ttu-id="05988-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="05988-113">PARAMETERS</span></span>

### <span data-ttu-id="05988-114">Description</span><span class="sxs-lookup"><span data-stu-id="05988-114">-Description</span></span>
<span data-ttu-id="05988-115">Spécifie un commentaire pour le groupe.</span><span class="sxs-lookup"><span data-stu-id="05988-115">Specifies a comment for the group.</span></span>
<span data-ttu-id="05988-116">La longueur maximale est de 48 caractères.</span><span class="sxs-lookup"><span data-stu-id="05988-116">The maximum length is 48 characters.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="05988-117">-Name</span><span class="sxs-lookup"><span data-stu-id="05988-117">-Name</span></span>
<span data-ttu-id="05988-118">Spécifie un nom pour le groupe.</span><span class="sxs-lookup"><span data-stu-id="05988-118">Specifies a name for the group.</span></span>
<span data-ttu-id="05988-119">La longueur maximale est de 256 caractères.</span><span class="sxs-lookup"><span data-stu-id="05988-119">The maximum length is 256 characters.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="05988-120">-Confirm</span><span class="sxs-lookup"><span data-stu-id="05988-120">-Confirm</span></span>
<span data-ttu-id="05988-121">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="05988-121">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="05988-122">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="05988-122">-WhatIf</span></span>
<span data-ttu-id="05988-123">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="05988-123">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="05988-124">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="05988-124">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="05988-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="05988-125">CommonParameters</span></span>
<span data-ttu-id="05988-126">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="05988-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="05988-127">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="05988-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="05988-128">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="05988-128">INPUTS</span></span>

### <span data-ttu-id="05988-129">System.String</span><span class="sxs-lookup"><span data-stu-id="05988-129">System.String</span></span>
<span data-ttu-id="05988-130">Vous pouvez diriger une chaîne vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="05988-130">You can pipe a string to this cmdlet.</span></span>

## <span data-ttu-id="05988-131">SORTIES</span><span class="sxs-lookup"><span data-stu-id="05988-131">OUTPUTS</span></span>

### <span data-ttu-id="05988-132">System. Management. Automation. SecurityAccountsManager. LocalGroup</span><span class="sxs-lookup"><span data-stu-id="05988-132">System.Management.Automation.SecurityAccountsManager.LocalGroup</span></span>
<span data-ttu-id="05988-133">Cette applet de commande retourne un groupe de sécurité.</span><span class="sxs-lookup"><span data-stu-id="05988-133">This cmdlet returns a security group.</span></span>

## <span data-ttu-id="05988-134">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="05988-134">NOTES</span></span>

* <span data-ttu-id="05988-135">La propriété **PrincipalSource** est une propriété des objets **LocalUser** , **LocalGroup** et **LocalPrincipal** qui décrit la source de l’objet.</span><span class="sxs-lookup"><span data-stu-id="05988-135">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="05988-136">Les sources possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="05988-136">The possible sources are as follows:</span></span>

- <span data-ttu-id="05988-137">Local</span><span class="sxs-lookup"><span data-stu-id="05988-137">Local</span></span>
- <span data-ttu-id="05988-138">Active Directory</span><span class="sxs-lookup"><span data-stu-id="05988-138">Active Directory</span></span>
- <span data-ttu-id="05988-139">Groupe Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="05988-139">Azure Active Directory group</span></span>
- <span data-ttu-id="05988-140">Compte Microsoft</span><span class="sxs-lookup"><span data-stu-id="05988-140">Microsoft Account</span></span>

<span data-ttu-id="05988-141">**PrincipalSource** est pris en charge uniquement par Windows 10, windows server 2016 et les versions ultérieures du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="05988-141">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="05988-142">Pour les versions antérieures, la propriété est vide.</span><span class="sxs-lookup"><span data-stu-id="05988-142">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="05988-143">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="05988-143">RELATED LINKS</span></span>

[<span data-ttu-id="05988-144">Get-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="05988-144">Get-LocalGroup</span></span>](Get-LocalGroup.md)

[<span data-ttu-id="05988-145">Remove-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="05988-145">Remove-LocalGroup</span></span>](Remove-LocalGroup.md)

[<span data-ttu-id="05988-146">Rename-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="05988-146">Rename-LocalGroup</span></span>](Rename-LocalGroup.md)

[<span data-ttu-id="05988-147">Set-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="05988-147">Set-LocalGroup</span></span>](Set-LocalGroup.md)
