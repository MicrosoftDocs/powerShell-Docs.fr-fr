---
title: Concepts d’applet de commande PowerShell de Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b3ef3f4-c626-4679-884f-406a37412b3e
caps.latest.revision: 16
ms.openlocfilehash: 2f84c57da7429462c69b2a020d9f8ac04f8d0f35
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067064"
---
# <a name="windows-powershell-cmdlet-concepts"></a><span data-ttu-id="d7deb-102">Concepts des applets de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d7deb-102">Windows PowerShell Cmdlet Concepts</span></span>

<span data-ttu-id="d7deb-103">Cette section décrit le fonctionnement des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="d7deb-103">This section describes how cmdlets work.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d7deb-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d7deb-104">In This Section</span></span>

<span data-ttu-id="d7deb-105">Cette section comprend les rubriques suivantes.</span><span class="sxs-lookup"><span data-stu-id="d7deb-105">This section includes the following topics.</span></span>

<span data-ttu-id="d7deb-106">[Directives de développement d’applet de commande](./cmdlet-development-guidelines.md) cette rubrique fournit des instructions de développement qui peuvent être utilisées pour produire des applets de commande bien formé.</span><span class="sxs-lookup"><span data-stu-id="d7deb-106">[Cmdlet Development Guidelines](./cmdlet-development-guidelines.md) This topic provides development guidelines that can be used to produce well-formed cmdlets.</span></span>

<span data-ttu-id="d7deb-107">[Déclaration de classe d’applet de commande](./cmdlet-class-declaration.md) cette rubrique décrit la déclaration de classe d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d7deb-107">[Cmdlet Class Declaration](./cmdlet-class-declaration.md) This topic describes cmdlet class declaration.</span></span>

<span data-ttu-id="d7deb-108">[Approbation des verbes pour les commandes Windows PowerShell](./approved-verbs-for-windows-powershell-commands.md) cette rubrique répertorie les verbes d’applet de commande prédéfinies que vous pouvez utiliser lorsque vous déclarez une classe de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d7deb-108">[Approved Verbs for Windows PowerShell Commands](./approved-verbs-for-windows-powershell-commands.md) This topic lists the predefined cmdlet verbs that you can use when you declare a cmdlet class.</span></span>

<span data-ttu-id="d7deb-109">[Applet de commande des méthodes de traitement d’entrée](./cmdlet-input-processing-methods.md) cette rubrique décrit les méthodes qui permettent une applet de commande effectuer les opérations de prétraitement, entrée des opérations de traitement et publier les opérations de traitement.</span><span class="sxs-lookup"><span data-stu-id="d7deb-109">[Cmdlet Input Processing Methods](./cmdlet-input-processing-methods.md) This topic describes the methods that allow a cmdlet to perform preprocessing operations, input processing operations, and post processing operations.</span></span>

<span data-ttu-id="d7deb-110">[Paramètres de l’applet de commande](./cmdlet-parameters.md) cette section décrit les différents types de paramètres que vous pouvez ajouter aux applets de commande.</span><span class="sxs-lookup"><span data-stu-id="d7deb-110">[Cmdlet Parameters](./cmdlet-parameters.md) This section describes the different types of parameters that you can add to cmdlets.</span></span>

<span data-ttu-id="d7deb-111">[Attributs de l’applet de commande](./cmdlet-attributes.md) cette section décrit les attributs qui sont utilisés pour déclarer des classes .NET Framework en tant que les applets de commande, pour déclarer des champs en tant que paramètres de l’applet de commande et pour déclarer des règles de validation d’entrée pour les paramètres.</span><span class="sxs-lookup"><span data-stu-id="d7deb-111">[Cmdlet Attributes](./cmdlet-attributes.md) This section describes the attributes that are used to declare .NET Framework classes as cmdlets, to declare fields as cmdlet parameters, and to declare input validation rules for parameters.</span></span>

<span data-ttu-id="d7deb-112">[Alias d’applet de commande](./cmdlet-aliases.md) cette rubrique décrit les alias d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d7deb-112">[Cmdlet Aliases](./cmdlet-aliases.md) This topic describes cmdlet aliases.</span></span>

<span data-ttu-id="d7deb-113">[Sortie de l’applet de commande](./cmdlet-output.md) cette section décrit le type de sortie qui retournent des applets de commande et comment définir et afficher les objets retournés par les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="d7deb-113">[Cmdlet Output](./cmdlet-output.md) This section describes the type of output that cmdlets can return and how to define and display the objects that are returned by cmdlets.</span></span>

<span data-ttu-id="d7deb-114">[L’inscription des applets de commande](./modules-and-snap-ins.md) cette section décrit comment inscrire des applets de commande à l’aide de modules et composants logiciel enfichables.</span><span class="sxs-lookup"><span data-stu-id="d7deb-114">[Registering Cmdlets](./modules-and-snap-ins.md) This section describes how to register cmdlets by using modules and snap-ins.</span></span>

<span data-ttu-id="d7deb-115">[Demander Confirmation](./requesting-confirmation-from-cmdlets.md) cette section décrit comment applets de commande demande confirmation à partir d’un utilisateur avant de leur apportent une modification au système.</span><span class="sxs-lookup"><span data-stu-id="d7deb-115">[Requesting Confirmation](./requesting-confirmation-from-cmdlets.md) This section describes how cmdlets request confirmation from a user before they make a change to the system.</span></span>

<span data-ttu-id="d7deb-116">[Rapport d’erreurs Windows PowerShell](./error-reporting-concepts.md) cette section décrit comment les applets de commande signalent des erreurs avec fin d’exécution et les erreurs sans fin d’exécution, et elle explique comment interpréter les enregistrements d’erreur.</span><span class="sxs-lookup"><span data-stu-id="d7deb-116">[Windows PowerShell Error Reporting](./error-reporting-concepts.md) This section describes how cmdlets report terminating errors and non-terminating errors, and it describes how to interpret error records.</span></span>

<span data-ttu-id="d7deb-117">[Tâches en arrière-plan](./background-jobs.md) cette rubrique décrit comment les applets de commande peuvent effectuer leur travail en tâches en arrière-plan qui n’interfèrent pas avec les commandes qui sont exécutent dans la session active.</span><span class="sxs-lookup"><span data-stu-id="d7deb-117">[Background Jobs](./background-jobs.md) This topic describes how cmdlets can perform their work within background jobs that do not interfere with the commands that are executing in the current session.</span></span>

<span data-ttu-id="d7deb-118">[Appel des applets de commande et Scripts au sein d’une applet de commande](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) cette rubrique décrit comment applets de commande peut appeler autres applets de commande et les scripts depuis leur entrée méthodes de traitement.</span><span class="sxs-lookup"><span data-stu-id="d7deb-118">[Invoking Cmdlets and Scripts Within a Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) This topic describes how cmdlets can invoke other cmdlets and scripts from within their input processing methods.</span></span>

<span data-ttu-id="d7deb-119">[Applet de commande définit](./cmdlet-sets.md) cette rubrique décrit l’utilisation des classes de base pour créer des jeux d’applets de commande.</span><span class="sxs-lookup"><span data-stu-id="d7deb-119">[Cmdlet Sets](./cmdlet-sets.md) This topic describes using base classes to create sets of cmdlets.</span></span>

<span data-ttu-id="d7deb-120">[État de Session Windows PowerShell](./windows-powershell-session-state.md) cette rubrique décrit l’état de session Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d7deb-120">[Windows PowerShell Session State](./windows-powershell-session-state.md) This topic describes Windows PowerShell session state.</span></span>
