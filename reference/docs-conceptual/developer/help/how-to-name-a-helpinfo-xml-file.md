---
ms.date: 09/12/2016
ms.topic: reference
title: Guide pratique pour nommer un fichier XML HelpInfo
description: Guide pratique pour nommer un fichier XML HelpInfo
ms.openlocfilehash: 55bc2ef9530fc457e4d9ddf18e79e7226c991663
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659037"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="441ce-103">Guide pratique pour nommer un fichier XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="441ce-103">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="441ce-104">Cette rubrique décrit le format de nom requis pour les fichiers d’informations d’aide pouvant être mis à jour, communément appelés fichiers XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="441ce-104">This topic explains the required name format for the Updatable Help Information files, commonly known as HelpInfo XML files.</span></span>

## <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="441ce-105">Guide pratique pour nommer un fichier XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="441ce-105">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="441ce-106">Un fichier XML HelpInfo doit avoir un nom au format suivant.</span><span class="sxs-lookup"><span data-stu-id="441ce-106">A HelpInfo XML file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

<span data-ttu-id="441ce-107">Les éléments du nom sont les suivants.</span><span class="sxs-lookup"><span data-stu-id="441ce-107">The elements of the name are as follows.</span></span>

- <span data-ttu-id="441ce-108">`<ModuleName>` -La valeur de la propriété **Name** de l’objet **ModuleInfo** retourné par l’applet de commande [« obten-module »](/powershell/module/Microsoft.PowerShell.Core/Get-Module) .</span><span class="sxs-lookup"><span data-stu-id="441ce-108">`<ModuleName>` - The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

- <span data-ttu-id="441ce-109">`<ModuleGUID>` -La valeur de la clé **GUID** dans le manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="441ce-109">`<ModuleGUID>` - The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="441ce-110">Par exemple, si le nom du module est « TestModule » et que le GUID du module est 9cabb9ad-f2ac-4914-A46B-bfc1bebf07f9, le nom du fichier XML HelpInfo du module serait :</span><span class="sxs-lookup"><span data-stu-id="441ce-110">For example, if the module name is "TestModule" and the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, the name of the HelpInfo XML file for the module would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`
