---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/remove-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-LocalUser
ms.openlocfilehash: de1054971dab19f8cfae654208488ca9ce5e17e4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204105"
---
# <span data-ttu-id="58496-103">Remove-LocalUser</span><span class="sxs-lookup"><span data-stu-id="58496-103">Remove-LocalUser</span></span>

## <span data-ttu-id="58496-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="58496-104">SYNOPSIS</span></span>
<span data-ttu-id="58496-105">Supprime les comptes d’utilisateurs locaux.</span><span class="sxs-lookup"><span data-stu-id="58496-105">Deletes local user accounts.</span></span>

## <span data-ttu-id="58496-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="58496-106">SYNTAX</span></span>

### <span data-ttu-id="58496-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="58496-107">InputObject</span></span>

```
Remove-LocalUser [-InputObject] <LocalUser[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="58496-108">Default</span><span class="sxs-lookup"><span data-stu-id="58496-108">Default</span></span>

```
Remove-LocalUser [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="58496-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="58496-109">SecurityIdentifier</span></span>

```
Remove-LocalUser [-SID] <SecurityIdentifier[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="58496-110">Description</span><span class="sxs-lookup"><span data-stu-id="58496-110">DESCRIPTION</span></span>
<span data-ttu-id="58496-111">L’applet de commande **Remove-LocalUser** supprime les comptes d’utilisateur locaux.</span><span class="sxs-lookup"><span data-stu-id="58496-111">The **Remove-LocalUser** cmdlet deletes local user accounts.</span></span>

## <span data-ttu-id="58496-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="58496-112">EXAMPLES</span></span>

### <span data-ttu-id="58496-113">Exemple 1 : supprimer un compte d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="58496-113">Example 1: Delete a user account</span></span>

```
PS C:\> Remove-LocalUser -Name "AdminContoso02"
```

<span data-ttu-id="58496-114">Cette commande supprime le compte d’utilisateur nommé AdminContoso02.</span><span class="sxs-lookup"><span data-stu-id="58496-114">This command deletes the user account named AdminContoso02.</span></span>

> [!NOTE]
> <span data-ttu-id="58496-115">Le module Microsoft. PowerShell. LocalAccounts n’est pas disponible dans PowerShell 32 bits sur un système 64 bits.</span><span class="sxs-lookup"><span data-stu-id="58496-115">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="58496-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="58496-116">PARAMETERS</span></span>

### <span data-ttu-id="58496-117">-InputObject</span><span class="sxs-lookup"><span data-stu-id="58496-117">-InputObject</span></span>
<span data-ttu-id="58496-118">Spécifie un tableau de comptes d’utilisateur que cette applet de commande supprime.</span><span class="sxs-lookup"><span data-stu-id="58496-118">Specifies an array of user accounts that this cmdlet deletes.</span></span>
<span data-ttu-id="58496-119">Pour obtenir un compte d’utilisateur, utilisez l’applet de commande Get-LocalUser.</span><span class="sxs-lookup"><span data-stu-id="58496-119">To obtain a user account, use the Get-LocalUser cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalUser[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="58496-120">-Name</span><span class="sxs-lookup"><span data-stu-id="58496-120">-Name</span></span>
<span data-ttu-id="58496-121">Spécifie un tableau de noms des comptes d’utilisateur que cette applet de commande supprime.</span><span class="sxs-lookup"><span data-stu-id="58496-121">Specifies an array of names of the user accounts that this cmdlet deletes.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="58496-122">-SID</span><span class="sxs-lookup"><span data-stu-id="58496-122">-SID</span></span>
<span data-ttu-id="58496-123">Spécifie un tableau d’ID de sécurité (SID) des comptes d’utilisateur que cette applet de commande supprime.</span><span class="sxs-lookup"><span data-stu-id="58496-123">Specifies an array of security IDs (SIDs) of user accounts that this cmdlet deletes.</span></span>

```yaml
Type: System.Security.Principal.SecurityIdentifier[]
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="58496-124">-Confirm</span><span class="sxs-lookup"><span data-stu-id="58496-124">-Confirm</span></span>
<span data-ttu-id="58496-125">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="58496-125">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="58496-126">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="58496-126">-WhatIf</span></span>
<span data-ttu-id="58496-127">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="58496-127">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="58496-128">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="58496-128">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="58496-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="58496-129">CommonParameters</span></span>
<span data-ttu-id="58496-130">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="58496-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="58496-131">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="58496-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="58496-132">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="58496-132">INPUTS</span></span>

### <span data-ttu-id="58496-133">System. Management. Automation. SecurityAccountsManager. LocalUser, System. String, System. Security. principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="58496-133">System.Management.Automation.SecurityAccountsManager.LocalUser, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="58496-134">Vous pouvez diriger un utilisateur local, une chaîne ou un SID vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="58496-134">You can pipe a local user, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="58496-135">SORTIES</span><span class="sxs-lookup"><span data-stu-id="58496-135">OUTPUTS</span></span>

### <span data-ttu-id="58496-136">Aucun</span><span class="sxs-lookup"><span data-stu-id="58496-136">None</span></span>
<span data-ttu-id="58496-137">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="58496-137">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="58496-138">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="58496-138">NOTES</span></span>

* <span data-ttu-id="58496-139">La propriété **PrincipalSource** est une propriété des objets **LocalUser** , **LocalGroup** et **LocalPrincipal** qui décrit la source de l’objet.</span><span class="sxs-lookup"><span data-stu-id="58496-139">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="58496-140">Les sources possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="58496-140">The possible sources are as follows:</span></span>

- <span data-ttu-id="58496-141">Local</span><span class="sxs-lookup"><span data-stu-id="58496-141">Local</span></span>
- <span data-ttu-id="58496-142">Active Directory</span><span class="sxs-lookup"><span data-stu-id="58496-142">Active Directory</span></span>
- <span data-ttu-id="58496-143">Groupe Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="58496-143">Azure Active Directory group</span></span>
- <span data-ttu-id="58496-144">Compte Microsoft</span><span class="sxs-lookup"><span data-stu-id="58496-144">Microsoft Account</span></span>

<span data-ttu-id="58496-145">**PrincipalSource** est pris en charge uniquement par Windows 10, windows server 2016 et les versions ultérieures du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="58496-145">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="58496-146">Pour les versions antérieures, la propriété est vide.</span><span class="sxs-lookup"><span data-stu-id="58496-146">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="58496-147">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="58496-147">RELATED LINKS</span></span>

[<span data-ttu-id="58496-148">Disable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="58496-148">Disable-LocalUser</span></span>](Disable-LocalUser.md)

[<span data-ttu-id="58496-149">Enable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="58496-149">Enable-LocalUser</span></span>](Enable-LocalUser.md)

[<span data-ttu-id="58496-150">Get-LocalUser</span><span class="sxs-lookup"><span data-stu-id="58496-150">Get-LocalUser</span></span>](Get-LocalUser.md)

[<span data-ttu-id="58496-151">New-LocalUser</span><span class="sxs-lookup"><span data-stu-id="58496-151">New-LocalUser</span></span>](New-LocalUser.md)

[<span data-ttu-id="58496-152">Rename-LocalUser</span><span class="sxs-lookup"><span data-stu-id="58496-152">Rename-LocalUser</span></span>](Rename-LocalUser.md)

[<span data-ttu-id="58496-153">Set-LocalUser</span><span class="sxs-lookup"><span data-stu-id="58496-153">Set-LocalUser</span></span>](Set-LocalUser.md)
