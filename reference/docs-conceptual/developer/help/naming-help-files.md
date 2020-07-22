---
title: Nommage des fichiers d’aide
ms.date: 09/12/2016
ms.openlocfilehash: ea95e6d6c87e553ed11fe6e3f058fc9a1b3d03f8
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893269"
---
# <a name="naming-help-files"></a><span data-ttu-id="7920e-102">Nommage des fichiers d’aide</span><span class="sxs-lookup"><span data-stu-id="7920e-102">Naming Help Files</span></span>

<span data-ttu-id="7920e-103">Cette rubrique explique comment nommer un fichier d’aide XML pour que l’applet [de commande d’obtention d’aide](/powershell/module/Microsoft.PowerShell.Core/Get-Help) puisse le trouver.</span><span class="sxs-lookup"><span data-stu-id="7920e-103">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="7920e-104">Les spécifications de noms diffèrent pour chaque type de commande.</span><span class="sxs-lookup"><span data-stu-id="7920e-104">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="7920e-105">Fichiers d’aide sur les applets de commande</span><span class="sxs-lookup"><span data-stu-id="7920e-105">Cmdlet Help Files</span></span>

<span data-ttu-id="7920e-106">Le fichier d’aide d’une applet de commande C# doit être nommé pour l’assembly dans lequel l’applet de commande est définie.</span><span class="sxs-lookup"><span data-stu-id="7920e-106">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="7920e-107">Utilisez le format de nom de fichier suivant :</span><span class="sxs-lookup"><span data-stu-id="7920e-107">Use the following filename format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="7920e-108">Le format du nom de l’assembly est requis même lorsque l’assembly est un module imbriqué.</span><span class="sxs-lookup"><span data-stu-id="7920e-108">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="7920e-109">Par exemple, l’applet de commande [WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) est définie dans l’assembly Microsoft.PowerShell.Diagnostics.dll.</span><span class="sxs-lookup"><span data-stu-id="7920e-109">For example, the [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="7920e-110">L' `Get-Help` applet de commande recherche une rubrique d’aide pour l’applet de commande `Get-WinEvent` uniquement dans le `Microsoft.PowerShell.Diagnostics.dll-help.xml` fichier du répertoire du module.</span><span class="sxs-lookup"><span data-stu-id="7920e-110">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the `Microsoft.PowerShell.Diagnostics.dll-help.xml` file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="7920e-111">Fichiers d’aide du fournisseur</span><span class="sxs-lookup"><span data-stu-id="7920e-111">Provider Help files</span></span>

<span data-ttu-id="7920e-112">Le fichier d’aide d’un fournisseur PowerShell doit être nommé pour l’assembly dans lequel le fournisseur est défini.</span><span class="sxs-lookup"><span data-stu-id="7920e-112">The help file for a PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="7920e-113">Utilisez le format de nom de fichier suivant :</span><span class="sxs-lookup"><span data-stu-id="7920e-113">Use the following filename format:</span></span>

`<AssemblyName>.dll-help.xml`

<span data-ttu-id="7920e-114">Le format du nom de l’assembly est requis même lorsque l’assembly est un module imbriqué.</span><span class="sxs-lookup"><span data-stu-id="7920e-114">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="7920e-115">Par exemple, le fournisseur de certificats est défini dans l' `Microsoft.PowerShell.Security.dll` assembly.</span><span class="sxs-lookup"><span data-stu-id="7920e-115">For example, the Certificate provider is defined in the `Microsoft.PowerShell.Security.dll` assembly.</span></span> <span data-ttu-id="7920e-116">L' `Get-Help` applet de commande recherche une rubrique d’aide pour le fournisseur de certificats uniquement dans le `Microsoft.PowerShell.Security.dll-help.xml` fichier du répertoire du module.</span><span class="sxs-lookup"><span data-stu-id="7920e-116">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the `Microsoft.PowerShell.Security.dll-help.xml` file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="7920e-117">Fichiers d’aide de fonction</span><span class="sxs-lookup"><span data-stu-id="7920e-117">Function Help Files</span></span>

<span data-ttu-id="7920e-118">Les fonctions peuvent être documentées à l’aide d’une [aide basée sur des commentaires](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) ou documentées dans un fichier d’aide XML.</span><span class="sxs-lookup"><span data-stu-id="7920e-118">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="7920e-119">Lorsque la fonction est documentée dans un fichier XML, la fonction doit avoir un `.ExternalHelp` mot clé de commentaire qui associe la fonction au fichier XML.</span><span class="sxs-lookup"><span data-stu-id="7920e-119">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="7920e-120">Dans le cas contraire, l’applet de commande `Get-Help` ne peut pas trouver le fichier d’aide.</span><span class="sxs-lookup"><span data-stu-id="7920e-120">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="7920e-121">Il n’existe aucune exigence technique pour le nom d’un fichier d’aide de fonction.</span><span class="sxs-lookup"><span data-stu-id="7920e-121">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="7920e-122">Toutefois, il est recommandé de nommer le fichier d’aide pour le module de script dans lequel la fonction est définie.</span><span class="sxs-lookup"><span data-stu-id="7920e-122">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="7920e-123">Par exemple, la fonction suivante est définie dans le `MyModule.psm1` fichier.</span><span class="sxs-lookup"><span data-stu-id="7920e-123">For example, the following function is defined in the `MyModule.psm1` file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="7920e-124">Fichiers d’aide de commande CIM</span><span class="sxs-lookup"><span data-stu-id="7920e-124">CIM Command Help Files</span></span>

<span data-ttu-id="7920e-125">Le fichier d’aide pour une commande CIM doit être nommé pour le fichier CDXML dans lequel la commande CIM est définie.</span><span class="sxs-lookup"><span data-stu-id="7920e-125">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="7920e-126">Utilisez le format de nom de fichier suivant :</span><span class="sxs-lookup"><span data-stu-id="7920e-126">Use the following filename format:</span></span>

`<FileName>.cdxml-help.xml`

<span data-ttu-id="7920e-127">Les commandes CIM sont définies dans les fichiers CDXML qui peuvent être inclus dans les modules en tant que modules imbriqués.</span><span class="sxs-lookup"><span data-stu-id="7920e-127">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="7920e-128">Lorsque la commande CIM est importée dans la session en tant que fonction, PowerShell ajoute un `.ExternalHelp` mot clé de commentaire à la définition de fonction qui associe la fonction à un fichier d’aide XML nommé pour le fichier CDXML dans lequel la commande CIM est définie.</span><span class="sxs-lookup"><span data-stu-id="7920e-128">When the CIM command is imported into the session as a function, PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="7920e-129">Script des fichiers d’aide du flux de travail</span><span class="sxs-lookup"><span data-stu-id="7920e-129">Script Workflow Help Files</span></span>

<span data-ttu-id="7920e-130">Les workflows de script inclus dans les modules peuvent être documentés dans les fichiers d’aide XML.</span><span class="sxs-lookup"><span data-stu-id="7920e-130">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="7920e-131">Il n’existe aucune exigence technique pour le nom du fichier d’aide.</span><span class="sxs-lookup"><span data-stu-id="7920e-131">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="7920e-132">Toutefois, il est recommandé de nommer le fichier d’aide pour le module de script dans lequel le flux de travail de script est défini.</span><span class="sxs-lookup"><span data-stu-id="7920e-132">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="7920e-133">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="7920e-133">For example:</span></span>

`<ScriptModule>.psm1-help.xml`

<span data-ttu-id="7920e-134">Contrairement à d’autres commandes scriptées, les flux de travail de script ne nécessitent pas `.ExternalHelp` de mot clé de commentaire pour les associer à un fichier d’aide.</span><span class="sxs-lookup"><span data-stu-id="7920e-134">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="7920e-135">Au lieu de cela, PowerShell recherche dans les sous-répertoires spécifiques à la culture de l’interface utilisateur du répertoire du module des fichiers d’aide basés sur XML et recherche de l’aide pour le workflow de script dans tous les fichiers.</span><span class="sxs-lookup"><span data-stu-id="7920e-135">Instead, PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="7920e-136">`.ExternalHelp`le mot clé de commentaire est ignoré.</span><span class="sxs-lookup"><span data-stu-id="7920e-136">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="7920e-137">Étant donné que le `.ExternalHelp` mot clé comment est ignoré, l' `Get-Help` applet de commande ne peut trouver de l’aide pour les workflows de script que lorsqu’ils sont inclus dans des modules.</span><span class="sxs-lookup"><span data-stu-id="7920e-137">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>
