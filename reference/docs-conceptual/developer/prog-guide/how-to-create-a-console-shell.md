---
title: Comment créer un interpréteur de commandes de console | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Make-Shell [PowerShell Programmer's Guide]
ms.assetid: 6c24dd44-a8ec-421d-ac86-90912e1a8cc6
caps.latest.revision: 5
ms.openlocfilehash: 7166881bd1403ea8c81ec2928321f6b93e3ac58d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360268"
---
# <a name="how-to-create-a-console-shell"></a><span data-ttu-id="fce59-102">Guide pratique pour créer un shell de console</span><span class="sxs-lookup"><span data-stu-id="fce59-102">How to Create a Console Shell</span></span>

<span data-ttu-id="fce59-103">Windows PowerShell fournit un outil make-shell, également appelé « make-Kit », qui est utilisé pour créer un interpréteur de commandes de console qui n’est pas extensible.</span><span class="sxs-lookup"><span data-stu-id="fce59-103">Windows PowerShell provides a Make-Shell tool, also referred to as the "make-kit", that is used to create a console shell that is not extensible.</span></span> <span data-ttu-id="fce59-104">Les coques créées avec ce nouvel outil ne peuvent pas être étendues ultérieurement via un composant logiciel enfichable Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fce59-104">Shells created with this new tool cannot be extended later through a Windows PowerShell snap-in.</span></span>

## <a name="syntax"></a><span data-ttu-id="fce59-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fce59-105">Syntax</span></span>

<span data-ttu-id="fce59-106">Voici la syntaxe utilisée pour exécuter make-shell à partir d’un fichier make-file.</span><span class="sxs-lookup"><span data-stu-id="fce59-106">Here is the syntax used to run Make-Shell from within a make-file.</span></span>

```
make-shell
  -out n.exe
  -namespace ns
  [ -lib libdirectory1[,libdirectory2,..] ]
  [ -reference ca1.dll[,ca2.dll,...] ]
  [ -formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...] ]
  [ -typedata td1.type.ps1xml[,td2.type.ps1xml,...] ]
  [ -source c1.cs [,c2.cs,...] ]
  [ -authorizationmanager authorizationManagerType ]
  [ -win32icon i.ico ]
  [ -initscript p.ps1 ]
  [ -builtinscript s1.ps1[,s2.ps1,...] ]
  [ -resource resourcefile.txt ]
  [ -cscflags cscFlags ]
  [ -? | -help ]
```

## <a name="parameters"></a><span data-ttu-id="fce59-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fce59-107">Parameters</span></span>

<span data-ttu-id="fce59-108">Voici une brève description des paramètres de make-shell.</span><span class="sxs-lookup"><span data-stu-id="fce59-108">Here is a brief description of the parameters of Make-Shell.</span></span>

> [!CAUTION]
> <span data-ttu-id="fce59-109">Les chemins d’accès UNC aux assemblys ne sont pas pris en charge par make-shell.</span><span class="sxs-lookup"><span data-stu-id="fce59-109">UNC paths to assemblies are not supported by Make-Shell.</span></span>

|<span data-ttu-id="fce59-110">Paramètre</span><span class="sxs-lookup"><span data-stu-id="fce59-110">Parameter</span></span>|<span data-ttu-id="fce59-111">Description</span><span class="sxs-lookup"><span data-stu-id="fce59-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="fce59-112">-out n. exe</span><span class="sxs-lookup"><span data-stu-id="fce59-112">-out n.exe</span></span>|<span data-ttu-id="fce59-113">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="fce59-113">Required.</span></span> <span data-ttu-id="fce59-114">Nom de l’interpréteur de commandes à produire.</span><span class="sxs-lookup"><span data-stu-id="fce59-114">The name of the shell to produce.</span></span> <span data-ttu-id="fce59-115">Le chemin d’accès est spécifié dans le cadre de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="fce59-115">The path is specified as part of this parameter.</span></span><br /><br /> <span data-ttu-id="fce59-116">Make-shell ajoute « . exe » à cette valeur, s’il n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="fce59-116">Make-shell will append ".exe" to this value if it is not specified.</span></span> <span data-ttu-id="fce59-117">**Attention :**  Ne créez pas de fichier de sortie portant le même nom que le fichier. dll référencé.</span><span class="sxs-lookup"><span data-stu-id="fce59-117">**Caution:**  Do not create an output file with the same name as the referenced .dll file.</span></span> <span data-ttu-id="fce59-118">Si vous tentez cette opération, l’outil make-shell crée un fichier. cs portant le même nom, ce qui remplace le fichier. cs qui contient le code source de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="fce59-118">If you attempt this, the Make-Shell tool creates a .cs file with the same name, which will overwrite the .cs file that has your cmdlet source code.</span></span>|
|<span data-ttu-id="fce59-119">-namespace NS</span><span class="sxs-lookup"><span data-stu-id="fce59-119">-namespace ns</span></span>|<span data-ttu-id="fce59-120">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="fce59-120">Required.</span></span> <span data-ttu-id="fce59-121">Espace de noms à utiliser pour la classe [System. Management. Automation. instances d’exécution. Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) dérivée que make-Kit génère et compile.</span><span class="sxs-lookup"><span data-stu-id="fce59-121">The namespace to use for the derived [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) class that the make-kit generates and compiles.</span></span>|
|<span data-ttu-id="fce59-122">-lib libdirectory1 [, libdirectory2,..]</span><span class="sxs-lookup"><span data-stu-id="fce59-122">-lib libdirectory1[,libdirectory2,..]</span></span>|<span data-ttu-id="fce59-123">Les répertoires dans lesquels sont recherchés les assemblys .NET, y compris les assemblys Windows PowerShell, les assemblys spécifiés par le paramètre `reference`, les assemblys indirectement référencés par un autre assembly et les assemblys système .NET.</span><span class="sxs-lookup"><span data-stu-id="fce59-123">The directories that are searched for .NET assemblies, including the Windows PowerShell assemblies, assemblies specified by the `reference` parameter, assemblies indirectly referenced by another assembly, and the .NET system assemblies.</span></span>|
|<span data-ttu-id="fce59-124">-Reference CA1. dll [, Ca2. dll,...]</span><span class="sxs-lookup"><span data-stu-id="fce59-124">-reference ca1.dll[,ca2.dll,...]</span></span>|<span data-ttu-id="fce59-125">Liste séparée par des virgules des assemblys à inclure dans l’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="fce59-125">A comma-separated list of the assemblies to include in the shell.</span></span> <span data-ttu-id="fce59-126">Ces assemblys incluent tous les assemblys d’applet de commande et de fournisseur, ainsi que les assemblys de ressource qui doivent être chargés.</span><span class="sxs-lookup"><span data-stu-id="fce59-126">These assemblies  includes all cmdlet and provider assemblies, as well as resource assemblies that should be loaded.</span></span> <span data-ttu-id="fce59-127">Si ce paramètre n’est pas spécifié, un interpréteur de commandes qui contient uniquement les applets de commande et les fournisseurs de base fournis par Windows PowerShell est généré.</span><span class="sxs-lookup"><span data-stu-id="fce59-127">If this parameter is not specified, then a shell is produced that contains only the core cmdlets and providers provided by Windows PowerShell.</span></span><br /><br /> <span data-ttu-id="fce59-128">Les assemblys peuvent être spécifiés à l’aide de leur chemin d’accès complet. dans le cas contraire, ils seront recherchés à l’aide du chemin d’accès spécifié par le paramètre `lib`.</span><span class="sxs-lookup"><span data-stu-id="fce59-128">The assemblies can be specified using their full path, otherwise they will be searched for using the path specified by the `lib` parameter.</span></span>|
|<span data-ttu-id="fce59-129">-FormatData FD1 en. format. ps1xml [, FD2. format. ps1xml,...]</span><span class="sxs-lookup"><span data-stu-id="fce59-129">-formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...]</span></span>|<span data-ttu-id="fce59-130">Liste séparée par des virgules des données de format à inclure dans l’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="fce59-130">A comma-separated list of format data to include in the shell.</span></span> <span data-ttu-id="fce59-131">Si ce paramètre n’est pas spécifié, un interpréteur de commandes qui contient uniquement les données de format fournies par Windows PowerShell est généré.</span><span class="sxs-lookup"><span data-stu-id="fce59-131">If this parameter is not specified, then a shell is produced that contains only the format data provided by Windows PowerShell.</span></span>|
|<span data-ttu-id="fce59-132">-TypeData TD1. type. ps1xml [, TD2. type. ps1xml,...]</span><span class="sxs-lookup"><span data-stu-id="fce59-132">-typedata td1.type.ps1xml[,td2.type.ps1xml,...]</span></span>|<span data-ttu-id="fce59-133">Liste séparée par des virgules des données de type à inclure dans l’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="fce59-133">A comma-separated list of type data to include in the shell.</span></span> <span data-ttu-id="fce59-134">Si ce paramètre n’est pas spécifié, un interpréteur de commandes qui contient uniquement les données de type fournies par Windows PowerShell est généré.</span><span class="sxs-lookup"><span data-stu-id="fce59-134">If this parameter is not specified, then a shell is produced that contains only the type data provided by Windows PowerShell.</span></span>|
|<span data-ttu-id="fce59-135">-source c1.cs [, c2.cs,...]</span><span class="sxs-lookup"><span data-stu-id="fce59-135">-source c1.cs [,c2.cs,...]</span></span>|<span data-ttu-id="fce59-136">Nom d’un fichier, fourni par le développeur de l’interpréteur de commandes, qui contient le code source nécessaire pour générer le shell.</span><span class="sxs-lookup"><span data-stu-id="fce59-136">The name of a file, provided by the shell developer, that contains any source code needed to build the shell.</span></span><br /><br /> <span data-ttu-id="fce59-137">Le fichier de code source peut contenir l’un des codes source suivants :</span><span class="sxs-lookup"><span data-stu-id="fce59-137">The source code file can contain any of the following source code:</span></span><br /><br /> <span data-ttu-id="fce59-138">: Implémentation du gestionnaire d’autorisations qui remplace le gestionnaire d’autorisations par défaut.</span><span class="sxs-lookup"><span data-stu-id="fce59-138">-   The Authorization manager implementation that overrides the default authorization manager.</span></span> <span data-ttu-id="fce59-139">(Cela peut également être fourni dans un assembly.)</span><span class="sxs-lookup"><span data-stu-id="fce59-139">(This could also be supplied compiled into an assembly.)</span></span><br /><span data-ttu-id="fce59-140">-Déclarations d’attribut d’informations d’assembly : telles que AssemblyCompanyAttribute, AssemblyCopyrightAttribute, AssemblyFileVersionAttribute, AssemblyInformationalVersionAttribute, AssemblyProductAttribute et AssemblyTrademarkAttribute.</span><span class="sxs-lookup"><span data-stu-id="fce59-140">-   Assembly informational attribute declarations: such as the AssemblyCompanyAttribute, AssemblyCopyrightAttribute, AssemblyFileVersionAttribute, AssemblyInformationalVersionAttribute, AssemblyProductAttribute, and AssemblyTrademarkAttribute.</span></span>|
|<span data-ttu-id="fce59-141">-authorizationmanager authorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="fce59-141">-authorizationmanager authorizationManagerType</span></span>|<span data-ttu-id="fce59-142">Type qui contient l’implémentation du gestionnaire d’autorisations.</span><span class="sxs-lookup"><span data-stu-id="fce59-142">The type that contains the authorization manager implementation.</span></span> <span data-ttu-id="fce59-143">Cela peut être défini dans le code source ou compilé dans un assembly (spécifié par le paramètre `reference`).</span><span class="sxs-lookup"><span data-stu-id="fce59-143">This can be defined in source code, or compiled into an assembly (specified by the `reference` parameter).</span></span> <span data-ttu-id="fce59-144">Si ce paramètre n’est pas spécifié, le gestionnaire de sécurité par défaut est utilisé.</span><span class="sxs-lookup"><span data-stu-id="fce59-144">If this parameter is not specified, the default security manager is used.</span></span> <span data-ttu-id="fce59-145">La valeur doit être le nom de type complet, y compris les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="fce59-145">The value should be the full type name, including namespaces.</span></span>|
|<span data-ttu-id="fce59-146">-win32icon i. ico</span><span class="sxs-lookup"><span data-stu-id="fce59-146">-win32icon i.ico</span></span>|<span data-ttu-id="fce59-147">Icône du fichier. exe pour l’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="fce59-147">The icon for the .exe file for the shell.</span></span> <span data-ttu-id="fce59-148">S’il n’est pas spécifié, l’interpréteur de commandes aura l’icône include par le compilateur c# (le cas échéant).</span><span class="sxs-lookup"><span data-stu-id="fce59-148">If not specified, then the shell will have the icon that the c# compiler includes (if any).</span></span>|
|<span data-ttu-id="fce59-149">-initscript p. ps1</span><span class="sxs-lookup"><span data-stu-id="fce59-149">-initscript p.ps1</span></span>|<span data-ttu-id="fce59-150">Profil de démarrage de l’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="fce59-150">The startup profile for the shell.</span></span> <span data-ttu-id="fce59-151">Le fichier est inclus « en l’or »; aucune vérification de validité n’est effectuée par make-shell.</span><span class="sxs-lookup"><span data-stu-id="fce59-151">The file is included "as-is"; no validity checking is done by Make-Shell.</span></span>|
|<span data-ttu-id="fce59-152">-builtinscript S1. ps1 [, S2. ps1,...]</span><span class="sxs-lookup"><span data-stu-id="fce59-152">-builtinscript s1.ps1[,s2.ps1,...]</span></span>|<span data-ttu-id="fce59-153">Liste de scripts intégrés pour l’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="fce59-153">A list of built-in scripts for the shell.</span></span> <span data-ttu-id="fce59-154">Ces scripts sont découverts avant les scripts dans le chemin d’accès et leur contenu ne peut pas être modifié une fois l’interpréteur de commandes généré.</span><span class="sxs-lookup"><span data-stu-id="fce59-154">These scripts are discovered before scripts in the path, and their contents cannot be changed once the shell is built.</span></span><br /><br /> <span data-ttu-id="fce59-155">Les fichiers sont inclus « en l’absence »; aucune vérification de validité n’est effectuée par make-shell.</span><span class="sxs-lookup"><span data-stu-id="fce59-155">The files are included "as-is"; no validity checking is done by Make-Shell.</span></span>|
|<span data-ttu-id="fce59-156">-ressource ResourceFile. txt</span><span class="sxs-lookup"><span data-stu-id="fce59-156">-resource resourcefile.txt</span></span>|<span data-ttu-id="fce59-157">Fichier. txt contenant les ressources d’aide et de bannière pour l’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="fce59-157">The .txt file containing help and banner resources for the shell.</span></span> <span data-ttu-id="fce59-158">La première ressource est nommée ShellHelp et contient le texte affiché si l’interpréteur de commandes est appelé avec le paramètre `help`.</span><span class="sxs-lookup"><span data-stu-id="fce59-158">The first resource is named ShellHelp, and contains the text displayed if the shell is invoked with the `help` parameter.</span></span> <span data-ttu-id="fce59-159">La deuxième ressource est nommée ShellBanner et contient le texte et les informations de copyright affichés lorsque l’interpréteur de commandes est lancé en mode interactif.</span><span class="sxs-lookup"><span data-stu-id="fce59-159">The second resource is named ShellBanner, and it contains the text and copyright information displayed when the shell is launched in interactive mode.</span></span><br /><br /> <span data-ttu-id="fce59-160">Si ce paramètre n’est pas fourni, ou si ces ressources ne sont pas présentes, une aide et une bannière génériques sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="fce59-160">If this parameter is not provided, or these resources are not present, then a generic help and banner are used.</span></span>|
|<span data-ttu-id="fce59-161">-cscflags cscFlags</span><span class="sxs-lookup"><span data-stu-id="fce59-161">-cscflags cscFlags</span></span>|<span data-ttu-id="fce59-162">Indicateurs qui doivent être passés au C# compilateur (CSC. exe).</span><span class="sxs-lookup"><span data-stu-id="fce59-162">Flags that should be passed to the C# compiler (csc.exe).</span></span> <span data-ttu-id="fce59-163">Celles-ci sont transmises sans modification.</span><span class="sxs-lookup"><span data-stu-id="fce59-163">These are passed through unchanged.</span></span> <span data-ttu-id="fce59-164">Si ce paramètre comprend des espaces, il doit être placé entre guillemets doubles.</span><span class="sxs-lookup"><span data-stu-id="fce59-164">If this parameter includes spaces, it should be surrounded in double-quotes.</span></span>|
|<span data-ttu-id="fce59-165">-?</span><span class="sxs-lookup"><span data-stu-id="fce59-165">-?</span></span><br /><br /> <span data-ttu-id="fce59-166">-aide</span><span class="sxs-lookup"><span data-stu-id="fce59-166">-help</span></span>|<span data-ttu-id="fce59-167">Affiche les options de ligne de commande message de copyright et make-shell.</span><span class="sxs-lookup"><span data-stu-id="fce59-167">Displays the copyright message and Make-Shell command line options.</span></span>|
|<span data-ttu-id="fce59-168">-verbose</span><span class="sxs-lookup"><span data-stu-id="fce59-168">-verbose</span></span>|<span data-ttu-id="fce59-169">Affiche des informations détaillées pendant la création de l’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="fce59-169">Displays detailed information while the shell is being created.</span></span>|

## <a name="see-also"></a><span data-ttu-id="fce59-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fce59-170">See Also</span></span>

[<span data-ttu-id="fce59-171">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fce59-171">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="fce59-172">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="fce59-172">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)