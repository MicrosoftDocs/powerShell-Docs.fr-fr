---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/add-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-PSSnapin
ms.openlocfilehash: a21c2974fd66a9b02929752ae487c8995579b8a7
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388822"
---
# <span data-ttu-id="8a142-103">Add-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="8a142-103">Add-PSSnapin</span></span>

## <span data-ttu-id="8a142-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8a142-104">SYNOPSIS</span></span>
<span data-ttu-id="8a142-105">Ajoute un ou plusieurs composants logiciels enfichables Windows PowerShell à la session active.</span><span class="sxs-lookup"><span data-stu-id="8a142-105">Adds one or more Windows PowerShell snap-ins to the current session.</span></span>

## <span data-ttu-id="8a142-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="8a142-106">SYNTAX</span></span>

```
Add-PSSnapin [-Name] <String[]> [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="8a142-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8a142-107">DESCRIPTION</span></span>

<span data-ttu-id="8a142-108">L' `Add-PSSnapin` applet de commande ajoute les composants logiciels enfichables Windows PowerShell inscrits à la session active.</span><span class="sxs-lookup"><span data-stu-id="8a142-108">The `Add-PSSnapin` cmdlet adds registered Windows PowerShell snap-ins to the current session.</span></span> <span data-ttu-id="8a142-109">Après avoir ajouté les composants logiciels enfichables, vous pouvez utiliser les applets de commande et les fournisseurs pris en charge par les composants logiciels enfichables dans la session active.</span><span class="sxs-lookup"><span data-stu-id="8a142-109">After the snap-ins are added, you can use the cmdlets and providers that the snap-ins support in the current session.</span></span>

<span data-ttu-id="8a142-110">Pour ajouter le composant logiciel enfichable à toutes les futures sessions Windows PowerShell, ajoutez une `Add-PSSnapin` commande à votre profil Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8a142-110">To add the snap-in to all future Windows PowerShell sessions, add an `Add-PSSnapin` command to your Windows PowerShell profile.</span></span> <span data-ttu-id="8a142-111">Pour plus d’informations, consultez [about_Profiles](about/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="8a142-111">For more information, see [about_Profiles](about/about_Profiles.md).</span></span>

<span data-ttu-id="8a142-112">À compter de Windows PowerShell 3.0, les commandes de base qui sont incluses dans Windows PowerShell sont packagés dans des modules.</span><span class="sxs-lookup"><span data-stu-id="8a142-112">Beginning in Windows PowerShell 3.0, the core commands that are included in Windows PowerShell are packaged in modules.</span></span> <span data-ttu-id="8a142-113">L'exception est **Microsoft.PowerShell.Core** , qui est un composant logiciel enfichable (PSSnapin).</span><span class="sxs-lookup"><span data-stu-id="8a142-113">The exception is **Microsoft.PowerShell.Core** , which is a snap-in (PSSnapin).</span></span>
<span data-ttu-id="8a142-114">Par défaut, seul le composant logiciel enfichable **Microsoft.PowerShell.Core** est ajouté à la session.</span><span class="sxs-lookup"><span data-stu-id="8a142-114">By default, only the **Microsoft.PowerShell.Core** snap-in is added to the session.</span></span> <span data-ttu-id="8a142-115">Les modules sont importés automatiquement à la première utilisation, et vous pouvez utiliser l’applet de commande Import-Module pour les importer.</span><span class="sxs-lookup"><span data-stu-id="8a142-115">Modules are imported automatically on first use and you can use the Import-Module cmdlet to import them.</span></span>

## <span data-ttu-id="8a142-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8a142-116">EXAMPLES</span></span>

### <span data-ttu-id="8a142-117">Exemple 1 : ajouter des composants logiciels enfichables</span><span class="sxs-lookup"><span data-stu-id="8a142-117">Example 1: Add snap-ins</span></span>

```powershell
PS C:\> Add-PSSnapIn -Name Microsoft.Exchange, Microsoft.Windows.AD
```

<span data-ttu-id="8a142-118">Cette commande ajoute les composants logiciels enfichables Microsoft Exchange et Active Directory à la session active.</span><span class="sxs-lookup"><span data-stu-id="8a142-118">This command adds the Microsoft Exchange and Active Directory snap-ins to the current session.</span></span>

### <span data-ttu-id="8a142-119">Exemple 2 : ajouter tous les composants logiciels enfichables inscrits</span><span class="sxs-lookup"><span data-stu-id="8a142-119">Example 2: Add all the registered snap-ins</span></span>

```powershell
PS C:\> Get-PSSnapin -Registered | Add-PSSnapin -Passthru
```

<span data-ttu-id="8a142-120">Cette commande ajoute tous les composants logiciels enfichables Windows PowerShell inscrits à la session.</span><span class="sxs-lookup"><span data-stu-id="8a142-120">This command adds all of the registered Windows PowerShell snap-ins to the session.</span></span> <span data-ttu-id="8a142-121">Elle utilise l’applet de commande Get-PSSnapin avec le paramètre **Registered** pour récupérer des objets représentant chacun des composants logiciels enfichables inscrits. L’opérateur de pipeline (|) passe le résultat à `Add-PSSnapin` , qui les ajoute à la session.</span><span class="sxs-lookup"><span data-stu-id="8a142-121">It uses the Get-PSSnapin cmdlet with the **Registered** parameter to get objects representing each of the registered snap-ins. The pipeline operator (|) passes the result to `Add-PSSnapin`, which adds them to the session.</span></span> <span data-ttu-id="8a142-122">Le paramètre **PassThru** retourne des objets qui représentent chacun des composants logiciels enfichables ajoutés.</span><span class="sxs-lookup"><span data-stu-id="8a142-122">The **PassThru** parameter returns objects that represent each of the added snap-ins.</span></span>

### <span data-ttu-id="8a142-123">Exemple 3 : inscrire un composant logiciel enfichable et l’ajouter</span><span class="sxs-lookup"><span data-stu-id="8a142-123">Example 3: Register a snap-in and add it</span></span>

<span data-ttu-id="8a142-124">La première commande obtient les composants logiciels enfichables qui ont été ajoutés à la session active qui incluent les composants logiciels enfichables qui sont installés avec Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8a142-124">The first command gets snap-ins that have been added to the current session that include the snap-ins that are installed with Windows PowerShell.</span></span> <span data-ttu-id="8a142-125">Dans cet exemple, ManagementFeatures n'est pas retourné.</span><span class="sxs-lookup"><span data-stu-id="8a142-125">In this example, ManagementFeatures is not returned.</span></span> <span data-ttu-id="8a142-126">Cela indique qu'il n'a pas été ajouté à la session.</span><span class="sxs-lookup"><span data-stu-id="8a142-126">This indicates that it has not been added to the session.</span></span>

<span data-ttu-id="8a142-127">La deuxième commande récupère les composants logiciels enfichables qui ont été inscrits sur votre système, y compris ceux qui ont déjà été ajoutés à la session.</span><span class="sxs-lookup"><span data-stu-id="8a142-127">The second command gets snap-ins that have been registered on your system, which includes those that have already been added to the session.</span></span> <span data-ttu-id="8a142-128">Il n’inclut pas les composants logiciels enfichables qui sont installés avec Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8a142-128">It does not include the snap-ins that are installed with Windows PowerShell.</span></span> <span data-ttu-id="8a142-129">Dans ce cas, la commande ne retourne aucun composant logiciel enfichable. Cela indique que le composant logiciel enfichable ManagementFeatures n’a pas été inscrit sur le système.</span><span class="sxs-lookup"><span data-stu-id="8a142-129">In this case, the command does not return any snap-ins. This indicates that the ManagementFeatures snapin has not been registered on the system.</span></span>

<span data-ttu-id="8a142-130">La troisième commande crée un alias, installutil, pour le chemin d’accès de l’outil InstallUtil dans .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8a142-130">The third command creates an alias, installutil, for the path of the InstallUtil tool in .NET Framework.</span></span>

<span data-ttu-id="8a142-131">La quatrième commande utilise l’outil InstallUtil pour inscrire le composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="8a142-131">The fourth command uses the InstallUtil tool to register the snap-in.</span></span> <span data-ttu-id="8a142-132">La commande spécifie le chemin d’accès de ManagementCmdlets.dll, le nom de fichier ou le nom de module du composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="8a142-132">The command specifies the path of ManagementCmdlets.dll, the filename or module name of the snap-in.</span></span>

<span data-ttu-id="8a142-133">La cinquième commande est identique à la deuxième commande.</span><span class="sxs-lookup"><span data-stu-id="8a142-133">The fifth command is the same as the second command.</span></span> <span data-ttu-id="8a142-134">Cette fois, vous l'utilisez pour vérifier que le composant logiciel enfichable ManagementCmdlets est inscrit.</span><span class="sxs-lookup"><span data-stu-id="8a142-134">This time, you use it to verify that the ManagementCmdlets snap-in is registered.</span></span>

<span data-ttu-id="8a142-135">La sixième commande utilise l' `Add-PSSnapin` applet de commande pour ajouter le composant logiciel enfichable ManagementFeatures à la session.</span><span class="sxs-lookup"><span data-stu-id="8a142-135">The sixth command uses the `Add-PSSnapin` cmdlet to add the ManagementFeatures snap-in to the session.</span></span> <span data-ttu-id="8a142-136">Elle spécifie le nom du composant logiciel enfichable, ManagementFeatures, et non pas le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="8a142-136">It specifies the name of the snap-in, ManagementFeatures, not the file name.</span></span>

<span data-ttu-id="8a142-137">Pour vérifier que le composant logiciel enfichable est ajouté à la session, la septième commande utilise le paramètre **module** de l’applet de commande Get-Command.</span><span class="sxs-lookup"><span data-stu-id="8a142-137">To verify that the snap-in is added to the session, the seventh command uses the **Module** parameter of the Get-Command cmdlet.</span></span> <span data-ttu-id="8a142-138">Elle affiche les éléments qui ont été ajoutés à la session par un composant logiciel enfichable ou un module.</span><span class="sxs-lookup"><span data-stu-id="8a142-138">It displays the items that were added to the session by a snap-in or module.</span></span>

<span data-ttu-id="8a142-139">Vous pouvez également utiliser la propriété **PSSnapin** de l’objet retourné par l' `Get-Command` applet de commande pour trouver le composant logiciel enfichable ou le module dans lequel provient une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8a142-139">You can also use the **PSSnapin** property of the object that the `Get-Command` cmdlet returns to find the snap-in or module in which a cmdlet originated.</span></span> <span data-ttu-id="8a142-140">La huitième commande utilise la notation par points pour rechercher la valeur de la propriété PSSnapin de l’applet de commande Set-Alias.</span><span class="sxs-lookup"><span data-stu-id="8a142-140">The eighth command uses dot notation to find the value of the PSSnapin property of the Set-Alias cmdlet.</span></span>

```powershell
PS C:\> Get-PSSnapin
PS C:\> Get-PSSnapin -Registered
PS C:\> Set-Alias installutil $env:windir\Microsoft.NET\Framework\v2.0.50727\installutil.exe
PS C:\> installutil C:\Dev\Management\ManagementCmdlets.dll
PS C:\> Get-PSSnapin -Registered
PS C:\> add-pssnapin ManagementFeatures
PS C:\> Get-Command -Module ManagementFeatures
PS C:\> (Get-Command Set-Alias).pssnapin
```

<span data-ttu-id="8a142-141">Cet exemple montre le processus d'inscription d'un composant logiciel enfichable sur votre système, puis son ajout à votre session.</span><span class="sxs-lookup"><span data-stu-id="8a142-141">This example demonstrates the process of registering a snap-in on your system and then adding it to your session.</span></span> <span data-ttu-id="8a142-142">Elle utilise ManagementFeatures, un composant logiciel enfichable fictif implémenté dans un fichier nommé ManagementCmdlets.dll.</span><span class="sxs-lookup"><span data-stu-id="8a142-142">It uses ManagementFeatures, a fictitious snap-in implemented in a file that is named ManagementCmdlets.dll.</span></span>

## <span data-ttu-id="8a142-143">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="8a142-143">PARAMETERS</span></span>

### <span data-ttu-id="8a142-144">-Name</span><span class="sxs-lookup"><span data-stu-id="8a142-144">-Name</span></span>

<span data-ttu-id="8a142-145">Spécifie le nom du composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="8a142-145">Specifies the name of the snap-in.</span></span> <span data-ttu-id="8a142-146">Il s’agit du nom, et non de AssemblyName ou ModuleName.</span><span class="sxs-lookup"><span data-stu-id="8a142-146">This is the Name, not the AssemblyName or ModuleName.</span></span> <span data-ttu-id="8a142-147">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="8a142-147">Wildcards are permitted.</span></span>

<span data-ttu-id="8a142-148">Pour rechercher les noms des composants logiciels enfichables inscrits sur votre système, tapez `Get-PSSnapin -Registered` .</span><span class="sxs-lookup"><span data-stu-id="8a142-148">To find the names of the registered snap-ins on your system, type `Get-PSSnapin -Registered`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="8a142-149">-PassThru</span><span class="sxs-lookup"><span data-stu-id="8a142-149">-PassThru</span></span>

<span data-ttu-id="8a142-150">Indique que cette applet de commande retourne un objet qui représente chaque composant logiciel enfichable ajouté.</span><span class="sxs-lookup"><span data-stu-id="8a142-150">Indicates that this cmdlet returns an object that represents each added snap-in.</span></span> <span data-ttu-id="8a142-151">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="8a142-151">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="8a142-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8a142-152">CommonParameters</span></span>

<span data-ttu-id="8a142-153">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8a142-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8a142-154">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8a142-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8a142-155">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8a142-155">INPUTS</span></span>

### <span data-ttu-id="8a142-156">Aucun</span><span class="sxs-lookup"><span data-stu-id="8a142-156">None</span></span>
<span data-ttu-id="8a142-157">Vous ne pouvez pas rediriger des objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8a142-157">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="8a142-158">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8a142-158">OUTPUTS</span></span>

### <span data-ttu-id="8a142-159">None ou System. Management. Automation. PSSnapInInfo</span><span class="sxs-lookup"><span data-stu-id="8a142-159">None or System.Management.Automation.PSSnapInInfo</span></span>

<span data-ttu-id="8a142-160">Cette applet de commande retourne un objet PSSnapInInfo qui représente le composant logiciel enfichable si vous spécifiez le paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="8a142-160">This cmdlet returns a PSSnapInInfo object that represents the snap-in if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="8a142-161">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="8a142-161">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="8a142-162">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8a142-162">NOTES</span></span>

- <span data-ttu-id="8a142-163">À compter de Windows PowerShell 3.0, les commandes de base qui sont installées avec Windows PowerShell sont packagées dans des modules.</span><span class="sxs-lookup"><span data-stu-id="8a142-163">Beginning in Windows PowerShell 3.0, the core commands that are installed with Windows PowerShell are packaged in modules.</span></span> <span data-ttu-id="8a142-164">Dans Windows PowerShell 2,0 et dans les programmes hôtes qui créent des sessions de style plus anciennes dans les versions ultérieures de Windows PowerShell, les commandes de base sont empaquetées dans des composants logiciels enfichables (PSSnapins).</span><span class="sxs-lookup"><span data-stu-id="8a142-164">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of Windows PowerShell, the core commands are packaged in snap-ins (PSSnapins).</span></span> <span data-ttu-id="8a142-165">L’exception est **Microsoft. PowerShell. Core** , qui est toujours un composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="8a142-165">The exception is **Microsoft.PowerShell.Core** , which is always a snap-in.</span></span> <span data-ttu-id="8a142-166">En outre, les sessions à distance, telles que celles démarrées par l’applet de commande New-PSSession, sont des sessions de style plus anciennes qui incluent des composants logiciels enfichables principaux.</span><span class="sxs-lookup"><span data-stu-id="8a142-166">Also, remote sessions, such as those started by the New-PSSession cmdlet, are older-style sessions that include core snap-ins.</span></span>

  <span data-ttu-id="8a142-167">Pour plus d’informations sur la méthode **CreateDefault2** qui crée des sessions de style plus récentes avec des modules de base, consultez [méthode CreateDefault2](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2#System_Management_Automation_Runspaces_InitialSessionState_CreateDefault2).</span><span class="sxs-lookup"><span data-stu-id="8a142-167">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see [CreateDefault2 Method](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2#System_Management_Automation_Runspaces_InitialSessionState_CreateDefault2).</span></span>

- <span data-ttu-id="8a142-168">Pour plus d’informations sur les composants logiciels enfichables, consultez [about_Pssnapins](About/about_PSSnapins.md) et [comment créer un composant logiciel enfichable Windows PowerShell](/powershell/scripting/developer/cmdlet/how-to-create-a-windows-powershell-snap-in).</span><span class="sxs-lookup"><span data-stu-id="8a142-168">For more information about snap-ins, see [about_PSSnapins](About/about_PSSnapins.md) and [How to Create a Windows PowerShell Snap-in](/powershell/scripting/developer/cmdlet/how-to-create-a-windows-powershell-snap-in).</span></span>
- <span data-ttu-id="8a142-169">`Add-PSSnapin` Ajoute le composant logiciel enfichable uniquement à la session active.</span><span class="sxs-lookup"><span data-stu-id="8a142-169">`Add-PSSnapin` adds the snap-in only to the current session.</span></span> <span data-ttu-id="8a142-170">Pour ajouter le composant logiciel enfichable à toutes les sessions Windows PowerShell, ajoutez-le à votre profil Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8a142-170">To add the snap-in to all Windows PowerShell sessions, add it to your Windows PowerShell profile.</span></span> <span data-ttu-id="8a142-171">Pour plus d'informations, consultez about_Providers.</span><span class="sxs-lookup"><span data-stu-id="8a142-171">For more information, see about_Profiles.</span></span>
- <span data-ttu-id="8a142-172">Vous pouvez ajouter n’importe quel composant logiciel enfichable qui a été inscrit à l’aide de l’utilitaire d’installation Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8a142-172">You can add any snap-in that has been registered using the Microsoft .NET Framework install utility.</span></span> <span data-ttu-id="8a142-173">Pour plus d’informations, consultez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="8a142-173">For more information, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>
- <span data-ttu-id="8a142-174">Pour obtenir la liste des composants logiciels enfichables inscrits sur votre ordinateur, tapez `Get-PSSnapin -Registered` .</span><span class="sxs-lookup"><span data-stu-id="8a142-174">To get a list of snap-ins that are registered on your computer, type `Get-PSSnapin -Registered`.</span></span>
- <span data-ttu-id="8a142-175">Avant d’ajouter un composant logiciel enfichable, `Add-PSSnapin` vérifie la version du composant logiciel enfichable pour s’assurer qu’il est compatible avec la version actuelle de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8a142-175">Before adding a snap-in, `Add-PSSnapin` checks the version of the snap-in to verify that it is compatible with the current version of Windows PowerShell.</span></span> <span data-ttu-id="8a142-176">Si la version du composant logiciel enfichable n'est pas compatible, Windows PowerShell signale une erreur.</span><span class="sxs-lookup"><span data-stu-id="8a142-176">If the snap-in fails the version check, Windows PowerShell reports an error.</span></span>

## <span data-ttu-id="8a142-177">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8a142-177">RELATED LINKS</span></span>

[<span data-ttu-id="8a142-178">Get-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="8a142-178">Get-PSSnapin</span></span>](Get-PSSnapin.md)

[<span data-ttu-id="8a142-179">Remove-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="8a142-179">Remove-PSSnapin</span></span>](Remove-PSSnapin.md)
