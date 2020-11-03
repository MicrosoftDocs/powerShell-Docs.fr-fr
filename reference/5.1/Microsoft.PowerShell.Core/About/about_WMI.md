---
description: Windows Management Instrumentation (WMI) utilise le Common Information Model (CIM) pour représenter les systèmes, applications, réseaux, périphériques et autres composants gérables de l’entreprise moderne.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wmi?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WMI
ms.openlocfilehash: d24b952ee167e51815d6d9920e95bbc9a6bb9608
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207890"
---
# <a name="about-wmi"></a><span data-ttu-id="8e380-104">À propos de WMI</span><span class="sxs-lookup"><span data-stu-id="8e380-104">About WMI</span></span>

## <a name="short-description"></a><span data-ttu-id="8e380-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="8e380-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="8e380-106">Windows Management Instrumentation (WMI) utilise le Common Information Model (CIM) pour représenter les systèmes, applications, réseaux, périphériques et autres composants gérables de l’entreprise moderne.</span><span class="sxs-lookup"><span data-stu-id="8e380-106">Windows Management Instrumentation (WMI) uses the Common Information Model (CIM) to represent systems, applications, networks, devices, and other manageable components of the modern enterprise.</span></span>

## <a name="long-description"></a><span data-ttu-id="8e380-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="8e380-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="8e380-108">Windows Management Instrumentation (WMI) est l’implémentation par Microsoft de Web-Based Enterprise Management (WBEM), la norme du secteur.</span><span class="sxs-lookup"><span data-stu-id="8e380-108">Windows Management Instrumentation (WMI) is Microsoft's implementation of Web-Based Enterprise Management (WBEM), the industry standard.</span></span>

<span data-ttu-id="8e380-109">WMI classique utilise DCOM pour communiquer avec les appareils en réseau afin de gérer les systèmes distants.</span><span class="sxs-lookup"><span data-stu-id="8e380-109">Classic WMI uses DCOM to communicate with networked devices to manage remote systems.</span></span> <span data-ttu-id="8e380-110">Windows PowerShell 3,0 introduit un modèle de fournisseur CIM qui utilise WinRM pour supprimer la dépendance sur DCOM.</span><span class="sxs-lookup"><span data-stu-id="8e380-110">Windows PowerShell 3.0 introduces a CIM provider model that uses WinRM to remove the dependency on DCOM.</span></span> <span data-ttu-id="8e380-111">Ce modèle de fournisseur CIM utilise également de nouvelles API de fournisseur WMI qui permettent aux développeurs d’écrire des applets de commande Windows PowerShell en code natif (C \+ \+ ).</span><span class="sxs-lookup"><span data-stu-id="8e380-111">This CIM provider model also uses new WMI provider APIs that enable developers to write Windows PowerShell cmdlets in native code (C\+\+).</span></span>

<span data-ttu-id="8e380-112">Ne confondez pas les fournisseurs WMI avec les fournisseurs Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8e380-112">Do not confuse WMI providers with Windows PowerShell providers.</span></span> <span data-ttu-id="8e380-113">De nombreuses fonctionnalités Windows ont un fournisseur WMI associé qui expose leurs fonctionnalités de gestion.</span><span class="sxs-lookup"><span data-stu-id="8e380-113">Many Windows features have an associated WMI provider that exposes their management capabilities.</span></span> <span data-ttu-id="8e380-114">Pour obtenir des fournisseurs WMI, exécutez une requête WMI qui obtient des instances de la classe WMI __Provider, par exemple la requête suivante.</span><span class="sxs-lookup"><span data-stu-id="8e380-114">To get WMI providers, run a WMI query that gets instances of the __Provider WMI class, such as the following query.</span></span>

```powershell
Get-WmiObject -Class __Provider
```

## <a name="three-components-of-wmi"></a><span data-ttu-id="8e380-115">TROIS COMPOSANTS DE WMI</span><span class="sxs-lookup"><span data-stu-id="8e380-115">THREE COMPONENTS OF WMI</span></span>

<span data-ttu-id="8e380-116">Les trois composants suivants de WMI interagissent avec Windows PowerShell : espaces de noms, fournisseurs et classes.</span><span class="sxs-lookup"><span data-stu-id="8e380-116">The following three components of WMI interact with Windows PowerShell: Namespaces, Providers, and Classes.</span></span>

<span data-ttu-id="8e380-117">Les espaces de noms WMI organisent les fournisseurs WMI et les classes WMI en groupes de composants associés.</span><span class="sxs-lookup"><span data-stu-id="8e380-117">WMI Namespaces organize WMI providers and WMI classes into groups of related components.</span></span> <span data-ttu-id="8e380-118">De cette façon, elles sont similaires aux espaces de noms .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8e380-118">In this way, they are similar to .NET Framework namespaces.</span></span>
<span data-ttu-id="8e380-119">Les espaces de noms ne sont pas des emplacements physiques, mais ils sont plus similaires aux bases de données logiques.</span><span class="sxs-lookup"><span data-stu-id="8e380-119">Namespaces are not physical locations, but are more like logical databases.</span></span>
<span data-ttu-id="8e380-120">Tous les espaces de noms WMI sont des instances de la classe système __Namespace.</span><span class="sxs-lookup"><span data-stu-id="8e380-120">All WMI namespaces are instances of the __Namespace system class.</span></span> <span data-ttu-id="8e380-121">L’espace de noms WMI par défaut est root \/ cimv2 (depuis Microsoft Windows 2000).</span><span class="sxs-lookup"><span data-stu-id="8e380-121">The default WMI namespace is Root\/CIMV2 (since Microsoft Windows 2000).</span></span> <span data-ttu-id="8e380-122">Pour utiliser Windows PowerShell afin d’obtenir les espaces de noms WMI dans la session active, utilisez une commande au format suivant.</span><span class="sxs-lookup"><span data-stu-id="8e380-122">To use Windows PowerShell to get WMI namespaces in the current session, use a command with the following format.</span></span>

```powershell
Get-WmiObject -Class __Namespace
```

<span data-ttu-id="8e380-123">Pour récupérer les espaces de noms WMI dans d’autres espaces de noms, utilisez le paramètre Namespace pour modifier l’emplacement de la recherche.</span><span class="sxs-lookup"><span data-stu-id="8e380-123">To get WMI namespaces in other namespaces, use the Namespace parameter to change the location of the search.</span></span> <span data-ttu-id="8e380-124">La commande suivante recherche les espaces de noms WMI qui résident dans l’espace de noms root/Cimv2/applications.</span><span class="sxs-lookup"><span data-stu-id="8e380-124">The following command finds WMI namespaces that reside in the Root/Cimv2/Applications namespace.</span></span>

```powershell
Get-WmiObject -Class __Namespace -Namespace root/CIMv2/applications
```

<span data-ttu-id="8e380-125">Les espaces de noms WMI sont hiérarchiques.</span><span class="sxs-lookup"><span data-stu-id="8e380-125">WMI namespaces are hierarchical.</span></span> <span data-ttu-id="8e380-126">Par conséquent, l’obtention d’une liste de tous les espaces de noms sur un système particulier requiert l’exécution d’une requête récursive commençant au niveau de l’espace de noms racine.</span><span class="sxs-lookup"><span data-stu-id="8e380-126">Therefore, obtaining a list of all namespaces on a particular system requires performing a recursive query starting at the root namespace.</span></span>

<span data-ttu-id="8e380-127">Les fournisseurs WMI exposent des informations sur les objets Windows gérables.</span><span class="sxs-lookup"><span data-stu-id="8e380-127">WMI Providers expose information about Windows manageable objects.</span></span> <span data-ttu-id="8e380-128">Un fournisseur récupère les données d’un composant et transmet ces données via WMI à une application de gestion, telle que Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8e380-128">A provider retrieves data from a component, and passes that data through WMI to a management application, such as Windows PowerShell.</span></span> <span data-ttu-id="8e380-129">La plupart des fournisseurs WMI sont des fournisseurs dynamiques, ce qui signifie qu’ils obtiennent les données dynamiquement lorsqu’elles sont demandées via l’application de gestion.</span><span class="sxs-lookup"><span data-stu-id="8e380-129">Most WMI providers are dynamic providers, which means that they obtain the data dynamically when it is requested through the management application.</span></span>

## <a name="finding-wmi-classes"></a><span data-ttu-id="8e380-130">RECHERCHE DE CLASSES WMI</span><span class="sxs-lookup"><span data-stu-id="8e380-130">FINDING WMI CLASSES</span></span>

<span data-ttu-id="8e380-131">Dans une installation par défaut de Windows 8, il y a plus de 1 100 classes WMI dans le \/ Cimv2 racine.</span><span class="sxs-lookup"><span data-stu-id="8e380-131">In a default installation of Windows 8, there are more than 1,100 WMI classes in Root\/Cimv2.</span></span> <span data-ttu-id="8e380-132">Avec ces nombreuses classes WMI, le défi consiste à identifier la classe WMI appropriée à utiliser pour effectuer une tâche spécifique.</span><span class="sxs-lookup"><span data-stu-id="8e380-132">With this many WMI classes, the challenge becomes identifying the appropriate WMI class to use to perform a specific task.</span></span> <span data-ttu-id="8e380-133">Windows PowerShell 3,0 offre deux façons de rechercher des classes WMI associées à une rubrique spécifique.</span><span class="sxs-lookup"><span data-stu-id="8e380-133">Windows PowerShell 3.0 provides two ways to find WMI classes that are related to a specific topic.</span></span>

<span data-ttu-id="8e380-134">Par exemple, pour rechercher des classes WMI dans l' \\ espace de noms WMI cimv2 racine qui sont liées aux disques, vous pouvez utiliser une requête telle que celle présentée ici.</span><span class="sxs-lookup"><span data-stu-id="8e380-134">For example,to find WMI classes in the root\\CIMV2 WMI namespace that are related to disks, you can use a query such as the one shown here.</span></span>

```powershell
Get-WmiObject -List *disk*
```

<span data-ttu-id="8e380-135">Pour rechercher des classes WMI associées à la mémoire, vous pouvez utiliser une requête telle que celle présentée ici.</span><span class="sxs-lookup"><span data-stu-id="8e380-135">To find WMI classes that are related to memory, you might use a query such as the one shown here.</span></span>

```powershell
Get-WmiObject -List *memory*
```

<span data-ttu-id="8e380-136">Les applets de commande CIM offrent également la possibilité de découvrir des classes WMI.</span><span class="sxs-lookup"><span data-stu-id="8e380-136">The CIM cmdlets also provide the ability to discover WMI classes.</span></span> <span data-ttu-id="8e380-137">Pour ce faire, utilisez l’applet de commande Get-CIMClass.</span><span class="sxs-lookup"><span data-stu-id="8e380-137">To do this, use the Get-CIMClass cmdlet.</span></span> <span data-ttu-id="8e380-138">La commande illustrée ci-dessous répertorie les classes WMI associées à la vidéo.</span><span class="sxs-lookup"><span data-stu-id="8e380-138">The command shown here lists WMI classes related to video.</span></span>

```powershell
Get-CimClass *video*
```

<span data-ttu-id="8e380-139">L’expansion de tabulation fonctionne lorsque vous modifiez les espaces de noms WMI et, par conséquent, l’utilisation de l’expansion de tabulation rend les espaces de noms sous-WMI facilement détectables.</span><span class="sxs-lookup"><span data-stu-id="8e380-139">Tab expansion works when changing WMI namespaces, and therefore use of tab expansion makes sub-WMI namespaces easily discoverable.</span></span> <span data-ttu-id="8e380-140">Dans l’exemple suivant, l’applet de commande Get-CimClass répertorie les classes WMI associées aux paramètres d’alimentation.</span><span class="sxs-lookup"><span data-stu-id="8e380-140">In the following example, the Get-CimClass cmdlet lists WMI classes related to power settings.</span></span>
<span data-ttu-id="8e380-141">Pour le trouver, tapez l' `root/CIMV2/` espace de noms, puis appuyez plusieurs fois sur la touche Tab jusqu’à ce que l’espace de noms Power apparaisse.</span><span class="sxs-lookup"><span data-stu-id="8e380-141">To find it, type the `root/CIMV2/` namespace and then press the Tab key several times until the power namespace appears.</span></span> <span data-ttu-id="8e380-142">Voici la commande :</span><span class="sxs-lookup"><span data-stu-id="8e380-142">Here is the command:</span></span>

```powershell
Get-CimClass *power* -Namespace root/cimv2/power
```
