---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/rename-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-LocalUser
ms.openlocfilehash: fc5740e52e08ad2146981799a4e1659cd420b321
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204102"
---
# <span data-ttu-id="98573-103">Rename-LocalUser</span><span class="sxs-lookup"><span data-stu-id="98573-103">Rename-LocalUser</span></span>

## <span data-ttu-id="98573-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="98573-104">SYNOPSIS</span></span>
<span data-ttu-id="98573-105">Renomme un compte d’utilisateur local.</span><span class="sxs-lookup"><span data-stu-id="98573-105">Renames a local user account.</span></span>

## <span data-ttu-id="98573-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="98573-106">SYNTAX</span></span>

### <span data-ttu-id="98573-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="98573-107">InputObject</span></span>

```
Rename-LocalUser [-InputObject] <LocalUser> [-NewName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="98573-108">Default</span><span class="sxs-lookup"><span data-stu-id="98573-108">Default</span></span>

```
Rename-LocalUser [-Name] <String> [-NewName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="98573-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="98573-109">SecurityIdentifier</span></span>

```
Rename-LocalUser [-NewName] <String> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="98573-110">Description</span><span class="sxs-lookup"><span data-stu-id="98573-110">DESCRIPTION</span></span>
<span data-ttu-id="98573-111">L’applet de commande **Rename-LocalUser** renomme un compte d’utilisateur local.</span><span class="sxs-lookup"><span data-stu-id="98573-111">The **Rename-LocalUser** cmdlet renames a local user account.</span></span>

> [!NOTE]
> <span data-ttu-id="98573-112">Le module Microsoft. PowerShell. LocalAccounts n’est pas disponible dans PowerShell 32 bits sur un système 64 bits.</span><span class="sxs-lookup"><span data-stu-id="98573-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="98573-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="98573-113">EXAMPLES</span></span>

### <span data-ttu-id="98573-114">Exemple 1 : renommer un compte d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="98573-114">Example 1: Rename a user account</span></span>

```
PS C:\> Rename-LocalUser -Name "Admin02" -NewName "AdminContoso02"
```

<span data-ttu-id="98573-115">Cette commande renomme le compte d’utilisateur nommé admin02.</span><span class="sxs-lookup"><span data-stu-id="98573-115">This command renames the user account named Admin02.</span></span>

## <span data-ttu-id="98573-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="98573-116">PARAMETERS</span></span>

### <span data-ttu-id="98573-117">-InputObject</span><span class="sxs-lookup"><span data-stu-id="98573-117">-InputObject</span></span>
<span data-ttu-id="98573-118">Spécifie le compte d’utilisateur que cette applet de commande renomme.</span><span class="sxs-lookup"><span data-stu-id="98573-118">Specifies the user account that this cmdlet renames.</span></span>
<span data-ttu-id="98573-119">Pour obtenir un compte d’utilisateur, utilisez l’applet de commande Get-LocalUser.</span><span class="sxs-lookup"><span data-stu-id="98573-119">To obtain a user account, use the Get-LocalUser cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalUser
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="98573-120">-Name</span><span class="sxs-lookup"><span data-stu-id="98573-120">-Name</span></span>
<span data-ttu-id="98573-121">Spécifie le nom du compte d’utilisateur que cette applet de commande renomme.</span><span class="sxs-lookup"><span data-stu-id="98573-121">Specifies the name of the user account that this cmdlet renames.</span></span>

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

### <span data-ttu-id="98573-122">-NewName</span><span class="sxs-lookup"><span data-stu-id="98573-122">-NewName</span></span>
<span data-ttu-id="98573-123">Spécifie un nouveau nom pour le compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="98573-123">Specifies a new name for the user account.</span></span>

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

### <span data-ttu-id="98573-124">-SID</span><span class="sxs-lookup"><span data-stu-id="98573-124">-SID</span></span>
<span data-ttu-id="98573-125">Spécifie l’ID de sécurité (SID) d’un compte d’utilisateur que cette applet de commande renomme.</span><span class="sxs-lookup"><span data-stu-id="98573-125">Specifies the security ID (SID) of a user accounts that this cmdlet renames.</span></span>

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

### <span data-ttu-id="98573-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="98573-126">-Confirm</span></span>
<span data-ttu-id="98573-127">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="98573-127">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="98573-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="98573-128">-WhatIf</span></span>
<span data-ttu-id="98573-129">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="98573-129">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="98573-130">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="98573-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="98573-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="98573-131">CommonParameters</span></span>
<span data-ttu-id="98573-132">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="98573-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="98573-133">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="98573-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="98573-134">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="98573-134">INPUTS</span></span>

### <span data-ttu-id="98573-135">System. Management. Automation. SecurityAccountsManager. LocalUser, System. String, System. Security. principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="98573-135">System.Management.Automation.SecurityAccountsManager.LocalUser, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="98573-136">Vous pouvez diriger un utilisateur local, une chaîne ou un SID vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="98573-136">You can pipe a local user, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="98573-137">SORTIES</span><span class="sxs-lookup"><span data-stu-id="98573-137">OUTPUTS</span></span>

### <span data-ttu-id="98573-138">Aucun</span><span class="sxs-lookup"><span data-stu-id="98573-138">None</span></span>
<span data-ttu-id="98573-139">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="98573-139">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="98573-140">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="98573-140">NOTES</span></span>

* <span data-ttu-id="98573-141">La propriété **PrincipalSource** est une propriété des objets **LocalUser** , **LocalGroup** et **LocalPrincipal** qui décrit la source de l’objet.</span><span class="sxs-lookup"><span data-stu-id="98573-141">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="98573-142">Les sources possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="98573-142">The possible sources are as follows:</span></span>

- <span data-ttu-id="98573-143">Local</span><span class="sxs-lookup"><span data-stu-id="98573-143">Local</span></span>
- <span data-ttu-id="98573-144">Active Directory</span><span class="sxs-lookup"><span data-stu-id="98573-144">Active Directory</span></span>
- <span data-ttu-id="98573-145">Groupe Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="98573-145">Azure Active Directory group</span></span>
- <span data-ttu-id="98573-146">Compte Microsoft</span><span class="sxs-lookup"><span data-stu-id="98573-146">Microsoft Account</span></span>

<span data-ttu-id="98573-147">**PrincipalSource** est pris en charge uniquement par Windows 10, windows server 2016 et les versions ultérieures du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="98573-147">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="98573-148">Pour les versions antérieures, la propriété est vide.</span><span class="sxs-lookup"><span data-stu-id="98573-148">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="98573-149">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="98573-149">RELATED LINKS</span></span>

[<span data-ttu-id="98573-150">Disable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="98573-150">Disable-LocalUser</span></span>](Disable-LocalUser.md)

[<span data-ttu-id="98573-151">Enable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="98573-151">Enable-LocalUser</span></span>](Enable-LocalUser.md)

[<span data-ttu-id="98573-152">Get-LocalUser</span><span class="sxs-lookup"><span data-stu-id="98573-152">Get-LocalUser</span></span>](Get-LocalUser.md)

[<span data-ttu-id="98573-153">New-LocalUser</span><span class="sxs-lookup"><span data-stu-id="98573-153">New-LocalUser</span></span>](New-LocalUser.md)

[<span data-ttu-id="98573-154">Remove-LocalUser</span><span class="sxs-lookup"><span data-stu-id="98573-154">Remove-LocalUser</span></span>](Remove-LocalUser.md)

[<span data-ttu-id="98573-155">Set-LocalUser</span><span class="sxs-lookup"><span data-stu-id="98573-155">Set-LocalUser</span></span>](Set-LocalUser.md)
