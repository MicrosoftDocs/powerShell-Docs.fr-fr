---
title: Sortie de l’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1362f4cd-4e05-4ace-ade6-7128da8ad86c
caps.latest.revision: 10
ms.openlocfilehash: 4c6aacd49b0a87bca6806ba5f08a1b4d48a90959
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365938"
---
# <a name="cmdlet-output"></a><span data-ttu-id="93b39-102">Sortie des applets de commande</span><span class="sxs-lookup"><span data-stu-id="93b39-102">Cmdlet Output</span></span>

<span data-ttu-id="93b39-103">Cette section décrit les types de sortie des applets de commande et les méthodes que les applets de commande peuvent appeler pour générer une sortie telle que des messages d’erreur et des objets.</span><span class="sxs-lookup"><span data-stu-id="93b39-103">This section discusses the types of cmdlet output and the methods that cmdlets can call to generate output such as error messages and objects.</span></span> <span data-ttu-id="93b39-104">Cette section décrit également comment définir les types de .NET Framework retournés par vos applets de commande et comment ces objets sont affichés.</span><span class="sxs-lookup"><span data-stu-id="93b39-104">This section also describes how to define the .NET Framework types that are returned by your cmdlets and how those objects are displayed.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="93b39-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="93b39-105">In This Section</span></span>

<span data-ttu-id="93b39-106">[Types de sortie de l’applet de](./types-of-cmdlet-output.md) commande Décrit les types et la sortie que les applets de commande peuvent générer et les méthodes appelées par les applets de commande pour générer la sortie.</span><span class="sxs-lookup"><span data-stu-id="93b39-106">[Types of Cmdlet Output](./types-of-cmdlet-output.md) Describes the types and output that cmdlets can generate and the methods that cmdlets call to generate the output.</span></span>

<span data-ttu-id="93b39-107">[Rapport d’erreurs d’applet](./cmdlet-error-reporting.md) de commande Décrit le rapport d’erreurs d’applet de commande, un sous-ensemble de la sortie de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="93b39-107">[Cmdlet Error Reporting](./cmdlet-error-reporting.md) Discusses cmdlet error reporting, a subset of cmdlet output.</span></span>

<span data-ttu-id="93b39-108">[Extension d’objets de sortie](./extending-output-objects.md) Explique comment utiliser les fichiers de types (. ps1xml) pour étendre les objets .NET Framework retournés par des applets de commande, des fonctions et des scripts.</span><span class="sxs-lookup"><span data-stu-id="93b39-108">[Extending Output Objects](./extending-output-objects.md) Discusses how to use the types files (.ps1xml) to extend the .NET Framework objects that are returned by cmdlets, functions, and scripts.</span></span>

<span data-ttu-id="93b39-109">[Fichiers de mise en forme PowerShell](../format/powershell-formatting-files.md) Décrit les fichiers de mise en forme (. format. ps1xml) qui définissent l’affichage par défaut pour un ensemble spécifique d’objets .NET Framework dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="93b39-109">[PowerShell Formatting Files](../format/powershell-formatting-files.md) Describes the formatting files (.format.ps1xml) files that define the default display for a specific set of .NET Framework objects in Windows PowerShell.</span></span>

<span data-ttu-id="93b39-110">[Fichiers de mise en forme personnalisés](./custom-formatting-files.md) Décrit comment créer vos propres fichiers de mise en forme personnalisés pour remplacer les formats d’affichage par défaut ou pour définir l’affichage des objets retournés par vos propres commandes.</span><span class="sxs-lookup"><span data-stu-id="93b39-110">[Custom Formatting Files](./custom-formatting-files.md) Describes how to create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="93b39-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93b39-111">See Also</span></span>

[<span data-ttu-id="93b39-112">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="93b39-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
