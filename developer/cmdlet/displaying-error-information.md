---
title: Affichage des informations d’erreur | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858275"
---
# <a name="displaying-error-information"></a><span data-ttu-id="ca524-102">Affichage des informations sur les erreurs</span><span class="sxs-lookup"><span data-stu-id="ca524-102">Displaying Error Information</span></span>

<span data-ttu-id="ca524-103">Cette rubrique décrit les façons dans lequel les utilisateurs peuvent afficher des informations sur l’erreur.</span><span class="sxs-lookup"><span data-stu-id="ca524-103">This topic discusses the ways in which users can display error information.</span></span>

<span data-ttu-id="ca524-104">Lorsque votre applet de commande rencontre une erreur, la présentation des informations d’erreur, par défaut, ressemble à la sortie d’erreur suivant.</span><span class="sxs-lookup"><span data-stu-id="ca524-104">When your cmdlet encounters an error, the presentation of the error information will, by default, resemble the following error output.</span></span>

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

<span data-ttu-id="ca524-105">Toutefois, les utilisateurs peuvent afficher les erreurs par catégorie en définissant le `$ErrorView` à la variable `"CategoryView"`.</span><span class="sxs-lookup"><span data-stu-id="ca524-105">However, users can view errors by category by setting the `$ErrorView` variable to `"CategoryView"`.</span></span> <span data-ttu-id="ca524-106">Affichage des catégories affiche des informations spécifiques à partir de l’enregistrement d’erreur plutôt qu’une description de texte libre de l’erreur.</span><span class="sxs-lookup"><span data-stu-id="ca524-106">Category view displays specific information from the error record rather than a free-text description of the error.</span></span> <span data-ttu-id="ca524-107">Cette vue peut être utile si vous avez une longue liste d’erreurs à analyser.</span><span class="sxs-lookup"><span data-stu-id="ca524-107">This view can be useful if you have a long list of errors to scan.</span></span> <span data-ttu-id="ca524-108">Dans l’affichage des catégories, le message d’erreur précédent s’affiche comme suit.</span><span class="sxs-lookup"><span data-stu-id="ca524-108">In category view, the previous error message is displayed as follows.</span></span>

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

<span data-ttu-id="ca524-109">Pour plus d’informations sur les catégories d’erreur, consultez [enregistrements d’erreur Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="ca524-109">For more information about error categories, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ca524-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca524-110">See Also</span></span>

[<span data-ttu-id="ca524-111">Windows PowerShell erreur enregistrements</span><span class="sxs-lookup"><span data-stu-id="ca524-111">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="ca524-112">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ca524-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
