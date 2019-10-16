---
title: Écriture d’un module Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 0b7263ea19745e902fff04b993933e443d4d6333
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360618"
---
# <a name="writing-a-windows-powershell-module"></a><span data-ttu-id="7eda9-102">Écriture d’un module Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7eda9-102">Writing a Windows PowerShell Module</span></span>

<span data-ttu-id="7eda9-103">Ce document est destiné aux administrateurs, aux développeurs de scripts et aux développeurs d’applets de commande qui doivent empaqueter et distribuer leurs applets de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7eda9-103">This document is written for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell cmdlets.</span></span> <span data-ttu-id="7eda9-104">À l’aide des modules Windows PowerShell, vous pouvez empaqueter et distribuer vos solutions Windows PowerShell sans utiliser de langage compilé.</span><span class="sxs-lookup"><span data-stu-id="7eda9-104">By using Windows PowerShell modules, you can package and distribute your Windows PowerShell solutions without using a compiled language.</span></span>

<span data-ttu-id="7eda9-105">Les modules Windows PowerShell vous permettent de partitionner, d’organiser et d’abstraire votre code Windows PowerShell en unités autonomes réutilisables.</span><span class="sxs-lookup"><span data-stu-id="7eda9-105">Windows PowerShell modules enable you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="7eda9-106">Ces unités réutilisables vous permettent de partager facilement vos modules directement avec d’autres.</span><span class="sxs-lookup"><span data-stu-id="7eda9-106">With these reusable units, you can easily share your modules directly with others.</span></span> <span data-ttu-id="7eda9-107">Si vous êtes développeur de script, vous pouvez également reconditionner des modules tiers pour créer des applications basées sur des scripts personnalisés.</span><span class="sxs-lookup"><span data-stu-id="7eda9-107">If you are a script developer, you can also repackage third-party modules to create custom script-based applications.</span></span> <span data-ttu-id="7eda9-108">Les modules, similaires aux modules dans d’autres langages de script tels que Perl et Python, permettent des solutions de script prêtes pour la production qui utilisent des composants redistribuables réutilisables, avec l’avantage supplémentaire de vous permettre de reconditionner et d’abstraire plusieurs composants dans créer des solutions personnalisées.</span><span class="sxs-lookup"><span data-stu-id="7eda9-108">Modules, similar to modules in other scripting languages such as Perl and Python, enable production-ready scripting solutions that use reusable, redistributable components, with the added benefit of enabling you to repackage and abstract multiple components to create custom solutions.</span></span>

<span data-ttu-id="7eda9-109">Au niveau le plus basique, Windows PowerShell traite tout code de script Windows PowerShell valide enregistré dans un fichier. psm1 en tant que module.</span><span class="sxs-lookup"><span data-stu-id="7eda9-109">At their most basic, Windows PowerShell will treat any valid Windows PowerShell script code saved in a .psm1 file as a module.</span></span> <span data-ttu-id="7eda9-110">PowerShell traitera également automatiquement tout assembly d’applet de commande binaire comme un module.</span><span class="sxs-lookup"><span data-stu-id="7eda9-110">PowerShell will also automatically treat any binary cmdlet assembly as a module.</span></span> <span data-ttu-id="7eda9-111">Toutefois, vous pouvez également utiliser un module (ou plus spécifiquement, un manifeste de module) pour regrouper une solution entière.</span><span class="sxs-lookup"><span data-stu-id="7eda9-111">However, you can also use a module (or more specifically, a module manifest) to bundle an entire solution together.</span></span> <span data-ttu-id="7eda9-112">Les scénarios suivants décrivent les utilisations typiques des modules Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7eda9-112">The following scenarios describe typical uses for Windows PowerShell modules.</span></span>

### <a name="libraries"></a><span data-ttu-id="7eda9-113">Bibliothèques</span><span class="sxs-lookup"><span data-stu-id="7eda9-113">Libraries</span></span>

<span data-ttu-id="7eda9-114">Les modules peuvent être utilisés pour empaqueter et distribuer des bibliothèques cohérentes de fonctions qui effectuent des tâches courantes.</span><span class="sxs-lookup"><span data-stu-id="7eda9-114">Modules can be used to package and distribute cohesive libraries of functions that perform common tasks.</span></span> <span data-ttu-id="7eda9-115">En règle générale, les noms de ces fonctions partagent un ou plusieurs noms qui reflètent la tâche courante pour laquelle ils sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="7eda9-115">Typically, the names of these functions share one or more nouns that reflect the common task that they are used for.</span></span> <span data-ttu-id="7eda9-116">Ces fonctions peuvent également être similaires aux classes .NET Framework dans la mesure où elles peuvent avoir des membres publics et privés.</span><span class="sxs-lookup"><span data-stu-id="7eda9-116">These functions can also be similar to .NET Framework classes in that they can have public and private members.</span></span> <span data-ttu-id="7eda9-117">Par exemple, une bibliothèque peut contenir un ensemble de fonctions pour les transferts de fichiers.</span><span class="sxs-lookup"><span data-stu-id="7eda9-117">For example, a library can contain a set of functions for file transfers.</span></span> <span data-ttu-id="7eda9-118">Dans ce cas, le substantif qui reflète la tâche courante peut être « file ».</span><span class="sxs-lookup"><span data-stu-id="7eda9-118">In this case, the noun reflecting the common task might be "file."</span></span>

### <a name="configuration"></a><span data-ttu-id="7eda9-119">Configuration</span><span class="sxs-lookup"><span data-stu-id="7eda9-119">Configuration</span></span>

<span data-ttu-id="7eda9-120">Les modules peuvent être utilisés pour personnaliser votre environnement en ajoutant des applets de commande, des fournisseurs, des fonctions et des variables spécifiques.</span><span class="sxs-lookup"><span data-stu-id="7eda9-120">Modules can be used to customize your environment by adding specific cmdlets, providers, functions, and variables.</span></span>

### <a name="compiled-code-development-and-distribution"></a><span data-ttu-id="7eda9-121">Développement et distribution de code compilé</span><span class="sxs-lookup"><span data-stu-id="7eda9-121">Compiled Code Development and Distribution</span></span>

<span data-ttu-id="7eda9-122">Les développeurs d’applets de commande et fournisseurs peuvent utiliser des modules pour tester et distribuer leur code compilé sans avoir besoin de créer des composants logiciels enfichables. Ils peuvent importer l’assembly qui contient le code compilé en tant que module (un module binaire) sans avoir à créer et inscrire des composants logiciels enfichables.</span><span class="sxs-lookup"><span data-stu-id="7eda9-122">Cmdlet and provider developers can use modules to test and distribute their compiled code without needing to create snap-ins. They can import the assembly that contains the compiled code as a module (a binary module) without needing to create and register snap-ins.</span></span>

## <a name="see-also"></a><span data-ttu-id="7eda9-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7eda9-123">See Also</span></span>

[<span data-ttu-id="7eda9-124">Fonctionnement d’un module Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7eda9-124">Understanding a Windows PowerShell Module</span></span>](./understanding-a-windows-powershell-module.md)

[<span data-ttu-id="7eda9-125">Comment écrire un module de script PowerShell</span><span class="sxs-lookup"><span data-stu-id="7eda9-125">How to Write a PowerShell Script Module</span></span>](./how-to-write-a-powershell-script-module.md)

[<span data-ttu-id="7eda9-126">Comment écrire un module binaire PowerShell</span><span class="sxs-lookup"><span data-stu-id="7eda9-126">How to Write a PowerShell Binary Module</span></span>](./how-to-write-a-powershell-binary-module.md)

[<span data-ttu-id="7eda9-127">Comment écrire un manifeste de module PowerShell</span><span class="sxs-lookup"><span data-stu-id="7eda9-127">How to Write a PowerShell Module Manifest</span></span>](how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="7eda9-128">Modification du chemin d’installation de PSModulePath</span><span class="sxs-lookup"><span data-stu-id="7eda9-128">Modifying the PSModulePath Installation Path</span></span>](./modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="7eda9-129">Importation d’un module PowerShell</span><span class="sxs-lookup"><span data-stu-id="7eda9-129">Importing a PowerShell Module</span></span>](./importing-a-powershell-module.md)

[<span data-ttu-id="7eda9-130">Installation d’un module PowerShell</span><span class="sxs-lookup"><span data-stu-id="7eda9-130">Installing a PowerShell Module</span></span>](./installing-a-powershell-module.md)
