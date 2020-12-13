---
ms.date: 09/12/2016
ms.topic: reference
title: Nommage des fichiers d’aide
description: Nommage des fichiers d’aide
ms.openlocfilehash: b77af8f9b9510785a4198fed9da1263184a27b99
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667587"
---
# <a name="naming-help-files"></a><span data-ttu-id="e3b19-103">Nommage des fichiers d’aide</span><span class="sxs-lookup"><span data-stu-id="e3b19-103">Naming Help Files</span></span>

<span data-ttu-id="e3b19-104">Cette rubrique explique comment nommer un fichier d’aide XML pour que l’applet [de commande d’obtention d’aide](/powershell/module/Microsoft.PowerShell.Core/Get-Help) puisse le trouver.</span><span class="sxs-lookup"><span data-stu-id="e3b19-104">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="e3b19-105">Les spécifications de noms diffèrent pour chaque type de commande.</span><span class="sxs-lookup"><span data-stu-id="e3b19-105">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="e3b19-106">Fichiers d’aide sur les applets de commande</span><span class="sxs-lookup"><span data-stu-id="e3b19-106">Cmdlet Help Files</span></span>

<span data-ttu-id="e3b19-107">Le fichier d’aide d’une applet de commande C# doit être nommé pour l’assembly dans lequel l’applet de commande est définie.</span><span class="sxs-lookup"><span data-stu-id="e3b19-107">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="e3b19-108">Utilisez le format de nom de fichier suivant :</span><span class="sxs-lookup"><span data-stu-id="e3b19-108">Use the following filename format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="e3b19-109">Le format du nom de l’assembly est requis même lorsque l’assembly est un module imbriqué.</span><span class="sxs-lookup"><span data-stu-id="e3b19-109">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="e3b19-110">Par exemple, l’applet de commande [WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) est définie dans l’assembly Microsoft.PowerShell.Diagnostics.dll.</span><span class="sxs-lookup"><span data-stu-id="e3b19-110">For example, the [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="e3b19-111">L' `Get-Help` applet de commande recherche une rubrique d’aide pour l’applet de commande `Get-WinEvent` uniquement dans le `Microsoft.PowerShell.Diagnostics.dll-help.xml` fichier du répertoire du module.</span><span class="sxs-lookup"><span data-stu-id="e3b19-111">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the `Microsoft.PowerShell.Diagnostics.dll-help.xml` file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="e3b19-112">Fichiers d’aide du fournisseur</span><span class="sxs-lookup"><span data-stu-id="e3b19-112">Provider Help files</span></span>

<span data-ttu-id="e3b19-113">Le fichier d’aide d’un fournisseur PowerShell doit être nommé pour l’assembly dans lequel le fournisseur est défini.</span><span class="sxs-lookup"><span data-stu-id="e3b19-113">The help file for a PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="e3b19-114">Utilisez le format de nom de fichier suivant :</span><span class="sxs-lookup"><span data-stu-id="e3b19-114">Use the following filename format:</span></span>

`<AssemblyName>.dll-help.xml`

<span data-ttu-id="e3b19-115">Le format du nom de l’assembly est requis même lorsque l’assembly est un module imbriqué.</span><span class="sxs-lookup"><span data-stu-id="e3b19-115">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="e3b19-116">Par exemple, le fournisseur de certificats est défini dans l' `Microsoft.PowerShell.Security.dll` assembly.</span><span class="sxs-lookup"><span data-stu-id="e3b19-116">For example, the Certificate provider is defined in the `Microsoft.PowerShell.Security.dll` assembly.</span></span> <span data-ttu-id="e3b19-117">L' `Get-Help` applet de commande recherche une rubrique d’aide pour le fournisseur de certificats uniquement dans le `Microsoft.PowerShell.Security.dll-help.xml` fichier du répertoire du module.</span><span class="sxs-lookup"><span data-stu-id="e3b19-117">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the `Microsoft.PowerShell.Security.dll-help.xml` file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="e3b19-118">Fichiers d’aide de fonction</span><span class="sxs-lookup"><span data-stu-id="e3b19-118">Function Help Files</span></span>

<span data-ttu-id="e3b19-119">Les fonctions peuvent être documentées à l’aide d’une [aide basée sur des commentaires](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) ou documentées dans un fichier d’aide XML.</span><span class="sxs-lookup"><span data-stu-id="e3b19-119">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="e3b19-120">Lorsque la fonction est documentée dans un fichier XML, la fonction doit avoir un `.ExternalHelp` mot clé de commentaire qui associe la fonction au fichier XML.</span><span class="sxs-lookup"><span data-stu-id="e3b19-120">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="e3b19-121">Dans le cas contraire, l’applet de commande `Get-Help` ne peut pas trouver le fichier d’aide.</span><span class="sxs-lookup"><span data-stu-id="e3b19-121">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="e3b19-122">Il n’existe aucune exigence technique pour le nom d’un fichier d’aide de fonction.</span><span class="sxs-lookup"><span data-stu-id="e3b19-122">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="e3b19-123">Toutefois, il est recommandé de nommer le fichier d’aide pour le module de script dans lequel la fonction est définie.</span><span class="sxs-lookup"><span data-stu-id="e3b19-123">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="e3b19-124">Par exemple, la fonction suivante est définie dans le `MyModule.psm1` fichier.</span><span class="sxs-lookup"><span data-stu-id="e3b19-124">For example, the following function is defined in the `MyModule.psm1` file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="e3b19-125">Fichiers d’aide de commande CIM</span><span class="sxs-lookup"><span data-stu-id="e3b19-125">CIM Command Help Files</span></span>

<span data-ttu-id="e3b19-126">Le fichier d’aide pour une commande CIM doit être nommé pour le fichier CDXML dans lequel la commande CIM est définie.</span><span class="sxs-lookup"><span data-stu-id="e3b19-126">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="e3b19-127">Utilisez le format de nom de fichier suivant :</span><span class="sxs-lookup"><span data-stu-id="e3b19-127">Use the following filename format:</span></span>

`<FileName>.cdxml-help.xml`

<span data-ttu-id="e3b19-128">Les commandes CIM sont définies dans les fichiers CDXML qui peuvent être inclus dans les modules en tant que modules imbriqués.</span><span class="sxs-lookup"><span data-stu-id="e3b19-128">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="e3b19-129">Lorsque la commande CIM est importée dans la session en tant que fonction, PowerShell ajoute un `.ExternalHelp` mot clé de commentaire à la définition de fonction qui associe la fonction à un fichier d’aide XML nommé pour le fichier CDXML dans lequel la commande CIM est définie.</span><span class="sxs-lookup"><span data-stu-id="e3b19-129">When the CIM command is imported into the session as a function, PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="e3b19-130">Script des fichiers d’aide du flux de travail</span><span class="sxs-lookup"><span data-stu-id="e3b19-130">Script Workflow Help Files</span></span>

<span data-ttu-id="e3b19-131">Les workflows de script inclus dans les modules peuvent être documentés dans les fichiers d’aide XML.</span><span class="sxs-lookup"><span data-stu-id="e3b19-131">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="e3b19-132">Il n’existe aucune exigence technique pour le nom du fichier d’aide.</span><span class="sxs-lookup"><span data-stu-id="e3b19-132">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="e3b19-133">Toutefois, il est recommandé de nommer le fichier d’aide pour le module de script dans lequel le flux de travail de script est défini.</span><span class="sxs-lookup"><span data-stu-id="e3b19-133">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="e3b19-134">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e3b19-134">For example:</span></span>

`<ScriptModule>.psm1-help.xml`

<span data-ttu-id="e3b19-135">Contrairement à d’autres commandes scriptées, les flux de travail de script ne nécessitent pas `.ExternalHelp` de mot clé de commentaire pour les associer à un fichier d’aide.</span><span class="sxs-lookup"><span data-stu-id="e3b19-135">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="e3b19-136">Au lieu de cela, PowerShell recherche dans les sous-répertoires spécifiques à la culture de l’interface utilisateur du répertoire du module des fichiers d’aide basés sur XML et recherche de l’aide pour le workflow de script dans tous les fichiers.</span><span class="sxs-lookup"><span data-stu-id="e3b19-136">Instead, PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="e3b19-137">`.ExternalHelp` le mot clé de commentaire est ignoré.</span><span class="sxs-lookup"><span data-stu-id="e3b19-137">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="e3b19-138">Étant donné que le `.ExternalHelp` mot clé comment est ignoré, l' `Get-Help` applet de commande ne peut trouver de l’aide pour les workflows de script que lorsqu’ils sont inclus dans des modules.</span><span class="sxs-lookup"><span data-stu-id="e3b19-138">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>
