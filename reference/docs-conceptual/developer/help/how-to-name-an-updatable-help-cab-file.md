---
ms.date: 09/12/2016
ms.topic: reference
title: Guide pratique pour nommer un fichier CAB d’aide actualisable
description: Guide pratique pour nommer un fichier CAB d’aide actualisable
ms.openlocfilehash: 57ea188d07a382d1a986a49c9ae22c5919dafa8e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658914"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="d9da5-103">Guide pratique pour nommer un fichier CAB d’aide actualisable</span><span class="sxs-lookup"><span data-stu-id="d9da5-103">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="d9da5-104">Cette rubrique explique le format de nom requis pour les fichiers CAB de l’aide actualisable ( `.CAB` ).</span><span class="sxs-lookup"><span data-stu-id="d9da5-104">This topic explains the required name format for the Updatable Help cabinet (`.CAB`) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="d9da5-105">Guide pratique pour nommer un fichier CAB d’aide actualisable</span><span class="sxs-lookup"><span data-stu-id="d9da5-105">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="d9da5-106">Un fichier cabinet () pouvant être mis `.CAB` à jour doit avoir un nom au format suivant.</span><span class="sxs-lookup"><span data-stu-id="d9da5-106">A Updatable cabinet (`.CAB`) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="d9da5-107">Les éléments du nom sont les suivants.</span><span class="sxs-lookup"><span data-stu-id="d9da5-107">The elements of the name are as follows.</span></span>

- <span data-ttu-id="d9da5-108">`<ModuleName>` -La valeur de la propriété **Name** de l’objet **ModuleInfo** retourné par l’applet de commande [« obten-module »](/powershell/module/Microsoft.PowerShell.Core/Get-Module) .</span><span class="sxs-lookup"><span data-stu-id="d9da5-108">`<ModuleName>` -The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>
- <span data-ttu-id="d9da5-109">`<ModuleGUID>` -La valeur de la clé **GUID** dans le manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="d9da5-109">`<ModuleGUID>` - The value of the **GUID** key in the module manifest.</span></span>
- <span data-ttu-id="d9da5-110">`<UICulture>` -La culture d’interface utilisateur des fichiers d’aide dans le fichier CAB.</span><span class="sxs-lookup"><span data-stu-id="d9da5-110">`<UICulture>` - The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="d9da5-111">Cette valeur doit correspondre à la valeur de l’un des éléments **UICulture** dans le fichier XML HelpInfo du module.</span><span class="sxs-lookup"><span data-stu-id="d9da5-111">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="d9da5-112">Par exemple, si le nom du module est « TestModule », le GUID du module est 9cabb9ad-f2ac-4914-A46B-bfc1bebf07f9, et la culture de l’interface utilisateur est « en-US », le nom du fichier CAB est le suivant :</span><span class="sxs-lookup"><span data-stu-id="d9da5-112">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`
