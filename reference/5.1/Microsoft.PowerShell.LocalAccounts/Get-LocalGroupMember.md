---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/get-localgroupmember?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LocalGroupMember
ms.openlocfilehash: 200368c5d13bd027302ad824533e6c187906ed0f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202233"
---
# <span data-ttu-id="f1962-103">Get-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="f1962-103">Get-LocalGroupMember</span></span>

## <span data-ttu-id="f1962-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="f1962-104">SYNOPSIS</span></span>
<span data-ttu-id="f1962-105">Obtient les membres d’un groupe local.</span><span class="sxs-lookup"><span data-stu-id="f1962-105">Gets members from a local group.</span></span>

## <span data-ttu-id="f1962-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f1962-106">SYNTAX</span></span>

### <span data-ttu-id="f1962-107">Valeur par défaut (par défaut)</span><span class="sxs-lookup"><span data-stu-id="f1962-107">Default (Default)</span></span>

```
Get-LocalGroupMember [[-Member] <String>] [-Name] <String> [<CommonParameters>]
```

### <span data-ttu-id="f1962-108">Groupe</span><span class="sxs-lookup"><span data-stu-id="f1962-108">Group</span></span>

```
Get-LocalGroupMember [-Group] <LocalGroup> [[-Member] <String>] [<CommonParameters>]
```

### <span data-ttu-id="f1962-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="f1962-109">SecurityIdentifier</span></span>

```
Get-LocalGroupMember [[-Member] <String>] [-SID] <SecurityIdentifier> [<CommonParameters>]
```

## <span data-ttu-id="f1962-110">Description</span><span class="sxs-lookup"><span data-stu-id="f1962-110">DESCRIPTION</span></span>
<span data-ttu-id="f1962-111">L’applet de commande **obtenir-LocalGroupMember** obtient les membres d’un groupe local.</span><span class="sxs-lookup"><span data-stu-id="f1962-111">The **Get-LocalGroupMember** cmdlet gets members from a local group.</span></span>

> [!NOTE]
> <span data-ttu-id="f1962-112">Le module Microsoft. PowerShell. LocalAccounts n’est pas disponible dans PowerShell 32 bits sur un système 64 bits.</span><span class="sxs-lookup"><span data-stu-id="f1962-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="f1962-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="f1962-113">EXAMPLES</span></span>

### <span data-ttu-id="f1962-114">Exemple 1 : récupération de tous les membres du groupe administrateurs</span><span class="sxs-lookup"><span data-stu-id="f1962-114">Example 1: Get all members of the Administrators group</span></span>

```
PS C:\> Get-LocalGroupMember -Group "Administrators"
ObjectClass Name                    PrincipalSource
----------- ----                    ---------------
User        CONTOSOPC\Administrator Local
User        CONTOSOPC\LocalAdmin    Local
```

<span data-ttu-id="f1962-115">Cette commande obtient tous les membres du groupe Administrateurs local.</span><span class="sxs-lookup"><span data-stu-id="f1962-115">This command gets all the members of the local Administrators group.</span></span>

## <span data-ttu-id="f1962-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f1962-116">PARAMETERS</span></span>

### <span data-ttu-id="f1962-117">-Group</span><span class="sxs-lookup"><span data-stu-id="f1962-117">-Group</span></span>
<span data-ttu-id="f1962-118">Spécifie le groupe de sécurité à partir duquel cette applet de commande obtient des membres.</span><span class="sxs-lookup"><span data-stu-id="f1962-118">Specifies the security group from which this cmdlet gets members.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup
Parameter Sets: Group
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f1962-119">-Membre</span><span class="sxs-lookup"><span data-stu-id="f1962-119">-Member</span></span>
<span data-ttu-id="f1962-120">Spécifie un utilisateur ou un groupe que cette applet de commande obtient d’un groupe de sécurité.</span><span class="sxs-lookup"><span data-stu-id="f1962-120">Specifies a user or group that this cmdlet gets from a security group.</span></span>
<span data-ttu-id="f1962-121">Vous pouvez spécifier des utilisateurs ou des groupes par nom ou ID de sécurité (SID).</span><span class="sxs-lookup"><span data-stu-id="f1962-121">You can specify users or groups by name or security ID (SID).</span></span>
<span data-ttu-id="f1962-122">Spécifiez les chaînes SID dans S-R-I-S-S.</span><span class="sxs-lookup"><span data-stu-id="f1962-122">Specify SID strings in S-R-I-S-S .</span></span>
<span data-ttu-id="f1962-123">.</span><span class="sxs-lookup"><span data-stu-id="f1962-123">.</span></span> <span data-ttu-id="f1962-124">.</span><span class="sxs-lookup"><span data-stu-id="f1962-124">.</span></span>
<span data-ttu-id="f1962-125">HH:MM:SS.</span><span class="sxs-lookup"><span data-stu-id="f1962-125">format.</span></span>
<span data-ttu-id="f1962-126">Vous pouvez utiliser des caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="f1962-126">You can use wildcard characters.</span></span>
<span data-ttu-id="f1962-127">Si vous ne spécifiez pas ce paramètre, l’applet de commande obtient tous les membres du groupe.</span><span class="sxs-lookup"><span data-stu-id="f1962-127">If you do not specify this parameter, the cmdlet gets all members of the group.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f1962-128">-Name</span><span class="sxs-lookup"><span data-stu-id="f1962-128">-Name</span></span>
<span data-ttu-id="f1962-129">Spécifie le nom du groupe de sécurité à partir duquel cette applet de commande obtient des membres.</span><span class="sxs-lookup"><span data-stu-id="f1962-129">Specifies the name of the security group from which this cmdlet gets members.</span></span>

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

### <span data-ttu-id="f1962-130">-SID</span><span class="sxs-lookup"><span data-stu-id="f1962-130">-SID</span></span>
<span data-ttu-id="f1962-131">Spécifie l’ID de sécurité du groupe de sécurité à partir duquel cette applet de commande obtient des membres.</span><span class="sxs-lookup"><span data-stu-id="f1962-131">Specifies the security ID of the security group from which this cmdlet gets members.</span></span>

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

### <span data-ttu-id="f1962-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f1962-132">CommonParameters</span></span>
<span data-ttu-id="f1962-133">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f1962-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f1962-134">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f1962-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f1962-135">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="f1962-135">INPUTS</span></span>

### <span data-ttu-id="f1962-136">System. Management. Automation. SecurityAccountsManager. LocalGroup, System. String, System. Security. principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="f1962-136">System.Management.Automation.SecurityAccountsManager.LocalGroup, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="f1962-137">Vous pouvez diriger un groupe local, une chaîne ou un SID vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f1962-137">You can pipe a local group, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="f1962-138">SORTIES</span><span class="sxs-lookup"><span data-stu-id="f1962-138">OUTPUTS</span></span>

### <span data-ttu-id="f1962-139">Microsoft. SecurityAccountsManager. LocalPrincipal</span><span class="sxs-lookup"><span data-stu-id="f1962-139">Microsoft.SecurityAccountsManager.LocalPrincipal</span></span>
<span data-ttu-id="f1962-140">Cette applet de commande retourne les principaux locaux.</span><span class="sxs-lookup"><span data-stu-id="f1962-140">This cmdlet returns local principals.</span></span>

## <span data-ttu-id="f1962-141">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="f1962-141">NOTES</span></span>

* <span data-ttu-id="f1962-142">La propriété **PrincipalSource** est une propriété des objets **LocalUser** , **LocalGroup** et **LocalPrincipal** qui décrit la source de l’objet.</span><span class="sxs-lookup"><span data-stu-id="f1962-142">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="f1962-143">Les sources possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f1962-143">The possible sources are as follows:</span></span>

- <span data-ttu-id="f1962-144">Local</span><span class="sxs-lookup"><span data-stu-id="f1962-144">Local</span></span>
- <span data-ttu-id="f1962-145">Active Directory</span><span class="sxs-lookup"><span data-stu-id="f1962-145">Active Directory</span></span>
- <span data-ttu-id="f1962-146">Groupe Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="f1962-146">Azure Active Directory group</span></span>
- <span data-ttu-id="f1962-147">Compte Microsoft</span><span class="sxs-lookup"><span data-stu-id="f1962-147">Microsoft Account</span></span>

<span data-ttu-id="f1962-148">**PrincipalSource** est pris en charge uniquement par Windows 10, windows server 2016 et les versions ultérieures du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="f1962-148">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="f1962-149">Pour les versions antérieures, la propriété est vide.</span><span class="sxs-lookup"><span data-stu-id="f1962-149">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="f1962-150">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="f1962-150">RELATED LINKS</span></span>

[<span data-ttu-id="f1962-151">Add-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="f1962-151">Add-LocalGroupMember</span></span>](Add-LocalGroupMember.md)

[<span data-ttu-id="f1962-152">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="f1962-152">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="f1962-153">Remove-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="f1962-153">Remove-LocalGroupMember</span></span>](Remove-LocalGroupMember.md)
