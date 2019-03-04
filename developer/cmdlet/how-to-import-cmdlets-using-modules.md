---
title: Comment importer les applets de commande à l’aide de Modules | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: c007bb11324e10ffd100797dccd9e6ab0d09a73e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859145"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="53efb-102">Guide pratique pour importer des applets de commande avec des modules</span><span class="sxs-lookup"><span data-stu-id="53efb-102">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="53efb-103">Cette rubrique décrit comment importer les applets de commande à une session Windows PowerShell à l’aide d’un module binaire.</span><span class="sxs-lookup"><span data-stu-id="53efb-103">This topic describes how to import cmdlets to a Windows PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="53efb-104">Les membres des modules peuvent inclure des applets de commande, fournisseurs, fonctions, des variables, alias et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="53efb-104">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="53efb-105">Composants logiciel enfichables peuvent contenir uniquement des applets de commande et des fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="53efb-105">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="53efb-106">Comment charger des applets de commande à l’aide d’un module</span><span class="sxs-lookup"><span data-stu-id="53efb-106">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="53efb-107">Créez un dossier de module qui porte le même nom que le fichier d’assembly dans lequel les applets de commande sont implémentées.</span><span class="sxs-lookup"><span data-stu-id="53efb-107">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="53efb-108">Dans cette procédure, le dossier de module est créé dans le `system32` dossier.</span><span class="sxs-lookup"><span data-stu-id="53efb-108">In this procedure, the module folder is created in the `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

2. <span data-ttu-id="53efb-109">Assurez-vous que le `PSModulePath` variable d’environnement inclut le chemin d’accès à votre nouveau dossier de module.</span><span class="sxs-lookup"><span data-stu-id="53efb-109">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="53efb-110">Par défaut, le dossier du système est déjà ajouté à la `PSModulePath` variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="53efb-110">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span>

3. <span data-ttu-id="53efb-111">Copiez l’assembly de l’applet de commande dans le dossier de module.</span><span class="sxs-lookup"><span data-stu-id="53efb-111">Copy the cmdlet assembly into the module folder.</span></span>

4. <span data-ttu-id="53efb-112">Exécutez la commande suivante pour ajouter les applets de commande à la session :</span><span class="sxs-lookup"><span data-stu-id="53efb-112">Run the following command to add the cmdlets to the session:</span></span>

   `import-module [Module_Name]`

   <span data-ttu-id="53efb-113">Cette procédure peut être utilisée pour tester vos applets de commande.</span><span class="sxs-lookup"><span data-stu-id="53efb-113">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="53efb-114">Il ajoute toutes les applets de commande dans l’assembly à la session.</span><span class="sxs-lookup"><span data-stu-id="53efb-114">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="53efb-115">Pour plus d’informations sur les modules, consultez les différents types de modules, les différentes façons de charger des modules et comment limiter les éléments d’un module sont exportées, [écrire un PowerShell Module de Windows](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="53efb-115">For more information about modules, the different types of modules, the different ways to load modules, and how to restrict the elements of a module that are exported, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="53efb-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53efb-116">See Also</span></span>

[<span data-ttu-id="53efb-117">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="53efb-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="53efb-118">Installation des Modules</span><span class="sxs-lookup"><span data-stu-id="53efb-118">Installing Modules</span></span>](../module/installing-a-powershell-module.md)