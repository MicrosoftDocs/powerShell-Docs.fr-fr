---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/disable-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-LocalUser
ms.openlocfilehash: a62242251da00688d3299c60e4cdae7aae6f581a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202249"
---
# <span data-ttu-id="be337-103">Disable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="be337-103">Disable-LocalUser</span></span>

## <span data-ttu-id="be337-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="be337-104">SYNOPSIS</span></span>
<span data-ttu-id="be337-105">Désactive un compte d’utilisateur local.</span><span class="sxs-lookup"><span data-stu-id="be337-105">Disables a local user account.</span></span>

## <span data-ttu-id="be337-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="be337-106">SYNTAX</span></span>

### <span data-ttu-id="be337-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="be337-107">InputObject</span></span>

```
Disable-LocalUser [-InputObject] <LocalUser[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="be337-108">Default</span><span class="sxs-lookup"><span data-stu-id="be337-108">Default</span></span>

```
Disable-LocalUser [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="be337-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="be337-109">SecurityIdentifier</span></span>

```
Disable-LocalUser [-SID] <SecurityIdentifier[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="be337-110">Description</span><span class="sxs-lookup"><span data-stu-id="be337-110">DESCRIPTION</span></span>
<span data-ttu-id="be337-111">L’applet **de commande Disable-LocalUser désactive les** comptes d’utilisateur locaux.</span><span class="sxs-lookup"><span data-stu-id="be337-111">The **Disable-LocalUser** cmdlet disables local user accounts.</span></span>
<span data-ttu-id="be337-112">Lorsqu’un compte d’utilisateur est désactivé, l’utilisateur ne peut pas ouvrir de session.</span><span class="sxs-lookup"><span data-stu-id="be337-112">When a user account is disabled, the user cannot log on.</span></span>
<span data-ttu-id="be337-113">Lorsqu’un compte d’utilisateur est activé, l’utilisateur peut ouvrir une session.</span><span class="sxs-lookup"><span data-stu-id="be337-113">When a user account is enabled, the user can log on.</span></span>

> [!NOTE]
> <span data-ttu-id="be337-114">Le module Microsoft. PowerShell. LocalAccounts n’est pas disponible dans PowerShell 32 bits sur un système 64 bits.</span><span class="sxs-lookup"><span data-stu-id="be337-114">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="be337-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="be337-115">EXAMPLES</span></span>

### <span data-ttu-id="be337-116">Exemple 1 : désactiver un compte en spécifiant un nom</span><span class="sxs-lookup"><span data-stu-id="be337-116">Example 1: Disable an account by specifying a name</span></span>

```
PS C:\> Disable-LocalUser -Name "Admin02"
```

<span data-ttu-id="be337-117">Cette commande désactive le compte d’utilisateur nommé admin02.</span><span class="sxs-lookup"><span data-stu-id="be337-117">This command disables the user account named Admin02.</span></span>

### <span data-ttu-id="be337-118">Exemple 2 : désactiver un compte à l’aide du pipeline</span><span class="sxs-lookup"><span data-stu-id="be337-118">Example 2: Disable an account by using the pipeline</span></span>

```
PS C:\> Get-LocalUser Guest | Disable-LocalUser
```

<span data-ttu-id="be337-119">Cette commande obtient le compte invité intégré à l’aide de la commande **obtenir-LocalUser** , puis le passe à l’applet de commande en cours à l’aide de l’opérateur Pipeline.</span><span class="sxs-lookup"><span data-stu-id="be337-119">This command gets the built-in Guest account by using **Get-LocalUser** , and then passes it to the current cmdlet by using the pipeline operator.</span></span>
<span data-ttu-id="be337-120">Cette applet de commande désactive ce compte.</span><span class="sxs-lookup"><span data-stu-id="be337-120">That cmdlet disables that account.</span></span>

## <span data-ttu-id="be337-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="be337-121">PARAMETERS</span></span>

### <span data-ttu-id="be337-122">-InputObject</span><span class="sxs-lookup"><span data-stu-id="be337-122">-InputObject</span></span>
<span data-ttu-id="be337-123">Spécifie un tableau de comptes d’utilisateur que cette applet de commande désactive.</span><span class="sxs-lookup"><span data-stu-id="be337-123">Specifies an array of user accounts that this cmdlet disables.</span></span>
<span data-ttu-id="be337-124">Pour obtenir un compte d’utilisateur, utilisez l’applet de commande Get-LocalUser.</span><span class="sxs-lookup"><span data-stu-id="be337-124">To obtain a user account, use the Get-LocalUser cmdlet.</span></span>

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

### <span data-ttu-id="be337-125">-Name</span><span class="sxs-lookup"><span data-stu-id="be337-125">-Name</span></span>
<span data-ttu-id="be337-126">Spécifie un tableau de noms des comptes d’utilisateur que cette applet de commande désactive.</span><span class="sxs-lookup"><span data-stu-id="be337-126">Specifies an array of names of the user accounts that this cmdlet disables.</span></span>

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

### <span data-ttu-id="be337-127">-SID</span><span class="sxs-lookup"><span data-stu-id="be337-127">-SID</span></span>
<span data-ttu-id="be337-128">Spécifie un tableau de comptes d’utilisateur que cette applet de commande désactive.</span><span class="sxs-lookup"><span data-stu-id="be337-128">Specifies an array of user accounts that this cmdlet disables.</span></span>

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

### <span data-ttu-id="be337-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="be337-129">-Confirm</span></span>
<span data-ttu-id="be337-130">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="be337-130">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="be337-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="be337-131">-WhatIf</span></span>
<span data-ttu-id="be337-132">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="be337-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="be337-133">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="be337-133">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="be337-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="be337-134">CommonParameters</span></span>
<span data-ttu-id="be337-135">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="be337-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="be337-136">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="be337-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="be337-137">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="be337-137">INPUTS</span></span>

### <span data-ttu-id="be337-138">System. Management. Automation. SecurityAccountsManager. LocalUser, System. String, System. Security. principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="be337-138">System.Management.Automation.SecurityAccountsManager.LocalUser, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="be337-139">Vous pouvez diriger un utilisateur local, une chaîne ou un SID vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="be337-139">You can pipe a local user, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="be337-140">SORTIES</span><span class="sxs-lookup"><span data-stu-id="be337-140">OUTPUTS</span></span>

### <span data-ttu-id="be337-141">Aucun</span><span class="sxs-lookup"><span data-stu-id="be337-141">None</span></span>
<span data-ttu-id="be337-142">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="be337-142">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="be337-143">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="be337-143">NOTES</span></span>

* <span data-ttu-id="be337-144">La propriété **PrincipalSource** est une propriété des objets **LocalUser** , **LocalGroup** et **LocalPrincipal** qui décrit la source de l’objet.</span><span class="sxs-lookup"><span data-stu-id="be337-144">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="be337-145">Les sources possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="be337-145">The possible sources are as follows:</span></span>

- <span data-ttu-id="be337-146">Local</span><span class="sxs-lookup"><span data-stu-id="be337-146">Local</span></span>
- <span data-ttu-id="be337-147">Active Directory</span><span class="sxs-lookup"><span data-stu-id="be337-147">Active Directory</span></span>
- <span data-ttu-id="be337-148">Groupe Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="be337-148">Azure Active Directory group</span></span>
- <span data-ttu-id="be337-149">Compte Microsoft</span><span class="sxs-lookup"><span data-stu-id="be337-149">Microsoft Account</span></span>

<span data-ttu-id="be337-150">**PrincipalSource** est pris en charge uniquement par Windows 10, windows server 2016 et les versions ultérieures du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="be337-150">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="be337-151">Pour les versions antérieures, la propriété est vide.</span><span class="sxs-lookup"><span data-stu-id="be337-151">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="be337-152">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="be337-152">RELATED LINKS</span></span>

[<span data-ttu-id="be337-153">Enable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="be337-153">Enable-LocalUser</span></span>](Enable-LocalUser.md)

[<span data-ttu-id="be337-154">Get-LocalUser</span><span class="sxs-lookup"><span data-stu-id="be337-154">Get-LocalUser</span></span>](Get-LocalUser.md)

[<span data-ttu-id="be337-155">New-LocalUser</span><span class="sxs-lookup"><span data-stu-id="be337-155">New-LocalUser</span></span>](New-LocalUser.md)

[<span data-ttu-id="be337-156">Remove-LocalUser</span><span class="sxs-lookup"><span data-stu-id="be337-156">Remove-LocalUser</span></span>](Remove-LocalUser.md)

[<span data-ttu-id="be337-157">Rename-LocalUser</span><span class="sxs-lookup"><span data-stu-id="be337-157">Rename-LocalUser</span></span>](Rename-LocalUser.md)

[<span data-ttu-id="be337-158">Set-LocalUser</span><span class="sxs-lookup"><span data-stu-id="be337-158">Set-LocalUser</span></span>](Set-LocalUser.md)
