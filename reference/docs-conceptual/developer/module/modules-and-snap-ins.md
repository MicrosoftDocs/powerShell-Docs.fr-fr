---
ms.date: 09/13/2016
ms.topic: reference
title: Modules et composants logiciels enfichables
description: Modules et composants logiciels enfichables
ms.openlocfilehash: de4ff1de9a29b78d7783fe7ed0265f5516db1fb4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658677"
---
# <a name="modules-and-snap-ins"></a><span data-ttu-id="435f4-103">Modules et composants logiciels enfichables</span><span class="sxs-lookup"><span data-stu-id="435f4-103">Modules and Snap-ins</span></span>

<span data-ttu-id="435f4-104">Des applets de commande peuvent être ajoutées à une session à l’aide de modules (introduits par Windows PowerShell 2,0) ou de composants logiciels enfichables. Une fois l’applet de commande ajoutée à la session, elle peut être exécutée par programme par une application hôte ou de manière interactive à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="435f4-104">Cmdlets can be added to a session using modules (introduced by Windows PowerShell 2.0) or snap-ins. Once the cmdlet is added to the session it can be run programmatically by a host application or interactively at the command line.</span></span>

<span data-ttu-id="435f4-105">Nous vous recommandons d’utiliser les modules comme méthode de remise pour ajouter des applets de commande à une session pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="435f4-105">We recommend that you use modules as the delivery method for adding cmdlets to a session for the following reasons:</span></span>

- <span data-ttu-id="435f4-106">Les modules vous permettent d’ajouter des applets de commande en chargeant l’assembly dans lequel l’applet de commande est définie.</span><span class="sxs-lookup"><span data-stu-id="435f4-106">Modules allow you to add cmdlets by loading the assembly where the cmdlet is defined.</span></span> <span data-ttu-id="435f4-107">Il n’est pas nécessaire d’implémenter une classe de composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="435f4-107">There is no need to implement a snap-in class.</span></span>

- <span data-ttu-id="435f4-108">Les modules vous permettent d’ajouter d’autres ressources, telles que des variables, des fonctions, des scripts, des types et des fichiers de mise en forme, et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="435f4-108">Modules allow you to add other resources, such as variables, functions, scripts, types and formatting files, and more.</span></span>

- <span data-ttu-id="435f4-109">Les composants logiciels enfichables ne peuvent être utilisés que pour ajouter des applets de commande et des fournisseurs à la session.</span><span class="sxs-lookup"><span data-stu-id="435f4-109">Snap-ins can be used only to add cmdlets and providers to the session.</span></span>

## <a name="see-also"></a><span data-ttu-id="435f4-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="435f4-110">See Also</span></span>

[<span data-ttu-id="435f4-111">Écriture d’un module Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="435f4-111">Writing a Windows PowerShell Module</span></span>](writing-a-windows-powershell-module.md)

[<span data-ttu-id="435f4-112">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="435f4-112">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/cmdlet-overview.md)
