---
title: Concepts des applets de commande Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b3ef3f4-c626-4679-884f-406a37412b3e
caps.latest.revision: 16
ms.openlocfilehash: 2f84c57da7429462c69b2a020d9f8ac04f8d0f35
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369118"
---
# <a name="windows-powershell-cmdlet-concepts"></a><span data-ttu-id="c4c9c-102">Concepts des applets de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c4c9c-102">Windows PowerShell Cmdlet Concepts</span></span>

<span data-ttu-id="c4c9c-103">Cette section décrit le fonctionnement des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="c4c9c-103">This section describes how cmdlets work.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="c4c9c-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c4c9c-104">In This Section</span></span>

<span data-ttu-id="c4c9c-105">Cette section comprend les rubriques suivantes.</span><span class="sxs-lookup"><span data-stu-id="c4c9c-105">This section includes the following topics.</span></span>

<span data-ttu-id="c4c9c-106">[Instructions de développement d’applets](./cmdlet-development-guidelines.md) de commande Cette rubrique fournit des instructions de développement qui peuvent être utilisées pour produire des applets de commande bien formées.</span><span class="sxs-lookup"><span data-stu-id="c4c9c-106">[Cmdlet Development Guidelines](./cmdlet-development-guidelines.md) This topic provides development guidelines that can be used to produce well-formed cmdlets.</span></span>

<span data-ttu-id="c4c9c-107">[Déclaration de classe d’applet](./cmdlet-class-declaration.md) de commande Cette rubrique décrit la déclaration de classe d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c4c9c-107">[Cmdlet Class Declaration](./cmdlet-class-declaration.md) This topic describes cmdlet class declaration.</span></span>

<span data-ttu-id="c4c9c-108">[Verbes approuvés pour les commandes Windows PowerShell](./approved-verbs-for-windows-powershell-commands.md) Cette rubrique répertorie les verbes d’applet de commande prédéfinis que vous pouvez utiliser lorsque vous déclarez une classe d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c4c9c-108">[Approved Verbs for Windows PowerShell Commands](./approved-verbs-for-windows-powershell-commands.md) This topic lists the predefined cmdlet verbs that you can use when you declare a cmdlet class.</span></span>

<span data-ttu-id="c4c9c-109">[Méthodes de traitement d’entrée d’applet](./cmdlet-input-processing-methods.md) de commande Cette rubrique décrit les méthodes qui permettent à une applet de commande d’effectuer des opérations de prétraitement, des opérations de traitement d’entrée et des opérations de validation de traitement.</span><span class="sxs-lookup"><span data-stu-id="c4c9c-109">[Cmdlet Input Processing Methods](./cmdlet-input-processing-methods.md) This topic describes the methods that allow a cmdlet to perform preprocessing operations, input processing operations, and post processing operations.</span></span>

<span data-ttu-id="c4c9c-110">[Paramètres d’applet](./cmdlet-parameters.md) de commande Cette section décrit les différents types de paramètres que vous pouvez ajouter aux applets de commande.</span><span class="sxs-lookup"><span data-stu-id="c4c9c-110">[Cmdlet Parameters](./cmdlet-parameters.md) This section describes the different types of parameters that you can add to cmdlets.</span></span>

<span data-ttu-id="c4c9c-111">[Attributs d’applet](./cmdlet-attributes.md) de commande Cette section décrit les attributs utilisés pour déclarer des classes .NET Framework en tant qu’applets de commande, pour déclarer des champs en tant que paramètres d’applet de commande et pour déclarer des règles de validation d’entrée pour les paramètres.</span><span class="sxs-lookup"><span data-stu-id="c4c9c-111">[Cmdlet Attributes](./cmdlet-attributes.md) This section describes the attributes that are used to declare .NET Framework classes as cmdlets, to declare fields as cmdlet parameters, and to declare input validation rules for parameters.</span></span>

<span data-ttu-id="c4c9c-112">[Alias d’applet](./cmdlet-aliases.md) de commande Cette rubrique décrit les alias d’applets de commande.</span><span class="sxs-lookup"><span data-stu-id="c4c9c-112">[Cmdlet Aliases](./cmdlet-aliases.md) This topic describes cmdlet aliases.</span></span>

<span data-ttu-id="c4c9c-113">[Sortie](./cmdlet-output.md) de l’applet de commande Cette section décrit le type de sortie que les applets de commande peuvent retourner et comment définir et afficher les objets retournés par les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="c4c9c-113">[Cmdlet Output](./cmdlet-output.md) This section describes the type of output that cmdlets can return and how to define and display the objects that are returned by cmdlets.</span></span>

<span data-ttu-id="c4c9c-114">[Inscription des applets](./modules-and-snap-ins.md) de commande Cette section décrit comment inscrire des applets de commande à l’aide de modules et de composants logiciels enfichables.</span><span class="sxs-lookup"><span data-stu-id="c4c9c-114">[Registering Cmdlets](./modules-and-snap-ins.md) This section describes how to register cmdlets by using modules and snap-ins.</span></span>

<span data-ttu-id="c4c9c-115">[Demande de confirmation](./requesting-confirmation-from-cmdlets.md) Cette section décrit comment les applets de commande demandent confirmation à un utilisateur avant d’apporter une modification au système.</span><span class="sxs-lookup"><span data-stu-id="c4c9c-115">[Requesting Confirmation](./requesting-confirmation-from-cmdlets.md) This section describes how cmdlets request confirmation from a user before they make a change to the system.</span></span>

<span data-ttu-id="c4c9c-116">[Rapport d’erreurs Windows PowerShell](./error-reporting-concepts.md) Cette section décrit comment les applets de commande signalent les erreurs de fin et les erreurs sans fin d’opération, et explique comment interpréter les enregistrements d’erreur.</span><span class="sxs-lookup"><span data-stu-id="c4c9c-116">[Windows PowerShell Error Reporting](./error-reporting-concepts.md) This section describes how cmdlets report terminating errors and non-terminating errors, and it describes how to interpret error records.</span></span>

<span data-ttu-id="c4c9c-117">[Travaux en arrière-plan](./background-jobs.md) Cette rubrique décrit comment les applets de commande peuvent effectuer leur travail dans des tâches en arrière-plan qui n’interfèrent pas avec les commandes qui s’exécutent dans la session active.</span><span class="sxs-lookup"><span data-stu-id="c4c9c-117">[Background Jobs](./background-jobs.md) This topic describes how cmdlets can perform their work within background jobs that do not interfere with the commands that are executing in the current session.</span></span>

<span data-ttu-id="c4c9c-118">[Appel d’applets de commande et de scripts dans une applet de](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) commande Cette rubrique décrit comment les applets de commande peuvent appeler d’autres applets de commande et scripts à partir de leurs méthodes de traitement d’entrée.</span><span class="sxs-lookup"><span data-stu-id="c4c9c-118">[Invoking Cmdlets and Scripts Within a Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) This topic describes how cmdlets can invoke other cmdlets and scripts from within their input processing methods.</span></span>

<span data-ttu-id="c4c9c-119">[Ensembles d’applets](./cmdlet-sets.md) de commande Cette rubrique décrit l’utilisation des classes de base pour créer des ensembles d’applets de commande.</span><span class="sxs-lookup"><span data-stu-id="c4c9c-119">[Cmdlet Sets](./cmdlet-sets.md) This topic describes using base classes to create sets of cmdlets.</span></span>

<span data-ttu-id="c4c9c-120">[État de session Windows PowerShell](./windows-powershell-session-state.md) Cette rubrique décrit l’état de session Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c4c9c-120">[Windows PowerShell Session State](./windows-powershell-session-state.md) This topic describes Windows PowerShell session state.</span></span>
