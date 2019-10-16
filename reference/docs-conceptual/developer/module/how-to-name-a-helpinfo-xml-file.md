---
title: Comment nommer un fichier XML HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: 462cd7bd486a5924bb2bc43e0ac8d1558e30e657
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367198"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="f757e-102">Guide pratique pour nommer un fichier XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="f757e-102">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="f757e-103">Cette rubrique décrit le format de nom requis pour les fichiers d’informations d’aide pouvant être mis à jour, communément appelés fichiers XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="f757e-103">This topic explains the required name format for the Updatable Help Information files, commonly known as HelpInfo XML files.</span></span>

## <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="f757e-104">Guide pratique pour nommer un fichier XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="f757e-104">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="f757e-105">Un fichier XML HelpInfo doit avoir un nom au format suivant.</span><span class="sxs-lookup"><span data-stu-id="f757e-105">A HelpInfo XML file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

<span data-ttu-id="f757e-106">Les éléments du nom sont les suivants.</span><span class="sxs-lookup"><span data-stu-id="f757e-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="f757e-107">ModuleName la valeur de la propriété **Name** de l’objet **ModuleInfo** [retourné par l’applet de](/powershell/module/Microsoft.PowerShell.Core/Get-Module) commande.</span><span class="sxs-lookup"><span data-stu-id="f757e-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="f757e-108">ModuleGUID la valeur de la clé **GUID** dans le manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="f757e-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="f757e-109">Par exemple, si le nom du module est « TestModule » et que le GUID du module est 9cabb9ad-f2ac-4914-A46B-bfc1bebf07f9, le nom du fichier XML HelpInfo du module serait :</span><span class="sxs-lookup"><span data-stu-id="f757e-109">For example, if the module name is "TestModule" and the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, the name of the HelpInfo XML file for the module would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`