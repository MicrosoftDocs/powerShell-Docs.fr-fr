---
title: Modules et composants logiciel enfichables | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: 157cd64e286392f3fd770e1e34542682b1e63625
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067618"
---
# <a name="modules-and-snap-ins"></a><span data-ttu-id="32d41-102">Modules et composants logiciels enfichables</span><span class="sxs-lookup"><span data-stu-id="32d41-102">Modules and Snap-ins</span></span>

<span data-ttu-id="32d41-103">Applets de commande peuvent être ajoutés à une session à l’aide de modules (introduites par Windows PowerShell 2.0) ou des composants logiciel enfichables. Une fois que l’applet de commande est ajoutée à la session, qu'il peut être exécuté par programme par une application hôte ou de manière interactive en ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="32d41-103">Cmdlets can be added to a session using modules (introduced by Windows PowerShell 2.0) or snap-ins. Once the cmdlet is added to the session it can be run programmatically by a host application or interactively at the command line.</span></span>

<span data-ttu-id="32d41-104">Nous vous recommandons d’utiliser les modules en tant que la méthode de remise pour l’ajout d’applets de commande à une session pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="32d41-104">We recommend that you use modules as the delivery method for adding cmdlets to a session for the following reasons:</span></span>

- <span data-ttu-id="32d41-105">Modules permettent d’ajouter des applets de commande en chargeant l’assembly dans lequel l’applet de commande est défini.</span><span class="sxs-lookup"><span data-stu-id="32d41-105">Modules allow you to add cmdlets by loading the assembly where the cmdlet is defined.</span></span> <span data-ttu-id="32d41-106">Il est inutile d’implémenter une classe snap-in.</span><span class="sxs-lookup"><span data-stu-id="32d41-106">There is no need to implement a snap-in class.</span></span>

- <span data-ttu-id="32d41-107">Modules permettent d’ajouter d’autres ressources, telles que les variables, fonctions, scripts, types et mise en forme les fichiers et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="32d41-107">Modules allow you to add other resources, such as variables, functions, scripts, types and formatting files, and more.</span></span>

- <span data-ttu-id="32d41-108">Composants logiciel enfichables peuvent être utilisés uniquement pour ajouter des fournisseurs et applets de commande à la session.</span><span class="sxs-lookup"><span data-stu-id="32d41-108">Snap-ins can be used only to add cmdlets and providers to the session.</span></span>

## <a name="see-also"></a><span data-ttu-id="32d41-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32d41-109">See Also</span></span>

[<span data-ttu-id="32d41-110">Écrire un Module PowerShell de Windows</span><span class="sxs-lookup"><span data-stu-id="32d41-110">Writing a Windows PowerShell Module</span></span>](../module/writing-a-windows-powershell-module.md)

[<span data-ttu-id="32d41-111">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="32d41-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
