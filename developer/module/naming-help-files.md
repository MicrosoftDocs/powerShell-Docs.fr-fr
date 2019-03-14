---
title: Nommage des fichiers d’aide | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: f65a90023df88fceafae1d1875ddf46b9088e2b8
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795349"
---
# <a name="naming-help-files"></a><span data-ttu-id="7f45f-102">Nommage des fichiers d’aide</span><span class="sxs-lookup"><span data-stu-id="7f45f-102">Naming Help Files</span></span>

<span data-ttu-id="7f45f-103">Cette rubrique explique comment nommer un fichier d’aide basé sur XML afin que le [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet peut le trouver.</span><span class="sxs-lookup"><span data-stu-id="7f45f-103">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="7f45f-104">Les exigences relatives aux noms diffèrent pour chaque type de commande.</span><span class="sxs-lookup"><span data-stu-id="7f45f-104">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="7f45f-105">Fichiers d’aide de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="7f45f-105">Cmdlet Help Files</span></span>

<span data-ttu-id="7f45f-106">Le fichier d’aide pour un C# applet de commande doit être nommé pour l’assembly dans lequel l’applet de commande est défini.</span><span class="sxs-lookup"><span data-stu-id="7f45f-106">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="7f45f-107">Utilisez le format de nom de fichier suivant :</span><span class="sxs-lookup"><span data-stu-id="7f45f-107">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="7f45f-108">Le format de nom d’assembly est requis, même lorsque l’assembly est un module imbriqué.</span><span class="sxs-lookup"><span data-stu-id="7f45f-108">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="7f45f-109">Par exemple, le [Get-WinEvent ; PSITPro5_Diagnostic ; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) applet de commande est défini dans l’assembly Microsoft.PowerShell.Diagnostics.dll.</span><span class="sxs-lookup"><span data-stu-id="7f45f-109">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="7f45f-110">Le `Get-Help` applet de commande recherche d’une rubrique d’aide pour le `Get-WinEvent` applet de commande uniquement dans le fichier Microsoft.PowerShell.Diagnostics.dll-help.xml dans le répertoire de module.</span><span class="sxs-lookup"><span data-stu-id="7f45f-110">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="7f45f-111">Fichiers d’aide du fournisseur</span><span class="sxs-lookup"><span data-stu-id="7f45f-111">Provider Help files</span></span>

<span data-ttu-id="7f45f-112">Le fichier d’aide pour un fournisseur Windows PowerShell doit être nommé pour l’assembly dans lequel le fournisseur est défini.</span><span class="sxs-lookup"><span data-stu-id="7f45f-112">The help file for a Windows PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="7f45f-113">Utilisez le format de nom de fichier suivant :</span><span class="sxs-lookup"><span data-stu-id="7f45f-113">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="7f45f-114">Le format de nom d’assembly est requis, même lorsque l’assembly est un module imbriqué.</span><span class="sxs-lookup"><span data-stu-id="7f45f-114">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="7f45f-115">Par exemple, le fournisseur de certificats est défini dans l’assembly Microsoft.PowerShell.Security.dll.</span><span class="sxs-lookup"><span data-stu-id="7f45f-115">For example, the Certificate provider is defined in the Microsoft.PowerShell.Security.dll assembly.</span></span> <span data-ttu-id="7f45f-116">Le `Get-Help` applet de commande recherche une rubrique d’aide pour le fournisseur de certificats uniquement dans le fichier Microsoft.PowerShell.Security.dll-help.xml dans le répertoire de module.</span><span class="sxs-lookup"><span data-stu-id="7f45f-116">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the Microsoft.PowerShell.Security.dll-help.xml file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="7f45f-117">Fichiers d’aide (fonction)</span><span class="sxs-lookup"><span data-stu-id="7f45f-117">Function Help Files</span></span>

<span data-ttu-id="7f45f-118">Fonctions peuvent être décrites à l’aide de [aide basée sur le commentaire](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) ou documentés dans un fichier d’aide XML.</span><span class="sxs-lookup"><span data-stu-id="7f45f-118">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="7f45f-119">Lorsque la fonction est documentée dans un fichier XML, la fonction doit avoir un `.ExternalHelp` commenter le mot clé qui associe la fonction avec le fichier XML.</span><span class="sxs-lookup"><span data-stu-id="7f45f-119">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="7f45f-120">Sinon, le `Get-Help` applet de commande ne peut pas trouver le fichier d’aide.</span><span class="sxs-lookup"><span data-stu-id="7f45f-120">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="7f45f-121">Il n’existe aucune exigence technique pour le nom d’un fichier d’aide (fonction).</span><span class="sxs-lookup"><span data-stu-id="7f45f-121">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="7f45f-122">Toutefois, une bonne pratique consiste à nommer le fichier d’aide pour le module de script dans lequel la fonction est définie.</span><span class="sxs-lookup"><span data-stu-id="7f45f-122">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="7f45f-123">Par exemple, la fonction suivante est définie dans le fichier MyModule.psm1.</span><span class="sxs-lookup"><span data-stu-id="7f45f-123">For example, the following function is defined in the MyModule.psm1 file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="7f45f-124">Fichiers d’aide commande CIM</span><span class="sxs-lookup"><span data-stu-id="7f45f-124">CIM Command Help Files</span></span>

<span data-ttu-id="7f45f-125">Le fichier d’aide pour une commande CIM doit être nommé pour le fichier CDXML dans lequel la commande CIM est définie.</span><span class="sxs-lookup"><span data-stu-id="7f45f-125">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="7f45f-126">Utilisez le format de nom de fichier suivant :</span><span class="sxs-lookup"><span data-stu-id="7f45f-126">Use the following file name format:</span></span>

```
<FileName>.cdxml-help.xml
```

<span data-ttu-id="7f45f-127">Commandes CIM sont définies dans les fichiers CDXML qui peuvent être inclus dans les modules en tant que modules imbriqués.</span><span class="sxs-lookup"><span data-stu-id="7f45f-127">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="7f45f-128">Lorsque la commande CIM est importée dans la session en tant que fonction, Windows PowerShell ajoute un `.ExternalHelp` commentaire mot clé pour la définition de fonction qui associe la fonction avec un aide XML du fichier qui est nommé pour le fichier CDXML dans lequel la commande CIM est définie.</span><span class="sxs-lookup"><span data-stu-id="7f45f-128">When the CIM command is imported into the session as a function, Windows PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="7f45f-129">Fichiers d’aide de flux de travail de script</span><span class="sxs-lookup"><span data-stu-id="7f45f-129">Script Workflow Help Files</span></span>

<span data-ttu-id="7f45f-130">Workflows de script qui sont inclus dans les modules peuvent être documentées dans les fichiers d’aide basé sur XML.</span><span class="sxs-lookup"><span data-stu-id="7f45f-130">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="7f45f-131">Il n’existe aucune exigence technique pour le nom du fichier d’aide.</span><span class="sxs-lookup"><span data-stu-id="7f45f-131">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="7f45f-132">Toutefois, une bonne pratique consiste à nommer le fichier d’aide pour le module de script dans lequel le workflow de script est défini.</span><span class="sxs-lookup"><span data-stu-id="7f45f-132">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="7f45f-133">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="7f45f-133">For example:</span></span>

```
<ScriptModule>.psm1-help.xml
```

<span data-ttu-id="7f45f-134">Contrairement à d’autres commandes de l’aide de scripts, les workflows de script ne nécessitent pas une `.ExternalHelp` commenter le mot clé pour les associer à un fichier d’aide.</span><span class="sxs-lookup"><span data-stu-id="7f45f-134">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="7f45f-135">Au lieu de cela, Windows PowerShell recherche dans les sous-répertoires spécifiques de Culture de l’interface utilisateur du répertoire du module pour les fichiers d’aide basé sur XML et recherche de l’aide pour le workflow de script dans tous les fichiers.</span><span class="sxs-lookup"><span data-stu-id="7f45f-135">Instead, Windows PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="7f45f-136">`.ExternalHelp` mot clé de commentaire sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="7f45f-136">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="7f45f-137">Étant donné que le `.ExternalHelp` mot clé de commentaire est ignoré, le `Get-Help` applet de commande permettre trouver de l’aide pour les workflows de script uniquement lorsqu’ils sont inclus dans les modules.</span><span class="sxs-lookup"><span data-stu-id="7f45f-137">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>