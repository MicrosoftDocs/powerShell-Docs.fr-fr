---
title: Écrire un Module PowerShell de Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 3c6d8e410427d6cfaa1c15db421b3fe935f7d322
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082054"
---
# <a name="writing-a-windows-powershell-module"></a><span data-ttu-id="e77f9-102">Écriture d’un module Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e77f9-102">Writing a Windows PowerShell Module</span></span>

<span data-ttu-id="e77f9-103">Ce document est destiné aux administrateurs, développeurs de script et les développeurs d’applet de commande qui doivent empaqueter et distribuer leurs applets de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e77f9-103">This document is written for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell cmdlets.</span></span> <span data-ttu-id="e77f9-104">À l’aide de modules Windows PowerShell, vous pouvez empaqueter et distribuer vos solutions de Windows PowerShell sans utiliser un langage compilé.</span><span class="sxs-lookup"><span data-stu-id="e77f9-104">By using Windows PowerShell modules, you can package and distribute your Windows PowerShell solutions without using a compiled language.</span></span>

<span data-ttu-id="e77f9-105">Modules Windows PowerShell vous permettent de partition, organiser et d’abstraire votre code Windows PowerShell en unités autonomes réutilisables.</span><span class="sxs-lookup"><span data-stu-id="e77f9-105">Windows PowerShell modules enable you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="e77f9-106">Avec ces unités réutilisables, vous pouvez facilement partager vos modules directement avec d’autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="e77f9-106">With these reusable units, you can easily share your modules directly with others.</span></span> <span data-ttu-id="e77f9-107">Si vous êtes un développeur de script, vous pouvez également réorganiser des modules tiers pour créer des applications personnalisées en fonction de script.</span><span class="sxs-lookup"><span data-stu-id="e77f9-107">If you are a script developer, you can also repackage third-party modules to create custom script-based applications.</span></span> <span data-ttu-id="e77f9-108">Modules, similaires aux modules dans d’autres langages de script tels que Perl et Python, activer des solutions de script prêt pour la production qui utilisent des composants réutilisables et redistribuables, avec l’avantage supplémentaire de ce qui vous permet de réorganiser et d’abstraire plusieurs composants à créer des solutions personnalisées.</span><span class="sxs-lookup"><span data-stu-id="e77f9-108">Modules, similar to modules in other scripting languages such as Perl and Python, enable production-ready scripting solutions that use reusable, redistributable components, with the added benefit of enabling you to repackage and abstract multiple components to create custom solutions.</span></span>

<span data-ttu-id="e77f9-109">À leur plus simple, Windows PowerShell traite tout code de script Windows PowerShell valide enregistré dans un fichier .psm1 en tant que module.</span><span class="sxs-lookup"><span data-stu-id="e77f9-109">At their most basic, Windows PowerShell will treat any valid Windows PowerShell script code saved in a .psm1 file as a module.</span></span> <span data-ttu-id="e77f9-110">En tant que module traite également automatiquement n’importe quel assembly binaire applet de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e77f9-110">PowerShell will also automatically treat any binary cmdlet assembly as a module.</span></span> <span data-ttu-id="e77f9-111">Toutefois, vous pouvez également utiliser un module (ou plus précisément, un manifeste de module) pour regrouper un ensemble de la solution.</span><span class="sxs-lookup"><span data-stu-id="e77f9-111">However, you can also use a module (or more specifically, a module manifest) to bundle an entire solution together.</span></span> <span data-ttu-id="e77f9-112">Les scénarios suivants décrivent les utilisations courantes pour les modules Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e77f9-112">The following scenarios describe typical uses for Windows PowerShell modules.</span></span>

### <a name="libraries"></a><span data-ttu-id="e77f9-113">Bibliothèques</span><span class="sxs-lookup"><span data-stu-id="e77f9-113">Libraries</span></span>

<span data-ttu-id="e77f9-114">Modules peuvent être utilisés pour empaqueter et distribuer des bibliothèques cohérente de fonctions qui effectuent des tâches courantes.</span><span class="sxs-lookup"><span data-stu-id="e77f9-114">Modules can be used to package and distribute cohesive libraries of functions that perform common tasks.</span></span> <span data-ttu-id="e77f9-115">En règle générale, les noms de ces fonctions partagent un ou plusieurs noms qui reflètent la tâche courante qui elles sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="e77f9-115">Typically, the names of these functions share one or more nouns that reflect the common task that they are used for.</span></span> <span data-ttu-id="e77f9-116">Ces fonctions peuvent également être semblables aux classes du .NET Framework dans la mesure où ils peuvent avoir des membres publics et privés.</span><span class="sxs-lookup"><span data-stu-id="e77f9-116">These functions can also be similar to .NET Framework classes in that they can have public and private members.</span></span> <span data-ttu-id="e77f9-117">Par exemple, une bibliothèque peut contenir un ensemble de fonctions pour les transferts de fichiers.</span><span class="sxs-lookup"><span data-stu-id="e77f9-117">For example, a library can contain a set of functions for file transfers.</span></span> <span data-ttu-id="e77f9-118">Dans ce cas, le substantif reflétant la tâche courante peut être « fichier ».</span><span class="sxs-lookup"><span data-stu-id="e77f9-118">In this case, the noun reflecting the common task might be "file."</span></span>

### <a name="configuration"></a><span data-ttu-id="e77f9-119">Configuration</span><span class="sxs-lookup"><span data-stu-id="e77f9-119">Configuration</span></span>

<span data-ttu-id="e77f9-120">Modules peuvent être utilisés pour personnaliser votre environnement en ajoutant les variables, les fournisseurs, les fonctions et les applets de commande spécifique.</span><span class="sxs-lookup"><span data-stu-id="e77f9-120">Modules can be used to customize your environment by adding specific cmdlets, providers, functions, and variables.</span></span>

### <a name="compiled-code-development-and-distribution"></a><span data-ttu-id="e77f9-121">Développement de Code compilé et la Distribution</span><span class="sxs-lookup"><span data-stu-id="e77f9-121">Compiled Code Development and Distribution</span></span>

<span data-ttu-id="e77f9-122">Les développeurs d’applet de commande et le fournisseur peuvent utiliser des modules pour tester et distribuer leur code compilé sans avoir à créer des composants logiciel enfichables. Ils peuvent importer l’assembly qui contient le code compilé en tant que module (un module binaire) sans avoir à créer et inscrire les composants logiciel enfichables.</span><span class="sxs-lookup"><span data-stu-id="e77f9-122">Cmdlet and provider developers can use modules to test and distribute their compiled code without needing to create snap-ins. They can import the assembly that contains the compiled code as a module (a binary module) without needing to create and register snap-ins.</span></span>

## <a name="see-also"></a><span data-ttu-id="e77f9-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e77f9-123">See Also</span></span>

[<span data-ttu-id="e77f9-124">Comprendre un Module PowerShell de Windows</span><span class="sxs-lookup"><span data-stu-id="e77f9-124">Understanding a Windows PowerShell Module</span></span>](./understanding-a-windows-powershell-module.md)

[<span data-ttu-id="e77f9-125">Comment écrire un Module de Script PowerShell</span><span class="sxs-lookup"><span data-stu-id="e77f9-125">How to Write a PowerShell Script Module</span></span>](./how-to-write-a-powershell-script-module.md)

[<span data-ttu-id="e77f9-126">Comment écrire un Module PowerShell binaire</span><span class="sxs-lookup"><span data-stu-id="e77f9-126">How to Write a PowerShell Binary Module</span></span>](./how-to-write-a-powershell-binary-module.md)

[<span data-ttu-id="e77f9-127">Comment écrire un manifeste de Module PowerShell</span><span class="sxs-lookup"><span data-stu-id="e77f9-127">How to Write a PowerShell Module Manifest</span></span>](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6)

[<span data-ttu-id="e77f9-128">Modifier le chemin d’Installation de PSModulePath</span><span class="sxs-lookup"><span data-stu-id="e77f9-128">Modifying the PSModulePath Installation Path</span></span>](./modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="e77f9-129">Importation d’un Module PowerShell</span><span class="sxs-lookup"><span data-stu-id="e77f9-129">Importing a PowerShell Module</span></span>](./importing-a-powershell-module.md)

[<span data-ttu-id="e77f9-130">Installation d’un Module PowerShell</span><span class="sxs-lookup"><span data-stu-id="e77f9-130">Installing a PowerShell Module</span></span>](./installing-a-powershell-module.md)
