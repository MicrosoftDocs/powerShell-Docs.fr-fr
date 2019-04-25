---
title: Le nom d’un fichier CAB d’aide actualisable | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: 0b58d5ee19a85bed26bc6549ced48b890cd62f64
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082360"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="5272e-102">Guide pratique pour nommer un fichier CAB d’aide actualisable</span><span class="sxs-lookup"><span data-stu-id="5272e-102">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="5272e-103">Cette rubrique explique le format de nom requis pour le fichier CAB de l’aide actualisable (. Fichiers CAB).</span><span class="sxs-lookup"><span data-stu-id="5272e-103">This topic explains the required name format for the Updatable Help cabinet (.CAB) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="5272e-104">Guide pratique pour nommer un fichier CAB d’aide actualisable</span><span class="sxs-lookup"><span data-stu-id="5272e-104">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="5272e-105">Fichier CAB actualisable (. Fichier CAB) doit avoir un nom au format suivant.</span><span class="sxs-lookup"><span data-stu-id="5272e-105">A Updatable cabinet (.CAB) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="5272e-106">Voici les éléments du nom.</span><span class="sxs-lookup"><span data-stu-id="5272e-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="5272e-107">ModuleName la valeur de la **nom** propriété de la **ModuleInfo** de l’objet qui le [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) applet de commande renvoie.</span><span class="sxs-lookup"><span data-stu-id="5272e-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="5272e-108">ModuleGUID la valeur de la **GUID** clés dans le manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="5272e-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="5272e-109">Culture UICulture l’interface utilisateur des fichiers d’aide dans le fichier CAB.</span><span class="sxs-lookup"><span data-stu-id="5272e-109">UICulture The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="5272e-110">Cette valeur doit correspondre à la valeur de l’un de le **UICulture** éléments dans le fichier XML HelpInfo du module.</span><span class="sxs-lookup"><span data-stu-id="5272e-110">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="5272e-111">Par exemple, si le nom du module est « TestModule », le GUID du module est 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 et la culture d’interface utilisateur est « en-US », le nom du fichier CAB serait :</span><span class="sxs-lookup"><span data-stu-id="5272e-111">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`