---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psprovider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSProvider
ms.openlocfilehash: 20820d2d194f41d43048c9617b63b9acb3fbb4f8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596115"
---
# <span data-ttu-id="db33d-102">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="db33d-102">Get-PSProvider</span></span>

## <span data-ttu-id="db33d-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="db33d-103">SYNOPSIS</span></span>
<span data-ttu-id="db33d-104">Obtient des informations sur le fournisseur PowerShell spécifié.</span><span class="sxs-lookup"><span data-stu-id="db33d-104">Gets information about the specified PowerShell provider.</span></span>

## <span data-ttu-id="db33d-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="db33d-105">SYNTAX</span></span>

```
Get-PSProvider [[-PSProvider] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="db33d-106">Description</span><span class="sxs-lookup"><span data-stu-id="db33d-106">DESCRIPTION</span></span>

<span data-ttu-id="db33d-107">L' `Get-PSProvider` applet de commande obtient les fournisseurs PowerShell dans la session active.</span><span class="sxs-lookup"><span data-stu-id="db33d-107">The `Get-PSProvider` cmdlet gets the PowerShell providers in the current session.</span></span>
<span data-ttu-id="db33d-108">Vous pouvez obtenir un lecteur particulier ou tous les lecteurs présents dans la session.</span><span class="sxs-lookup"><span data-stu-id="db33d-108">You can get a particular drive or all drives in the session.</span></span>

<span data-ttu-id="db33d-109">Les fournisseurs PowerShell vous permettent d’accéder à divers magasins de données comme s’ils étaient des lecteurs de système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="db33d-109">PowerShell providers let you access a variety of data stores as though they were file system drives.</span></span>
<span data-ttu-id="db33d-110">Pour plus d’informations sur les fournisseurs PowerShell, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="db33d-110">For information about PowerShell providers, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="db33d-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="db33d-111">EXAMPLES</span></span>

### <span data-ttu-id="db33d-112">Exemple 1 : afficher la liste de tous les fournisseurs disponibles</span><span class="sxs-lookup"><span data-stu-id="db33d-112">Example 1: Display a list of all available providers</span></span>

```powershell
Get-PSProvider
```

<span data-ttu-id="db33d-113">Cette commande affiche la liste de tous les fournisseurs PowerShell disponibles.</span><span class="sxs-lookup"><span data-stu-id="db33d-113">This command displays a list of all available PowerShell providers.</span></span>

### <span data-ttu-id="db33d-114">Exemple 2 : afficher la liste de tous les fournisseurs PowerShell qui commencent par des lettres spécifiées</span><span class="sxs-lookup"><span data-stu-id="db33d-114">Example 2: Display a list of all PowerShell providers that begin with specified letters</span></span>

```powershell
Get-PSProvider f*, r* | Format-List
```

<span data-ttu-id="db33d-115">Cette commande affiche la liste de tous les fournisseurs PowerShell dont le nom commence par la lettre f ou r.</span><span class="sxs-lookup"><span data-stu-id="db33d-115">This command displays a list of all PowerShell providers with names that begin with the letter f or r.</span></span>

### <span data-ttu-id="db33d-116">Exemple 3 : Rechercher les composants logiciels enfichables ou les modules qui ont ajouté des fournisseurs à votre session</span><span class="sxs-lookup"><span data-stu-id="db33d-116">Example 3: Find snap-ins or module that added providers to your session</span></span>

```powershell
Get-PSProvider | Format-Table name, module, pssnapin -auto
```

```Output
Name        Module       PSSnapIn
----        ------       --------
Test        TestModule
WSMan                    Microsoft.WSMan.Management
Alias                    Microsoft.PowerShell.Core
Environment              Microsoft.PowerShell.Core
FileSystem               Microsoft.PowerShell.Core
Function                 Microsoft.PowerShell.Core
Registry                 Microsoft.PowerShell.Core
Variable                 Microsoft.PowerShell.Core
Certificate              Microsoft.PowerShell.Security
```

```powershell
Get-PSProvider | Where {$_.pssnapin -eq "Microsoft.PowerShell.Security"}
```

```Output
Name            Capabilities      Drives
----            ------------      ------
Certificate     ShouldProcess     {cert}
```

<span data-ttu-id="db33d-117">Ces commandes recherchent les modules ou composants logiciels enfichables PowerShell qui ont ajouté des fournisseurs à votre session.</span><span class="sxs-lookup"><span data-stu-id="db33d-117">These commands find the PowerShell snap-ins or modules that added providers to your session.</span></span>
<span data-ttu-id="db33d-118">Tous les éléments PowerShell, y compris les fournisseurs, proviennent d’un composant logiciel enfichable ou d’un module.</span><span class="sxs-lookup"><span data-stu-id="db33d-118">All PowerShell elements, including providers, originate in a snap-in or in a module.</span></span>

<span data-ttu-id="db33d-119">Ces commandes utilisent les propriétés PSSnapin et module de l’objet **providerinfo retourné par** qui `Get-PSProvider` retourne.</span><span class="sxs-lookup"><span data-stu-id="db33d-119">These commands use the PSSnapin and Module properties of the **ProviderInfo** object that `Get-PSProvider` returns.</span></span>
<span data-ttu-id="db33d-120">Les valeurs de ces propriétés contiennent le nom du module ou du composant logiciel enfichable qui ajoute le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="db33d-120">The values of these properties contain the name of the snap-in or module that adds the provider.</span></span>

<span data-ttu-id="db33d-121">La première commande obtient tous les fournisseurs présents dans la session et les présente sous forme de tableau indiquant les valeurs de leurs propriétés Name, Module et PSSnapin.</span><span class="sxs-lookup"><span data-stu-id="db33d-121">The first command gets all of the providers in the session and formats them in a table with the values of their Name, Module, and PSSnapin properties.</span></span>

<span data-ttu-id="db33d-122">La deuxième commande utilise l' `Where-Object` applet de commande pour récupérer les fournisseurs qui proviennent du composant logiciel enfichable **Microsoft. PowerShell. Security** .</span><span class="sxs-lookup"><span data-stu-id="db33d-122">The second command uses the `Where-Object` cmdlet to get the providers that come from the **Microsoft.PowerShell.Security** snap-in.</span></span>

### <span data-ttu-id="db33d-123">Exemple 4 : résolution du chemin d’accès de la propriété de démarrage du fournisseur de système de fichiers</span><span class="sxs-lookup"><span data-stu-id="db33d-123">Example 4: Resolve the path of the Home property of the file system provider</span></span>

```powershell
C:\> Resolve-Path ~
```

```Output
Path
----
C:\Users\User01
```

```powershell
PS C:\> (get-psprovider FileSystem).home
```

```Output
C:\Users\User01
```

<span data-ttu-id="db33d-124">Cet exemple montre que le symbole tilde (~) représente la valeur de la propriété de **démarrage** du fournisseur FileSystem.</span><span class="sxs-lookup"><span data-stu-id="db33d-124">This example shows that the tilde symbol (~) represents the value of the **Home** property of the FileSystem provider.</span></span>
<span data-ttu-id="db33d-125">La valeur de la propriété de **démarrage** est facultative, mais pour le fournisseur **FileSystem** , elle est définie en tant que `$env:homedrive\$env:homepath` ou `$home` .</span><span class="sxs-lookup"><span data-stu-id="db33d-125">The **Home** property value is optional, but for the **FileSystem** provider, it is defined as `$env:homedrive\$env:homepath` or `$home`.</span></span>

## <span data-ttu-id="db33d-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="db33d-126">PARAMETERS</span></span>

### <span data-ttu-id="db33d-127">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="db33d-127">-PSProvider</span></span>

<span data-ttu-id="db33d-128">Spécifie le nom ou les noms des fournisseurs PowerShell sur lesquels cette applet de commande obtient des informations.</span><span class="sxs-lookup"><span data-stu-id="db33d-128">Specifies the name or names of the PowerShell providers about which this cmdlet gets information.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="db33d-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="db33d-129">CommonParameters</span></span>

<span data-ttu-id="db33d-130">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="db33d-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="db33d-131">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="db33d-131">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="db33d-132">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="db33d-132">INPUTS</span></span>

### <span data-ttu-id="db33d-133">String[]</span><span class="sxs-lookup"><span data-stu-id="db33d-133">String[]</span></span>

<span data-ttu-id="db33d-134">Vous pouvez diriger une ou plusieurs chaînes de nom de fournisseur vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="db33d-134">You can pipe one or more provider name strings to this cmdlet.</span></span>

## <span data-ttu-id="db33d-135">SORTIES</span><span class="sxs-lookup"><span data-stu-id="db33d-135">OUTPUTS</span></span>

### <span data-ttu-id="db33d-136">System. Management. Automation. Providerinfo retourné par</span><span class="sxs-lookup"><span data-stu-id="db33d-136">System.Management.Automation.ProviderInfo</span></span>

<span data-ttu-id="db33d-137">Cette applet de commande retourne des objets qui représentent les fournisseurs PowerShell dans la session.</span><span class="sxs-lookup"><span data-stu-id="db33d-137">This cmdlet returns objects that represent the PowerShell providers in the session.</span></span>

## <span data-ttu-id="db33d-138">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="db33d-138">NOTES</span></span>

## <span data-ttu-id="db33d-139">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="db33d-139">RELATED LINKS</span></span>

