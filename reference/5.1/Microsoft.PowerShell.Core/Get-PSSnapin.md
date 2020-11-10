---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSnapin
ms.openlocfilehash: 156cadecd87910e3c3312e84929b16709770641d
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388669"
---
# <span data-ttu-id="75880-103">Get-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="75880-103">Get-PSSnapin</span></span>

## <span data-ttu-id="75880-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="75880-104">SYNOPSIS</span></span>
<span data-ttu-id="75880-105">Obtient les composants logiciels enfichables Windows PowerShell sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="75880-105">Gets the Windows PowerShell snap-ins on the computer.</span></span>

## <span data-ttu-id="75880-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="75880-106">SYNTAX</span></span>

```
Get-PSSnapin [[-Name] <String[]>] [-Registered] [<CommonParameters>]
```

## <span data-ttu-id="75880-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="75880-107">DESCRIPTION</span></span>

<span data-ttu-id="75880-108">L' `Get-PSSnapin` applet de commande obtient les composants logiciels enfichables Windows PowerShell qui ont été ajoutés à la session active ou qui ont été inscrits sur le système.</span><span class="sxs-lookup"><span data-stu-id="75880-108">The `Get-PSSnapin` cmdlet gets the Windows PowerShell snap-ins that have been added to the current session or that have been registered on the system.</span></span> <span data-ttu-id="75880-109">Cette applet de commande répertorie les composants logiciels enfichables dans l’ordre dans lequel ils sont détectés.</span><span class="sxs-lookup"><span data-stu-id="75880-109">This cmdlet lists the snap-ins in the order in which they are detected.</span></span>

<span data-ttu-id="75880-110">`Get-PSSnapin` Obtient uniquement les composants logiciels enfichables inscrits. Pour inscrire un composant logiciel enfichable Windows PowerShell, utilisez l’outil InstallUtil inclus dans le Microsoft .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="75880-110">`Get-PSSnapin` gets only registered snap-ins. To register a Windows PowerShell snap-in, use the InstallUtil tool included with the Microsoft .NET Framework 2.0.</span></span> <span data-ttu-id="75880-111">Pour plus d’informations, consultez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="75880-111">For more information, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

<span data-ttu-id="75880-112">À compter de Windows PowerShell 3,0, les commandes de base qui sont incluses dans Windows PowerShell sont empaquetées dans des modules.</span><span class="sxs-lookup"><span data-stu-id="75880-112">Starting in Windows PowerShell 3.0, the core commands that are included in Windows PowerShell are packaged in modules.</span></span> <span data-ttu-id="75880-113">L'exception est **Microsoft.PowerShell.Core** , qui est un composant logiciel enfichable (PSSnapin).</span><span class="sxs-lookup"><span data-stu-id="75880-113">The exception is **Microsoft.PowerShell.Core** , which is a snap-in (PSSnapin).</span></span>
<span data-ttu-id="75880-114">Par défaut, seul le composant logiciel enfichable **Microsoft.PowerShell.Core** est ajouté à la session.</span><span class="sxs-lookup"><span data-stu-id="75880-114">By default, only the **Microsoft.PowerShell.Core** snap-in is added to the session.</span></span> <span data-ttu-id="75880-115">Les modules sont importés automatiquement à la première utilisation, et vous pouvez utiliser l' `Import-Module` applet de commande pour les importer.</span><span class="sxs-lookup"><span data-stu-id="75880-115">Modules are imported automatically on first use and you can use the `Import-Module` cmdlet to import them.</span></span>

## <span data-ttu-id="75880-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="75880-116">EXAMPLES</span></span>

### <span data-ttu-id="75880-117">Exemple 1 : récupérer les composants logiciels enfichables qui sont actuellement chargés</span><span class="sxs-lookup"><span data-stu-id="75880-117">Example 1: Get snap-ins that are currently loaded</span></span>

```
PS C:\> Get-PSSnapIn
```

<span data-ttu-id="75880-118">Cette commande obtient les composants logiciels enfichables Windows PowerShell qui sont actuellement chargés dans la session.</span><span class="sxs-lookup"><span data-stu-id="75880-118">This command gets the Windows PowerShell snap-ins that are currently loaded in the session.</span></span> <span data-ttu-id="75880-119">Cela inclut les composants logiciels enfichables qui sont installés avec Windows PowerShell et ceux qui ont été ajoutés à la session.</span><span class="sxs-lookup"><span data-stu-id="75880-119">This includes the snap-ins that are installed with Windows PowerShell and those that have been added to the session.</span></span>

### <span data-ttu-id="75880-120">Exemple 2 : obtenir les composants logiciels enfichables qui ont été inscrits</span><span class="sxs-lookup"><span data-stu-id="75880-120">Example 2: Get snap-ins that have been registered</span></span>

```
PS C:\> get-PSSnapIn -Registered
```

<span data-ttu-id="75880-121">Cette commande obtient les composants logiciels enfichables Windows PowerShell qui ont été inscrits sur l'ordinateur, y compris ceux qui ont déjà été ajoutés à la session.</span><span class="sxs-lookup"><span data-stu-id="75880-121">This command gets the Windows PowerShell snap-ins that have been registered on the computer, including those that have already been added to the session.</span></span> <span data-ttu-id="75880-122">La sortie n'inclut pas les composants logiciels enfichables qui sont installés avec Windows PowerShell ni les bibliothèques de liens dynamiques (DLL) de composants logiciels enfichables Windows PowerShell qui n'ont pas encore été inscrites sur le système.</span><span class="sxs-lookup"><span data-stu-id="75880-122">The output does not include snap-ins that are installed with Windows PowerShell or Windows PowerShell snap-in dynamic-link libraries (DLLs) that have not yet been registered on the system.</span></span>

### <span data-ttu-id="75880-123">Exemple 3 : obtenir les composants logiciels enfichables actuels qui correspondent à une chaîne</span><span class="sxs-lookup"><span data-stu-id="75880-123">Example 3: Get current snap-ins that match a string</span></span>

```
PS C:\> Get-PSSnapIn -Name smp*
```

<span data-ttu-id="75880-124">Cette commande obtient les composants logiciels enfichables Windows PowerShell dans la session active dont les noms commencent par SMP.</span><span class="sxs-lookup"><span data-stu-id="75880-124">This command gets the Windows PowerShell snap-ins in the current session that have names that begin with smp.</span></span>

## <span data-ttu-id="75880-125">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="75880-125">PARAMETERS</span></span>

### <span data-ttu-id="75880-126">-Name</span><span class="sxs-lookup"><span data-stu-id="75880-126">-Name</span></span>

<span data-ttu-id="75880-127">Spécifie un tableau de noms de composants logiciels enfichables.</span><span class="sxs-lookup"><span data-stu-id="75880-127">Specifies an array of snap-in names.</span></span> <span data-ttu-id="75880-128">Cette applet de commande obtient uniquement les composants logiciels enfichables Windows PowerShell spécifiés. Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="75880-128">This cmdlet gets only the specified Windows PowerShell snap-ins. Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="75880-129">-Inscrit</span><span class="sxs-lookup"><span data-stu-id="75880-129">-Registered</span></span>

<span data-ttu-id="75880-130">Indique que cette applet de commande obtient les composants logiciels enfichables Windows PowerShell qui ont été inscrits sur le système, même s’ils n’ont pas encore été ajoutés à la session.</span><span class="sxs-lookup"><span data-stu-id="75880-130">Indicates that this cmdlet gets the Windows PowerShell snap-ins that have been registered on the system even if they have not yet been added to the session.</span></span>

<span data-ttu-id="75880-131">Les composants logiciels enfichables qui sont installés avec Windows PowerShell n'apparaissent pas dans cette liste.</span><span class="sxs-lookup"><span data-stu-id="75880-131">The snap-ins that are installed with Windows PowerShell do not appear in this list.</span></span>

<span data-ttu-id="75880-132">Sans ce paramètre, `Get-PSSnapin` obtient les composants logiciels enfichables Windows PowerShell qui ont été ajoutés à la session.</span><span class="sxs-lookup"><span data-stu-id="75880-132">Without this parameter, `Get-PSSnapin` gets the Windows PowerShell snap-ins that have been added to the session.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="75880-133">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="75880-133">CommonParameters</span></span>

<span data-ttu-id="75880-134">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="75880-134">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="75880-135">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="75880-135">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="75880-136">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="75880-136">INPUTS</span></span>

### <span data-ttu-id="75880-137">Aucun</span><span class="sxs-lookup"><span data-stu-id="75880-137">None</span></span>
<span data-ttu-id="75880-138">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="75880-138">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="75880-139">SORTIES</span><span class="sxs-lookup"><span data-stu-id="75880-139">OUTPUTS</span></span>

### <span data-ttu-id="75880-140">System. Management. Automation. PSSnapInInfo</span><span class="sxs-lookup"><span data-stu-id="75880-140">System.Management.Automation.PSSnapInInfo</span></span>

<span data-ttu-id="75880-141">`Get-PSSnapin` retourne un objet pour chaque composant logiciel enfichable qu’il obtient.</span><span class="sxs-lookup"><span data-stu-id="75880-141">`Get-PSSnapin` returns an object for each snap-in that it gets.</span></span>

## <span data-ttu-id="75880-142">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="75880-142">NOTES</span></span>

<span data-ttu-id="75880-143">À compter de Windows PowerShell 3,0, les commandes de base qui sont installées avec Windows PowerShell sont empaquetées dans des modules.</span><span class="sxs-lookup"><span data-stu-id="75880-143">Starting in Windows PowerShell 3.0, the core commands that are installed with Windows PowerShell are packaged in modules.</span></span> <span data-ttu-id="75880-144">Dans Windows PowerShell 2,0 et dans les programmes hôtes qui créent des sessions de style plus anciennes dans les versions ultérieures de Windows PowerShell, les commandes de base sont empaquetées dans des composants logiciels enfichables ( **PSSnapin** ).</span><span class="sxs-lookup"><span data-stu-id="75880-144">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of Windows PowerShell, the core commands are packaged in snap-ins ( **PSSnapin** ).</span></span> <span data-ttu-id="75880-145">L’exception est **Microsoft. PowerShell. Core** , qui est toujours un composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="75880-145">The exception is **Microsoft.PowerShell.Core** , which is always a snap-in.</span></span> <span data-ttu-id="75880-146">En outre, les sessions à distance, telles que celles démarrées par l’applet de commande `New-PSSession` , sont des sessions de style plus anciennes qui incluent des composants logiciels enfichables principaux.</span><span class="sxs-lookup"><span data-stu-id="75880-146">Also, remote sessions, such as those started by the `New-PSSession` cmdlet, are older-style sessions that include core snap-ins.</span></span>

 <span data-ttu-id="75880-147">Pour plus d’informations sur la méthode **CreateDefault2** qui crée des sessions de style plus récentes avec des modules de base, consultez [méthode CreateDefault2](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2#System_Management_Automation_Runspaces_InitialSessionState_CreateDefault2).</span><span class="sxs-lookup"><span data-stu-id="75880-147">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see [CreateDefault2 Method](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2#System_Management_Automation_Runspaces_InitialSessionState_CreateDefault2).</span></span>

## <span data-ttu-id="75880-148">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="75880-148">RELATED LINKS</span></span>

[<span data-ttu-id="75880-149">Add-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="75880-149">Add-PSSnapin</span></span>](Add-PSSnapin.md)

[<span data-ttu-id="75880-150">Remove-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="75880-150">Remove-PSSnapin</span></span>](Remove-PSSnapin.md)
