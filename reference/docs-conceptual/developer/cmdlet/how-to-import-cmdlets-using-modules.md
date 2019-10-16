---
title: Comment importer des applets de commande à l’aide de modules | Microsoft Docs
ms.custom: ''
ms.date: 08/28/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: 2f145795a57c988da0cb4ed294142aa141c53cae
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364458"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="67c73-102">Guide pratique pour importer des applets de commande avec des modules</span><span class="sxs-lookup"><span data-stu-id="67c73-102">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="67c73-103">Cet article explique comment importer des applets de commande dans une session PowerShell à l’aide d’un module binaire.</span><span class="sxs-lookup"><span data-stu-id="67c73-103">This article describes how to import cmdlets to a PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="67c73-104">Les membres des modules peuvent inclure des applets de commande, des fournisseurs, des fonctions, des variables, des alias et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="67c73-104">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="67c73-105">Les composants logiciels enfichables peuvent contenir uniquement des applets de commande et des fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="67c73-105">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="67c73-106">Comment charger des applets de commande à l’aide d’un module</span><span class="sxs-lookup"><span data-stu-id="67c73-106">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="67c73-107">Créez un dossier de module portant le même nom que le fichier d’assembly dans lequel les applets de commande sont implémentées.</span><span class="sxs-lookup"><span data-stu-id="67c73-107">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="67c73-108">Dans cette procédure, le dossier de module est créé dans le dossier Windows `system32`.</span><span class="sxs-lookup"><span data-stu-id="67c73-108">In this procedure, the module folder is created in the Windows `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

1. <span data-ttu-id="67c73-109">Assurez-vous que la variable d’environnement `PSModulePath` comprend le chemin d’accès à votre nouveau dossier de module.</span><span class="sxs-lookup"><span data-stu-id="67c73-109">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="67c73-110">Par défaut, le dossier système est déjà ajouté à la variable d’environnement `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="67c73-110">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span> <span data-ttu-id="67c73-111">Pour afficher le `PSModulePath`, tapez : `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="67c73-111">To view the `PSModulePath`, type: `$env:PSModulePath`.</span></span>

1. <span data-ttu-id="67c73-112">Copiez l’assembly de l’applet de commande dans le dossier du module.</span><span class="sxs-lookup"><span data-stu-id="67c73-112">Copy the cmdlet assembly into the module folder.</span></span>

1. <span data-ttu-id="67c73-113">Ajoutez un fichier manifeste de module (`.psd1`) dans le dossier racine du module.</span><span class="sxs-lookup"><span data-stu-id="67c73-113">Add a module manifest file (`.psd1`) in the module's root folder.</span></span> <span data-ttu-id="67c73-114">PowerShell utilise le manifeste de module pour importer votre module.</span><span class="sxs-lookup"><span data-stu-id="67c73-114">PowerShell uses the module manifest to import your module.</span></span> <span data-ttu-id="67c73-115">Pour plus d’informations, consultez [Comment écrire un manifeste de module PowerShell](../module/how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="67c73-115">For more information, see [How to Write a PowerShell Module Manifest](../module/how-to-write-a-powershell-module-manifest.md).</span></span>

1. <span data-ttu-id="67c73-116">Exécutez la commande suivante pour ajouter les applets de commande à la session :</span><span class="sxs-lookup"><span data-stu-id="67c73-116">Run the following command to add the cmdlets to the session:</span></span>

   `Import-Module [Module_Name]`

   <span data-ttu-id="67c73-117">Cette procédure peut être utilisée pour tester vos applets de commande.</span><span class="sxs-lookup"><span data-stu-id="67c73-117">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="67c73-118">Elle ajoute toutes les applets de commande de l’assembly à la session.</span><span class="sxs-lookup"><span data-stu-id="67c73-118">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="67c73-119">Pour plus d’informations sur les modules, consultez [écriture d’un module Windows PowerShell](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="67c73-119">For more information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="67c73-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67c73-120">See also</span></span>

[<span data-ttu-id="67c73-121">Comment écrire un manifeste de module PowerShell</span><span class="sxs-lookup"><span data-stu-id="67c73-121">How to Write a PowerShell Module Manifest</span></span>](../module/how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="67c73-122">Importation d’un module PowerShell</span><span class="sxs-lookup"><span data-stu-id="67c73-122">Importing a PowerShell Module</span></span>](../module/importing-a-powershell-module.md)

[<span data-ttu-id="67c73-123">Import-Module</span><span class="sxs-lookup"><span data-stu-id="67c73-123">Import-Module</span></span>](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[<span data-ttu-id="67c73-124">Installation des modules</span><span class="sxs-lookup"><span data-stu-id="67c73-124">Installing Modules</span></span>](../module/installing-a-powershell-module.md)

[<span data-ttu-id="67c73-125">Modification du chemin d’installation de PSModulePath</span><span class="sxs-lookup"><span data-stu-id="67c73-125">Modifying the PSModulePath Installation Path</span></span>](../module/modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="67c73-126">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="67c73-126">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
