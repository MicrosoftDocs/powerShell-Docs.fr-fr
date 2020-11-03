---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/get-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LocalGroup
ms.openlocfilehash: 2cd77c2766840527825b0ccf68abaac3c2ea6c16
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202238"
---
# <span data-ttu-id="841ed-103">Get-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="841ed-103">Get-LocalGroup</span></span>

## <span data-ttu-id="841ed-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="841ed-104">SYNOPSIS</span></span>
<span data-ttu-id="841ed-105">Obtient les groupes de sécurité locaux.</span><span class="sxs-lookup"><span data-stu-id="841ed-105">Gets the local security groups.</span></span>

## <span data-ttu-id="841ed-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="841ed-106">SYNTAX</span></span>

### <span data-ttu-id="841ed-107">Valeur par défaut (par défaut)</span><span class="sxs-lookup"><span data-stu-id="841ed-107">Default (Default)</span></span>

```
Get-LocalGroup [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="841ed-108">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="841ed-108">SecurityIdentifier</span></span>

```
Get-LocalGroup [[-SID] <SecurityIdentifier[]>] [<CommonParameters>]
```

## <span data-ttu-id="841ed-109">Description</span><span class="sxs-lookup"><span data-stu-id="841ed-109">DESCRIPTION</span></span>
<span data-ttu-id="841ed-110">L’applet de commande **obtenir-LocalGroup** obtient les groupes de sécurité locaux dans le gestionnaire de comptes de sécurité.</span><span class="sxs-lookup"><span data-stu-id="841ed-110">The **Get-LocalGroup** cmdlet gets local security groups in Security Account Manager.</span></span>
<span data-ttu-id="841ed-111">Cette applet de commande obtient les groupes intégrés et les groupes de sécurité locaux par défaut que vous créez.</span><span class="sxs-lookup"><span data-stu-id="841ed-111">This cmdlet gets default built-in groups and local security groups that you create.</span></span>

> [!NOTE]
> <span data-ttu-id="841ed-112">Le module Microsoft. PowerShell. LocalAccounts n’est pas disponible dans PowerShell 32 bits sur un système 64 bits.</span><span class="sxs-lookup"><span data-stu-id="841ed-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="841ed-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="841ed-113">EXAMPLES</span></span>

### <span data-ttu-id="841ed-114">Exemple 1 : récupérer le groupe administrateurs</span><span class="sxs-lookup"><span data-stu-id="841ed-114">Example 1: Get the Administrators group</span></span>

```
PS C:\> Get-LocalGroup -Name "Administrators"
Name           Description
----           -----------
Administrators Administrators have complete and unrestricted access to the computer/domain
```

<span data-ttu-id="841ed-115">Cette commande obtient le groupe Administrateurs local.</span><span class="sxs-lookup"><span data-stu-id="841ed-115">This command gets the local Administrators group.</span></span>
<span data-ttu-id="841ed-116">La commande affiche les propriétés du groupe dans la console.</span><span class="sxs-lookup"><span data-stu-id="841ed-116">The command displays properties of the group in the console.</span></span>

## <span data-ttu-id="841ed-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="841ed-117">PARAMETERS</span></span>

### <span data-ttu-id="841ed-118">-Name</span><span class="sxs-lookup"><span data-stu-id="841ed-118">-Name</span></span>
<span data-ttu-id="841ed-119">Spécifie un tableau de noms de groupes de sécurité que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="841ed-119">Specifies an array of names of security groups that this cmdlet gets.</span></span>
<span data-ttu-id="841ed-120">Vous pouvez utiliser le caractère générique.</span><span class="sxs-lookup"><span data-stu-id="841ed-120">You can use the wildcard character.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="841ed-121">-SID</span><span class="sxs-lookup"><span data-stu-id="841ed-121">-SID</span></span>
<span data-ttu-id="841ed-122">Spécifie un tableau d’ID de sécurité (SID) des groupes de sécurité que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="841ed-122">Specifies an array of security IDs (SIDs) of security groups that this cmdlet gets.</span></span>

```yaml
Type: System.Security.Principal.SecurityIdentifier[]
Parameter Sets: SecurityIdentifier
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="841ed-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="841ed-123">CommonParameters</span></span>
<span data-ttu-id="841ed-124">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="841ed-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="841ed-125">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="841ed-125">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="841ed-126">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="841ed-126">INPUTS</span></span>

### <span data-ttu-id="841ed-127">System. String, System. Security. principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="841ed-127">System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="841ed-128">Vous pouvez diriger une chaîne ou un SID vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="841ed-128">You can pipe a string or a SID to this cmdlet.</span></span>

## <span data-ttu-id="841ed-129">SORTIES</span><span class="sxs-lookup"><span data-stu-id="841ed-129">OUTPUTS</span></span>

### <span data-ttu-id="841ed-130">System. Management. Automation. SecurityAccountsManager. LocalGroup</span><span class="sxs-lookup"><span data-stu-id="841ed-130">System.Management.Automation.SecurityAccountsManager.LocalGroup</span></span>
<span data-ttu-id="841ed-131">Cette applet de commande retourne un groupe local.</span><span class="sxs-lookup"><span data-stu-id="841ed-131">This cmdlet returns a local group.</span></span>

## <span data-ttu-id="841ed-132">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="841ed-132">NOTES</span></span>

* <span data-ttu-id="841ed-133">La propriété **PrincipalSource** est une propriété des objets **LocalUser** , **LocalGroup** et **LocalPrincipal** qui décrit la source de l’objet.</span><span class="sxs-lookup"><span data-stu-id="841ed-133">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="841ed-134">Les sources possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="841ed-134">The possible sources are as follows:</span></span>

- <span data-ttu-id="841ed-135">Local</span><span class="sxs-lookup"><span data-stu-id="841ed-135">Local</span></span>
- <span data-ttu-id="841ed-136">Active Directory</span><span class="sxs-lookup"><span data-stu-id="841ed-136">Active Directory</span></span>
- <span data-ttu-id="841ed-137">Groupe Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="841ed-137">Azure Active Directory group</span></span>
- <span data-ttu-id="841ed-138">Compte Microsoft</span><span class="sxs-lookup"><span data-stu-id="841ed-138">Microsoft Account</span></span>

<span data-ttu-id="841ed-139">**PrincipalSource** est pris en charge uniquement par Windows 10, windows server 2016 et les versions ultérieures du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="841ed-139">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="841ed-140">Pour les versions antérieures, la propriété est vide.</span><span class="sxs-lookup"><span data-stu-id="841ed-140">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="841ed-141">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="841ed-141">RELATED LINKS</span></span>

[<span data-ttu-id="841ed-142">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="841ed-142">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="841ed-143">Remove-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="841ed-143">Remove-LocalGroup</span></span>](Remove-LocalGroup.md)

[<span data-ttu-id="841ed-144">Rename-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="841ed-144">Rename-LocalGroup</span></span>](Rename-LocalGroup.md)

[<span data-ttu-id="841ed-145">Set-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="841ed-145">Set-LocalGroup</span></span>](Set-LocalGroup.md)
