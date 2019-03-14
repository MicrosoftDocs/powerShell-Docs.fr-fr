---
title: Le nom d’un fichier XML HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: 462cd7bd486a5924bb2bc43e0ac8d1558e30e657
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794805"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="b7d98-102">Guide pratique pour nommer un fichier XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="b7d98-102">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="b7d98-103">Cette rubrique explique le format de nom requis pour les fichiers d’informations d’aide actualisable, communément appelé fichiers HelpInfo XML.</span><span class="sxs-lookup"><span data-stu-id="b7d98-103">This topic explains the required name format for the Updatable Help Information files, commonly known as HelpInfo XML files.</span></span>

## <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="b7d98-104">Guide pratique pour nommer un fichier XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="b7d98-104">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="b7d98-105">Un fichier XML HelpInfo doit avoir un nom au format suivant.</span><span class="sxs-lookup"><span data-stu-id="b7d98-105">A HelpInfo XML file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

<span data-ttu-id="b7d98-106">Voici les éléments du nom.</span><span class="sxs-lookup"><span data-stu-id="b7d98-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="b7d98-107">ModuleName la valeur de la **nom** propriété de la **ModuleInfo** de l’objet qui le [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) applet de commande renvoie.</span><span class="sxs-lookup"><span data-stu-id="b7d98-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="b7d98-108">ModuleGUID la valeur de la **GUID** clés dans le manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="b7d98-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="b7d98-109">Par exemple, si le nom du module est « TestModule » et le GUID du module est bfc1bebf07f9 du a46b 4914 9cabb9ad f2ac, le nom du fichier XML HelpInfo du module serait :</span><span class="sxs-lookup"><span data-stu-id="b7d98-109">For example, if the module name is "TestModule" and the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, the name of the HelpInfo XML file for the module would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`