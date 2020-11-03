---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psprovider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSProvider
ms.openlocfilehash: 997d86460837946a2cf18fc78f058f21472dd909
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203986"
---
# <span data-ttu-id="8b0a8-103">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="8b0a8-103">Get-PSProvider</span></span>

## <span data-ttu-id="8b0a8-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8b0a8-104">SYNOPSIS</span></span>
<span data-ttu-id="8b0a8-105">Obtient des informations se rapportant au fournisseur Windows PowerShell spécifié.</span><span class="sxs-lookup"><span data-stu-id="8b0a8-105">Gets information about the specified Windows PowerShell provider.</span></span>

## <span data-ttu-id="8b0a8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8b0a8-106">SYNTAX</span></span>

```
Get-PSProvider [[-PSProvider] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="8b0a8-107">Description</span><span class="sxs-lookup"><span data-stu-id="8b0a8-107">DESCRIPTION</span></span>
<span data-ttu-id="8b0a8-108">L’applet de commande **obtenir-PSProvider** obtient les fournisseurs Windows PowerShell dans la session active.</span><span class="sxs-lookup"><span data-stu-id="8b0a8-108">The **Get-PSProvider** cmdlet gets the Windows PowerShell providers in the current session.</span></span>
<span data-ttu-id="8b0a8-109">Vous pouvez obtenir un lecteur particulier ou tous les lecteurs présents dans la session.</span><span class="sxs-lookup"><span data-stu-id="8b0a8-109">You can get a particular drive or all drives in the session.</span></span>

<span data-ttu-id="8b0a8-110">Les fournisseurs Windows PowerShell vous permettent d’accéder à divers magasins de données, comme s’ils étaient des lecteurs de système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="8b0a8-110">Windows PowerShell providers let you access a variety of data stores as though they were file system drives.</span></span>
<span data-ttu-id="8b0a8-111">Pour plus d’informations sur les fournisseurs Windows PowerShell, consultez about_Providers.</span><span class="sxs-lookup"><span data-stu-id="8b0a8-111">For information about Windows PowerShell providers, see about_Providers.</span></span>

## <span data-ttu-id="8b0a8-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8b0a8-112">EXAMPLES</span></span>

### <span data-ttu-id="8b0a8-113">Exemple 1 : afficher la liste de tous les fournisseurs disponibles</span><span class="sxs-lookup"><span data-stu-id="8b0a8-113">Example 1: Display a list of all available providers</span></span>

```
PS C:\> Get-PSProvider
```

<span data-ttu-id="8b0a8-114">Cette commande affiche la liste de tous les fournisseurs Windows PowerShell disponibles.</span><span class="sxs-lookup"><span data-stu-id="8b0a8-114">This command displays a list of all available Windows PowerShell providers.</span></span>

### <span data-ttu-id="8b0a8-115">Exemple 2 : afficher une liste de tous les fournisseurs Windows PowerShell qui commencent par des lettres spécifiées</span><span class="sxs-lookup"><span data-stu-id="8b0a8-115">Example 2: Display a list of all Windows PowerShell providers that begin with specified letters</span></span>

```
PS C:\> Get-PSProvider f*, r* | Format-List
```

<span data-ttu-id="8b0a8-116">Cette commande affiche une liste de tous les fournisseurs Windows PowerShell dont le nom commence par la lettre f ou r.</span><span class="sxs-lookup"><span data-stu-id="8b0a8-116">This command displays a list of all Windows PowerShell providers with names that begin with the letter f or r.</span></span>

### <span data-ttu-id="8b0a8-117">Exemple 3 : Rechercher les composants logiciels enfichables ou les modules qui ont ajouté des fournisseurs à votre session</span><span class="sxs-lookup"><span data-stu-id="8b0a8-117">Example 3: Find snap-ins or module that added providers to your session</span></span>

```
PS C:\> Get-PSProvider | Format-Table name, module, pssnapin -auto

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

PS C:\> Get-PSProvider | Where {$_.pssnapin -eq "Microsoft.PowerShell.Security"}

Name            Capabilities      Drives
----            ------------      ------
Certificate     ShouldProcess     {cert}
```

<span data-ttu-id="8b0a8-118">Ces commandes recherchent les modules ou les composants logiciels enfichables Windows PowerShell qui ont ajouté des fournisseurs à votre session.</span><span class="sxs-lookup"><span data-stu-id="8b0a8-118">These commands find the Windows PowerShell snap-ins or modules that added providers to your session.</span></span>
<span data-ttu-id="8b0a8-119">Tous les éléments Windows PowerShell, y compris les fournisseurs, proviennent d’un module ou d’un composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="8b0a8-119">All Windows PowerShell elements, including providers, originate in a snap-in or in a module.</span></span>

<span data-ttu-id="8b0a8-120">Ces commandes utilisent les propriétés PSSnapin et module de l’objet **providerinfo retourné par** retourné par la méthode **-PSProvider** .</span><span class="sxs-lookup"><span data-stu-id="8b0a8-120">These commands use the PSSnapin and Module properties of the **ProviderInfo** object that **Get-PSProvider** returns.</span></span>
<span data-ttu-id="8b0a8-121">Les valeurs de ces propriétés contiennent le nom du module ou du composant logiciel enfichable qui ajoute le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="8b0a8-121">The values of these properties contain the name of the snap-in or module that adds the provider.</span></span>

<span data-ttu-id="8b0a8-122">La première commande obtient tous les fournisseurs présents dans la session et les présente sous forme de tableau indiquant les valeurs de leurs propriétés Name, Module et PSSnapin.</span><span class="sxs-lookup"><span data-stu-id="8b0a8-122">The first command gets all of the providers in the session and formats them in a table with the values of their Name, Module, and PSSnapin properties.</span></span>

<span data-ttu-id="8b0a8-123">La deuxième commande utilise l’applet de commande Where-Object pour récupérer les fournisseurs qui proviennent du composant logiciel enfichable **Microsoft. PowerShell. Security** .</span><span class="sxs-lookup"><span data-stu-id="8b0a8-123">The second command uses the Where-Object cmdlet to get the providers that come from the **Microsoft.PowerShell.Security** snap-in.</span></span>

### <span data-ttu-id="8b0a8-124">Exemple 4 : résolution du chemin d’accès de la propriété de démarrage du fournisseur de système de fichiers</span><span class="sxs-lookup"><span data-stu-id="8b0a8-124">Example 4: Resolve the path of the Home property of the file system provider</span></span>

```
PS C:\> Resolve-Path ~

Path
----
C:\Users\User01

PS C:\> (get-psprovider FileSystem).home
C:\Users\User01
```

<span data-ttu-id="8b0a8-125">Cet exemple montre que le symbole tilde (~) représente la valeur de la propriété Home du fournisseur de système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="8b0a8-125">This example shows that the tilde symbol (~) represents the value of the Home property of the FileSystem provider.</span></span>
<span data-ttu-id="8b0a8-126">La valeur de la propriété de démarrage est facultative, mais pour le fournisseur FileSystem, elle est définie comme $env : HomeDrive \$ env : homepath ou $Home.</span><span class="sxs-lookup"><span data-stu-id="8b0a8-126">The Home property value is optional, but for the FileSystem provider, it is defined as $env:homedrive\$env:homepath or $home.</span></span>

## <span data-ttu-id="8b0a8-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8b0a8-127">PARAMETERS</span></span>

### <span data-ttu-id="8b0a8-128">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="8b0a8-128">-PSProvider</span></span>
<span data-ttu-id="8b0a8-129">Spécifie le nom ou les noms des fournisseurs Windows PowerShell à propos desquels cette applet de commande obtient des informations.</span><span class="sxs-lookup"><span data-stu-id="8b0a8-129">Specifies the name or names of the Windows PowerShell providers about which this cmdlet gets information.</span></span>

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

### <span data-ttu-id="8b0a8-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8b0a8-130">CommonParameters</span></span>
<span data-ttu-id="8b0a8-131">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8b0a8-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8b0a8-132">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8b0a8-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8b0a8-133">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8b0a8-133">INPUTS</span></span>

### <span data-ttu-id="8b0a8-134">String[]</span><span class="sxs-lookup"><span data-stu-id="8b0a8-134">String[]</span></span>

<span data-ttu-id="8b0a8-135">Vous pouvez diriger une ou plusieurs chaînes de nom de fournisseur vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8b0a8-135">You can pipe one or more provider name strings to this cmdlet.</span></span>

## <span data-ttu-id="8b0a8-136">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8b0a8-136">OUTPUTS</span></span>

### <span data-ttu-id="8b0a8-137">System. Management. Automation. Providerinfo retourné par</span><span class="sxs-lookup"><span data-stu-id="8b0a8-137">System.Management.Automation.ProviderInfo</span></span>
<span data-ttu-id="8b0a8-138">Cette applet de commande retourne des objets qui représentent les fournisseurs Windows PowerShell dans la session.</span><span class="sxs-lookup"><span data-stu-id="8b0a8-138">This cmdlet returns objects that represent the Windows PowerShell providers in the session.</span></span>

## <span data-ttu-id="8b0a8-139">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8b0a8-139">NOTES</span></span>

## <span data-ttu-id="8b0a8-140">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8b0a8-140">RELATED LINKS</span></span>

## <span data-ttu-id="8b0a8-141">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8b0a8-141">RELATED LINKS</span></span>
