---
ms.date: 09/13/2016
ms.topic: reference
title: Affichage des informations sur les erreurs
description: Affichage des informations sur les erreurs
ms.openlocfilehash: 37a3adb91d0e616a5c7f27bcab866f8da139f969
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653053"
---
# <a name="displaying-error-information"></a><span data-ttu-id="3cafb-103">Affichage des informations sur les erreurs</span><span class="sxs-lookup"><span data-stu-id="3cafb-103">Displaying Error Information</span></span>

<span data-ttu-id="3cafb-104">Cette rubrique explique comment les utilisateurs peuvent afficher des informations sur les erreurs.</span><span class="sxs-lookup"><span data-stu-id="3cafb-104">This topic discusses the ways in which users can display error information.</span></span>

<span data-ttu-id="3cafb-105">Lorsque votre applet de commande rencontre une erreur, la présentation des informations sur l’erreur sera, par défaut, similaire à la sortie d’erreur suivante.</span><span class="sxs-lookup"><span data-stu-id="3cafb-105">When your cmdlet encounters an error, the presentation of the error information will, by default, resemble the following error output.</span></span>

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

<span data-ttu-id="3cafb-106">Toutefois, les utilisateurs peuvent afficher les erreurs par catégorie en affectant à la variable la valeur `$ErrorView` `"CategoryView"` .</span><span class="sxs-lookup"><span data-stu-id="3cafb-106">However, users can view errors by category by setting the `$ErrorView` variable to `"CategoryView"`.</span></span> <span data-ttu-id="3cafb-107">Affichage des catégories affiche des informations spécifiques à partir de l’enregistrement d’erreur plutôt qu’une description de l’erreur en texte libre.</span><span class="sxs-lookup"><span data-stu-id="3cafb-107">Category view displays specific information from the error record rather than a free-text description of the error.</span></span> <span data-ttu-id="3cafb-108">Cette vue peut être utile si vous avez une longue liste d’erreurs à analyser.</span><span class="sxs-lookup"><span data-stu-id="3cafb-108">This view can be useful if you have a long list of errors to scan.</span></span> <span data-ttu-id="3cafb-109">Dans l’affichage des catégories, le message d’erreur précédent s’affiche comme suit.</span><span class="sxs-lookup"><span data-stu-id="3cafb-109">In category view, the previous error message is displayed as follows.</span></span>

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

<span data-ttu-id="3cafb-110">Pour plus d’informations sur les catégories d’erreurs, consultez [enregistrements d’erreurs Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="3cafb-110">For more information about error categories, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3cafb-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3cafb-111">See Also</span></span>

[<span data-ttu-id="3cafb-112">Enregistrements d’erreurs Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3cafb-112">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="3cafb-113">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3cafb-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
