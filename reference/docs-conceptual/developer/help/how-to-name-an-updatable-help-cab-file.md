---
title: Comment nommer un fichier CAB d’aide actualisable | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: a253f98d213f797a659affb1560907bb99a045d3
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811698"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="25b18-102">Guide pratique pour nommer un fichier CAB d’aide actualisable</span><span class="sxs-lookup"><span data-stu-id="25b18-102">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="25b18-103">Cette rubrique explique le format de nom requis pour le fichier cab d’aide pouvant être mis à jour (. CAB).</span><span class="sxs-lookup"><span data-stu-id="25b18-103">This topic explains the required name format for the Updatable Help cabinet (.CAB) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="25b18-104">Guide pratique pour nommer un fichier CAB d’aide actualisable</span><span class="sxs-lookup"><span data-stu-id="25b18-104">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="25b18-105">Un fichier CAB pouvant être mis à jour (. CAB) doit avoir un nom au format suivant.</span><span class="sxs-lookup"><span data-stu-id="25b18-105">A Updatable cabinet (.CAB) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="25b18-106">Les éléments du nom sont les suivants.</span><span class="sxs-lookup"><span data-stu-id="25b18-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="25b18-107">ModuleName la valeur de la propriété **Name** de l’objet **ModuleInfo** [retourné par l’applet de](/powershell/module/Microsoft.PowerShell.Core/Get-Module) commande.</span><span class="sxs-lookup"><span data-stu-id="25b18-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="25b18-108">ModuleGUID la valeur de la clé **GUID** dans le manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="25b18-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="25b18-109">UICulture la culture d’interface utilisateur des fichiers d’aide dans le fichier CAB.</span><span class="sxs-lookup"><span data-stu-id="25b18-109">UICulture The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="25b18-110">Cette valeur doit correspondre à la valeur de l’un des éléments **UICulture** dans le fichier XML HelpInfo du module.</span><span class="sxs-lookup"><span data-stu-id="25b18-110">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="25b18-111">Par exemple, si le nom du module est « TestModule », le GUID du module est 9cabb9ad-f2ac-4914-A46B-bfc1bebf07f9, et la culture de l’interface utilisateur est « en-US », le nom du fichier CAB est le suivant :</span><span class="sxs-lookup"><span data-stu-id="25b18-111">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`
