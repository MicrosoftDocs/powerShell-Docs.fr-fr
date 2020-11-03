---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/remove-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-LocalGroup
ms.openlocfilehash: 6a2f921972fef1794581b301df6e7439e56c7f47
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203625"
---
# <span data-ttu-id="6850e-103">Remove-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="6850e-103">Remove-LocalGroup</span></span>

## <span data-ttu-id="6850e-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="6850e-104">SYNOPSIS</span></span>
<span data-ttu-id="6850e-105">Supprime les groupes de sécurité locaux.</span><span class="sxs-lookup"><span data-stu-id="6850e-105">Deletes local security groups.</span></span>

## <span data-ttu-id="6850e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6850e-106">SYNTAX</span></span>

### <span data-ttu-id="6850e-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="6850e-107">InputObject</span></span>

```
Remove-LocalGroup [-InputObject] <LocalGroup[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6850e-108">Default</span><span class="sxs-lookup"><span data-stu-id="6850e-108">Default</span></span>

```
Remove-LocalGroup [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6850e-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="6850e-109">SecurityIdentifier</span></span>

```
Remove-LocalGroup [-SID] <SecurityIdentifier[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6850e-110">Description</span><span class="sxs-lookup"><span data-stu-id="6850e-110">DESCRIPTION</span></span>
<span data-ttu-id="6850e-111">L’applet de commande **Remove-LocalGroup** supprime les groupes de sécurité locaux.</span><span class="sxs-lookup"><span data-stu-id="6850e-111">The **Remove-LocalGroup** cmdlet deletes local security groups.</span></span>
<span data-ttu-id="6850e-112">Cette applet de commande supprime uniquement un groupe local.</span><span class="sxs-lookup"><span data-stu-id="6850e-112">This cmdlet deletes only a local group.</span></span>
<span data-ttu-id="6850e-113">Elle ne supprime pas les comptes d’utilisateur, les comptes d’ordinateurs ou les comptes de groupe qui appartiennent à ce groupe.</span><span class="sxs-lookup"><span data-stu-id="6850e-113">It does not delete the user accounts, computer accounts, or group accounts that belong to that group.</span></span>
<span data-ttu-id="6850e-114">Vous ne pouvez pas récupérer un groupe supprimé.</span><span class="sxs-lookup"><span data-stu-id="6850e-114">You cannot recover a deleted group.</span></span>

<span data-ttu-id="6850e-115">Si vous supprimez un groupe, puis créez un autre groupe qui porte le même nom de groupe, vous devez définir de nouvelles autorisations pour le nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="6850e-115">If you delete a group and then create another group that has the same group name, you must set new permissions for the new group.</span></span>
<span data-ttu-id="6850e-116">Le nouveau groupe n’hérite pas des autorisations qui ont été affectées au groupe.</span><span class="sxs-lookup"><span data-stu-id="6850e-116">The new group does not inherit the permissions that were assigned to the group.</span></span>

> [!NOTE]
> <span data-ttu-id="6850e-117">Le module Microsoft. PowerShell. LocalAccounts n’est pas disponible dans PowerShell 32 bits sur un système 64 bits.</span><span class="sxs-lookup"><span data-stu-id="6850e-117">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="6850e-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="6850e-118">EXAMPLES</span></span>

### <span data-ttu-id="6850e-119">Exemple 1 : supprimer un groupe de sécurité</span><span class="sxs-lookup"><span data-stu-id="6850e-119">Example 1: Delete a security group</span></span>

```
PS C:\> Remove-LocalGroup -Name "SecurityGroup04"
```

<span data-ttu-id="6850e-120">Cette commande supprime le groupe nommé SecurityGroup04.</span><span class="sxs-lookup"><span data-stu-id="6850e-120">This command deletes the group named SecurityGroup04.</span></span>

## <span data-ttu-id="6850e-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6850e-121">PARAMETERS</span></span>

### <span data-ttu-id="6850e-122">-InputObject</span><span class="sxs-lookup"><span data-stu-id="6850e-122">-InputObject</span></span>
<span data-ttu-id="6850e-123">Spécifie un tableau de groupes de sécurité que cette applet de commande supprime.</span><span class="sxs-lookup"><span data-stu-id="6850e-123">Specifies an array of security groups that this cmdlet deletes.</span></span>
<span data-ttu-id="6850e-124">Pour obtenir des groupes, utilisez l’applet de commande Get-LocalGroup.</span><span class="sxs-lookup"><span data-stu-id="6850e-124">To obtain groups, use the Get-LocalGroup cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6850e-125">-Name</span><span class="sxs-lookup"><span data-stu-id="6850e-125">-Name</span></span>
<span data-ttu-id="6850e-126">Spécifie un tableau de noms des groupes de sécurité que cette applet de commande supprime.</span><span class="sxs-lookup"><span data-stu-id="6850e-126">Specifies an array of names of the security groups that this cmdlet deletes.</span></span>

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

### <span data-ttu-id="6850e-127">-SID</span><span class="sxs-lookup"><span data-stu-id="6850e-127">-SID</span></span>
<span data-ttu-id="6850e-128">Spécifie un tableau d’ID de sécurité (SID) des groupes de sécurité que cette applet de commande supprime.</span><span class="sxs-lookup"><span data-stu-id="6850e-128">Specifies an array of security IDs (SIDs) of security groups that this cmdlet deletes.</span></span>

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

### <span data-ttu-id="6850e-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6850e-129">-Confirm</span></span>
<span data-ttu-id="6850e-130">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6850e-130">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="6850e-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6850e-131">-WhatIf</span></span>
<span data-ttu-id="6850e-132">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6850e-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="6850e-133">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="6850e-133">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="6850e-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6850e-134">CommonParameters</span></span>
<span data-ttu-id="6850e-135">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6850e-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6850e-136">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6850e-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6850e-137">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="6850e-137">INPUTS</span></span>

### <span data-ttu-id="6850e-138">System. Management. Automation. SecurityAccountsManager. LocalGroup, System. String, System. Security. principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="6850e-138">System.Management.Automation.SecurityAccountsManager.LocalGroup, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="6850e-139">Vous pouvez diriger un groupe de sécurité, une chaîne ou un SID vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6850e-139">You can pipe a security group, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="6850e-140">SORTIES</span><span class="sxs-lookup"><span data-stu-id="6850e-140">OUTPUTS</span></span>

### <span data-ttu-id="6850e-141">Aucun</span><span class="sxs-lookup"><span data-stu-id="6850e-141">None</span></span>
<span data-ttu-id="6850e-142">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="6850e-142">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="6850e-143">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="6850e-143">NOTES</span></span>

* <span data-ttu-id="6850e-144">Cette applet de commande ne peut pas supprimer les groupes par défaut suivants :</span><span class="sxs-lookup"><span data-stu-id="6850e-144">This cmdlet cannot delete the following default groups:</span></span>

- <span data-ttu-id="6850e-145">Administrateurs</span><span class="sxs-lookup"><span data-stu-id="6850e-145">Administrators</span></span>
- <span data-ttu-id="6850e-146">Opérateurs de sauvegarde</span><span class="sxs-lookup"><span data-stu-id="6850e-146">Backup Operators</span></span>
- <span data-ttu-id="6850e-147">Opérateurs de chiffrement</span><span class="sxs-lookup"><span data-stu-id="6850e-147">Cryptographic Operators</span></span>
- <span data-ttu-id="6850e-148">Utilisateurs du modèle COM distribué</span><span class="sxs-lookup"><span data-stu-id="6850e-148">Distributed COM Users</span></span>
- <span data-ttu-id="6850e-149">Lecteurs des journaux d’événements</span><span class="sxs-lookup"><span data-stu-id="6850e-149">Event Log Readers</span></span>
- <span data-ttu-id="6850e-150">Invités</span><span class="sxs-lookup"><span data-stu-id="6850e-150">Guests</span></span>
- <span data-ttu-id="6850e-151">Administrateurs Hyper-V</span><span class="sxs-lookup"><span data-stu-id="6850e-151">Hyper-V Administrators</span></span>
- <span data-ttu-id="6850e-152">IIS_IUSRS</span><span class="sxs-lookup"><span data-stu-id="6850e-152">IIS_IUSRS</span></span>
- <span data-ttu-id="6850e-153">Opérateurs de configuration réseau</span><span class="sxs-lookup"><span data-stu-id="6850e-153">Network Configuration Operators</span></span>
- <span data-ttu-id="6850e-154">Utilisateurs du journal des performances</span><span class="sxs-lookup"><span data-stu-id="6850e-154">Performance Log Users</span></span>
- <span data-ttu-id="6850e-155">Utilisateurs de l’Analyseur de performances</span><span class="sxs-lookup"><span data-stu-id="6850e-155">Performance Monitor Users</span></span>
- <span data-ttu-id="6850e-156">Utilisateurs avec pouvoir</span><span class="sxs-lookup"><span data-stu-id="6850e-156">Power Users</span></span>
- <span data-ttu-id="6850e-157">Utilisateurs du Bureau à distance</span><span class="sxs-lookup"><span data-stu-id="6850e-157">Remote Desktop Users</span></span>
- <span data-ttu-id="6850e-158">Utilisateurs de gestion à distance</span><span class="sxs-lookup"><span data-stu-id="6850e-158">Remote Management Users</span></span>
- <span data-ttu-id="6850e-159">Duplicateur</span><span class="sxs-lookup"><span data-stu-id="6850e-159">Replicator</span></span>
- <span data-ttu-id="6850e-160">Utilisateurs</span><span class="sxs-lookup"><span data-stu-id="6850e-160">Users</span></span>
- <span data-ttu-id="6850e-161">WinRMRemoteWMIUsers__</span><span class="sxs-lookup"><span data-stu-id="6850e-161">WinRMRemoteWMIUsers__</span></span>

* <span data-ttu-id="6850e-162">La propriété **PrincipalSource** est une propriété des objets **LocalUser** , **LocalGroup** et **LocalPrincipal** qui décrit la source de l’objet.</span><span class="sxs-lookup"><span data-stu-id="6850e-162">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="6850e-163">Les sources possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="6850e-163">The possible sources are as follows:</span></span>

- <span data-ttu-id="6850e-164">Local</span><span class="sxs-lookup"><span data-stu-id="6850e-164">Local</span></span>
- <span data-ttu-id="6850e-165">Active Directory</span><span class="sxs-lookup"><span data-stu-id="6850e-165">Active Directory</span></span>
- <span data-ttu-id="6850e-166">Groupe Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="6850e-166">Azure Active Directory group</span></span>
- <span data-ttu-id="6850e-167">Compte Microsoft</span><span class="sxs-lookup"><span data-stu-id="6850e-167">Microsoft Account</span></span>

<span data-ttu-id="6850e-168">**PrincipalSource** est pris en charge uniquement par Windows 10, windows server 2016 et les versions ultérieures du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="6850e-168">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="6850e-169">Pour les versions antérieures, la propriété est vide.</span><span class="sxs-lookup"><span data-stu-id="6850e-169">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="6850e-170">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="6850e-170">RELATED LINKS</span></span>

[<span data-ttu-id="6850e-171">Get-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="6850e-171">Get-LocalGroup</span></span>](Get-LocalGroup.md)

[<span data-ttu-id="6850e-172">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="6850e-172">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="6850e-173">Rename-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="6850e-173">Rename-LocalGroup</span></span>](Rename-LocalGroup.md)

[<span data-ttu-id="6850e-174">Set-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="6850e-174">Set-LocalGroup</span></span>](Set-LocalGroup.md)
