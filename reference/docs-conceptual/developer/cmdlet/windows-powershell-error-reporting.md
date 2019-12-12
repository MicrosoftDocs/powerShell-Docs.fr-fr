---
title: Rapport d’erreurs Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61b7773a-c346-4835-a928-7212dc4c85bc
caps.latest.revision: 7
ms.openlocfilehash: 259de341fd2fcce2b0c4629f806b4348cba1ff2c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364268"
---
# <a name="windows-powershell-error-reporting"></a><span data-ttu-id="da9f4-102">Rapport d’erreurs Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="da9f4-102">Windows PowerShell Error Reporting</span></span>

<span data-ttu-id="da9f4-103">Les rubriques de cette section expliquent comment les applets de commande signalent des erreurs.</span><span class="sxs-lookup"><span data-stu-id="da9f4-103">The topics in this section discuss how cmdlets report errors.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="da9f4-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="da9f4-104">In This Section</span></span>

<span data-ttu-id="da9f4-105">[Concepts de signalement d’erreurs](./error-reporting-concepts.md) Décrit les deux mécanismes que les applets de commande peuvent utiliser pour signaler des erreurs.</span><span class="sxs-lookup"><span data-stu-id="da9f4-105">[Error Reporting Concepts](./error-reporting-concepts.md) Describes the two mechanisms that cmdlets can use to report errors.</span></span>

<span data-ttu-id="da9f4-106">[Arrêt des erreurs](./terminating-errors.md) Décrit la méthode utilisée pour signaler des erreurs de fin, où cette méthode peut être appelée à partir de l’applet de commande, et les exceptions qui peuvent être retournées par le runtime Windows PowerShell lorsque la méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="da9f4-106">[Terminating Errors](./terminating-errors.md) Describes the method used to report terminating errors, where that method can be called from within the cmdlet, and exceptions that can be returned by the Windows PowerShell runtime when the method is called.</span></span>

<span data-ttu-id="da9f4-107">[Erreurs sans fin d’arrêt](./non-terminating-errors.md) Décrit la méthode utilisée pour signaler des erreurs sans fin d’arrêt et où cette méthode peut être appelée à partir de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="da9f4-107">[Non-Terminating Errors](./non-terminating-errors.md) Describes the method used to report non-terminating errors and where that method can be called from within the cmdlet.</span></span>

<span data-ttu-id="da9f4-108">[Affichage des informations d’erreur par catégorie](./displaying-error-information.md) Explique comment les utilisateurs peuvent afficher une erreur.</span><span class="sxs-lookup"><span data-stu-id="da9f4-108">[Displaying Error Information by Category](./displaying-error-information.md) Discusses the ways that users can display error.</span></span>

<span data-ttu-id="da9f4-109">[Enregistrements d’erreurs Windows PowerShell](./windows-powershell-error-records.md) Décrit les composants d’un enregistrement d’erreur.</span><span class="sxs-lookup"><span data-stu-id="da9f4-109">[Windows PowerShell Error Records](./windows-powershell-error-records.md) Describes the components of an error record.</span></span>

<span data-ttu-id="da9f4-110">[Interprétation des objets ErrorRecord](./interpreting-errorrecord-objects.md) Explique comment les objets ErrorRecord sont interprétés.</span><span class="sxs-lookup"><span data-stu-id="da9f4-110">[Interpreting ErrorRecord Objects](./interpreting-errorrecord-objects.md) Discusses how ErrorRecord objects are interpreted.</span></span>

## <a name="see-also"></a><span data-ttu-id="da9f4-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da9f4-111">See Also</span></span>

[<span data-ttu-id="da9f4-112">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="da9f4-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
