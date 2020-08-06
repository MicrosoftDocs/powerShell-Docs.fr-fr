---
title: Affichage des informations sur les erreurs | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e542110e9c35a74c5d4c112b0a831f7f8ad9242e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774573"
---
# <a name="displaying-error-information"></a><span data-ttu-id="6f6fe-102">Affichage des informations sur les erreurs</span><span class="sxs-lookup"><span data-stu-id="6f6fe-102">Displaying Error Information</span></span>

<span data-ttu-id="6f6fe-103">Cette rubrique explique comment les utilisateurs peuvent afficher des informations sur les erreurs.</span><span class="sxs-lookup"><span data-stu-id="6f6fe-103">This topic discusses the ways in which users can display error information.</span></span>

<span data-ttu-id="6f6fe-104">Lorsque votre applet de commande rencontre une erreur, la présentation des informations sur l’erreur sera, par défaut, similaire à la sortie d’erreur suivante.</span><span class="sxs-lookup"><span data-stu-id="6f6fe-104">When your cmdlet encounters an error, the presentation of the error information will, by default, resemble the following error output.</span></span>

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

<span data-ttu-id="6f6fe-105">Toutefois, les utilisateurs peuvent afficher les erreurs par catégorie en affectant à la variable la valeur `$ErrorView` `"CategoryView"` .</span><span class="sxs-lookup"><span data-stu-id="6f6fe-105">However, users can view errors by category by setting the `$ErrorView` variable to `"CategoryView"`.</span></span> <span data-ttu-id="6f6fe-106">Affichage des catégories affiche des informations spécifiques à partir de l’enregistrement d’erreur plutôt qu’une description de l’erreur en texte libre.</span><span class="sxs-lookup"><span data-stu-id="6f6fe-106">Category view displays specific information from the error record rather than a free-text description of the error.</span></span> <span data-ttu-id="6f6fe-107">Cette vue peut être utile si vous avez une longue liste d’erreurs à analyser.</span><span class="sxs-lookup"><span data-stu-id="6f6fe-107">This view can be useful if you have a long list of errors to scan.</span></span> <span data-ttu-id="6f6fe-108">Dans l’affichage des catégories, le message d’erreur précédent s’affiche comme suit.</span><span class="sxs-lookup"><span data-stu-id="6f6fe-108">In category view, the previous error message is displayed as follows.</span></span>

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

<span data-ttu-id="6f6fe-109">Pour plus d’informations sur les catégories d’erreurs, consultez [enregistrements d’erreurs Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="6f6fe-109">For more information about error categories, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6f6fe-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f6fe-110">See Also</span></span>

[<span data-ttu-id="6f6fe-111">Enregistrements d’erreurs Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6f6fe-111">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="6f6fe-112">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6f6fe-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
