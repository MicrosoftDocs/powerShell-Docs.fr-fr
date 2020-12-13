---
ms.date: 09/13/2016
ms.topic: reference
title: État de session Windows PowerShell
description: État de session Windows PowerShell
ms.openlocfilehash: 51de92f1f392f708cf49c7ccb4a6808fd628076c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668131"
---
# <a name="windows-powershell-session-state"></a><span data-ttu-id="d28df-103">État de session Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d28df-103">Windows PowerShell Session State</span></span>

<span data-ttu-id="d28df-104">L’état de session fait référence à la configuration actuelle d’une session ou d’un module Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d28df-104">Session state refers to the current configuration of a Windows PowerShell session or module.</span></span> <span data-ttu-id="d28df-105">Une session Windows PowerShell est l’environnement d’exploitation qui est utilisé de manière interactive par l’utilisateur de la ligne de commande ou par programme par une application hôte.</span><span class="sxs-lookup"><span data-stu-id="d28df-105">A Windows PowerShell session is the operational environment that is used interactively by the command-line user or programmatically by a host application.</span></span> <span data-ttu-id="d28df-106">L’état de session d’une session est appelé état de session global.</span><span class="sxs-lookup"><span data-stu-id="d28df-106">The session state for a session is referred to as the global session state.</span></span>

<span data-ttu-id="d28df-107">Du point de vue du développeur, une session Windows PowerShell fait référence au délai entre le moment où une application hôte ouvre une instance d’exécution Windows PowerShell et le moment où elle ferme l’instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="d28df-107">From a developer perspective, a Windows PowerShell session refers to the time between when a host application opens a Windows PowerShell runspace and when it closes the runspace.</span></span> <span data-ttu-id="d28df-108">Vu d’une autre façon, la session est la durée de vie d’une instance du moteur Windows PowerShell qui est appelée alors que l’instance d’exécution existe.</span><span class="sxs-lookup"><span data-stu-id="d28df-108">Looked at another way, the session is the lifetime of an instance of the Windows PowerShell engine that is invoked while the runspace exists.</span></span>

## <a name="module-session-state"></a><span data-ttu-id="d28df-109">État de session de module</span><span class="sxs-lookup"><span data-stu-id="d28df-109">Module Session State</span></span>

<span data-ttu-id="d28df-110">Les États de session de module sont créés chaque fois que le module ou l’un de ses modules imbriqués est importé dans la session.</span><span class="sxs-lookup"><span data-stu-id="d28df-110">Module session states are created whenever the module or one of its nested modules is imported into the session.</span></span> <span data-ttu-id="d28df-111">Lorsqu’un module exporte un élément tel qu’une applet de commande, une fonction ou un script, une référence à cet élément est ajoutée à l’état de session global de la session.</span><span class="sxs-lookup"><span data-stu-id="d28df-111">When a module exports an element such as a cmdlet, function, or script, a reference to that element is added to the global session state of the session.</span></span> <span data-ttu-id="d28df-112">Toutefois, lorsque l’élément est exécuté, il est exécuté dans l’état de session du module.</span><span class="sxs-lookup"><span data-stu-id="d28df-112">However, when the element is run, it is executed within the session state of the module.</span></span>

## <a name="session-state-data"></a><span data-ttu-id="d28df-113">Données Session-State</span><span class="sxs-lookup"><span data-stu-id="d28df-113">Session-State Data</span></span>

<span data-ttu-id="d28df-114">Les données d’état de session peuvent être publiques ou privées.</span><span class="sxs-lookup"><span data-stu-id="d28df-114">Session state data can be public or private.</span></span> <span data-ttu-id="d28df-115">Les données publiques sont disponibles pour les appels en dehors de l’état de session, tandis que les données privées sont uniquement disponibles pour les appels à partir de l’état de session.</span><span class="sxs-lookup"><span data-stu-id="d28df-115">Public data is available to calls from outside the session state while private data is available only to calls from within the session state.</span></span> <span data-ttu-id="d28df-116">Par exemple, un module peut avoir une fonction privée qui peut être appelée uniquement par le module ou uniquement en interne par un élément public qui a été exporté.</span><span class="sxs-lookup"><span data-stu-id="d28df-116">For example, a module can have a private function that can be called only by the module or only internally by a public element that has been exported.</span></span> <span data-ttu-id="d28df-117">Cela est similaire aux membres privés et publics d’un type de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d28df-117">This is similar to the private and public members of a .NET Framework type.</span></span>

<span data-ttu-id="d28df-118">Les données d’état de session sont stockées par l’instance actuelle du moteur d’exécution dans le contexte de la session Windows PowerShell actuelle.</span><span class="sxs-lookup"><span data-stu-id="d28df-118">Session-state data is stored by the current instance of the execution engine within the context of the current Windows PowerShell session.</span></span> <span data-ttu-id="d28df-119">Les données d’état de session se composent des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="d28df-119">Session-state data consists of the following items:</span></span>

- <span data-ttu-id="d28df-120">Informations sur le chemin</span><span class="sxs-lookup"><span data-stu-id="d28df-120">Path information</span></span>

- <span data-ttu-id="d28df-121">Informations sur le lecteur</span><span class="sxs-lookup"><span data-stu-id="d28df-121">Drive information</span></span>

- <span data-ttu-id="d28df-122">Informations sur le fournisseur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d28df-122">Windows PowerShell provider information</span></span>

- <span data-ttu-id="d28df-123">Informations sur les modules importés et les références aux éléments de module (tels que les applets de commande, les fonctions et les scripts) qui sont exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="d28df-123">Information about the imported modules and references to the module elements (such as cmdlets, functions, and scripts) that are exported by the module.</span></span> <span data-ttu-id="d28df-124">Ces informations et ces références concernent uniquement l’état de session global.</span><span class="sxs-lookup"><span data-stu-id="d28df-124">This information and these references are for the global session state only.</span></span>

- <span data-ttu-id="d28df-125">Informations sur les variables d’état de session</span><span class="sxs-lookup"><span data-stu-id="d28df-125">Session-state variable information</span></span>

## <a name="accessing-session-state-data-within-cmdlets"></a><span data-ttu-id="d28df-126">Accès aux données Session-State dans les applets de commande</span><span class="sxs-lookup"><span data-stu-id="d28df-126">Accessing Session-State Data Within Cmdlets</span></span>

<span data-ttu-id="d28df-127">Les applets de commande peuvent accéder aux données d’état de session, soit indirectement par le biais de la propriété [System. Management. Automation. PSCmdlet. SessionState \*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) de la classe cmdlet, soit directement via la classe [System. Management. Automation. SessionState](/dotnet/api/System.Management.Automation.SessionState) .</span><span class="sxs-lookup"><span data-stu-id="d28df-127">Cmdlets can access session-state data either indirectly through the [System.Management.Automation.PSCmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) property of the cmdlet class or directly through the [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class.</span></span> <span data-ttu-id="d28df-128">La classe [System. Management. Automation. SessionState](/dotnet/api/System.Management.Automation.SessionState) fournit des propriétés qui peuvent être utilisées pour examiner les différents types de données d’état de session.</span><span class="sxs-lookup"><span data-stu-id="d28df-128">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class provides properties that can be used to investigate different types of session-state data.</span></span>

## <a name="see-also"></a><span data-ttu-id="d28df-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d28df-129">See Also</span></span>

[<span data-ttu-id="d28df-130">System. Management. Automation. PSCmdlet. SessionState</span><span class="sxs-lookup"><span data-stu-id="d28df-130">System.Management.Automation.PSCmdlet.Sessionstate</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[<span data-ttu-id="d28df-131">System. Management. Automation. SessionState ? Displayproperty = FullName</span><span class="sxs-lookup"><span data-stu-id="d28df-131">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span></span>](/dotnet/api/System.Management.Automation.SessionState)

[<span data-ttu-id="d28df-132">Applets de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d28df-132">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="d28df-133">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d28df-133">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="d28df-134">Kit SDK Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d28df-134">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
