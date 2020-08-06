---
title: Modules et composants logiciels enfichables | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 07cdc55fd6d1462130f1a81deb30056623a525e6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787306"
---
# <a name="modules-and-snap-ins"></a><span data-ttu-id="c324a-102">Modules et composants logiciels enfichables</span><span class="sxs-lookup"><span data-stu-id="c324a-102">Modules and Snap-ins</span></span>

<span data-ttu-id="c324a-103">Des applets de commande peuvent être ajoutées à une session à l’aide de modules (introduits par Windows PowerShell 2,0) ou de composants logiciels enfichables. Une fois l’applet de commande ajoutée à la session, elle peut être exécutée par programme par une application hôte ou de manière interactive à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="c324a-103">Cmdlets can be added to a session using modules (introduced by Windows PowerShell 2.0) or snap-ins. Once the cmdlet is added to the session it can be run programmatically by a host application or interactively at the command line.</span></span>

<span data-ttu-id="c324a-104">Nous vous recommandons d’utiliser les modules comme méthode de remise pour ajouter des applets de commande à une session pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="c324a-104">We recommend that you use modules as the delivery method for adding cmdlets to a session for the following reasons:</span></span>

- <span data-ttu-id="c324a-105">Les modules vous permettent d’ajouter des applets de commande en chargeant l’assembly dans lequel l’applet de commande est définie.</span><span class="sxs-lookup"><span data-stu-id="c324a-105">Modules allow you to add cmdlets by loading the assembly where the cmdlet is defined.</span></span> <span data-ttu-id="c324a-106">Il n’est pas nécessaire d’implémenter une classe de composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="c324a-106">There is no need to implement a snap-in class.</span></span>

- <span data-ttu-id="c324a-107">Les modules vous permettent d’ajouter d’autres ressources, telles que des variables, des fonctions, des scripts, des types et des fichiers de mise en forme, et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="c324a-107">Modules allow you to add other resources, such as variables, functions, scripts, types and formatting files, and more.</span></span>

- <span data-ttu-id="c324a-108">Les composants logiciels enfichables ne peuvent être utilisés que pour ajouter des applets de commande et des fournisseurs à la session.</span><span class="sxs-lookup"><span data-stu-id="c324a-108">Snap-ins can be used only to add cmdlets and providers to the session.</span></span>

## <a name="see-also"></a><span data-ttu-id="c324a-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c324a-109">See Also</span></span>

[<span data-ttu-id="c324a-110">Écriture d’un module Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c324a-110">Writing a Windows PowerShell Module</span></span>](writing-a-windows-powershell-module.md)

[<span data-ttu-id="c324a-111">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c324a-111">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/cmdlet-overview.md)
