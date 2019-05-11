---
title: Méthodes de traitement des entrées d’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- virtual methods (PowerShell SDK]
ms.assetid: b0bb8172-c9fa-454b-9f1b-57c3fe60671b
caps.latest.revision: 12
ms.openlocfilehash: a28c8d3df19bc72bf338d6abc4e02768c5097209
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670307"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="82c85-102">Méthodes de traitement des entrées des applets de commande</span><span class="sxs-lookup"><span data-stu-id="82c85-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="82c85-103">Applets de commande doit remplacer une ou plusieurs des méthodes décrites dans cette rubrique pour effectuer leur travail de traitement d’entrée.</span><span class="sxs-lookup"><span data-stu-id="82c85-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span>
<span data-ttu-id="82c85-104">Ces méthodes permettent de l’applet de commande effectuer des opérations de prétraitement, traitement d’entrée et de post-traitement.</span><span class="sxs-lookup"><span data-stu-id="82c85-104">These methods allow the cmdlet to perform operations of pre-processing, input processing, and post-processing.</span></span>
<span data-ttu-id="82c85-105">Ces méthodes vous permettent également d’arrêter le traitement de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="82c85-105">These methods also allow you to stop cmdlet processing.</span></span>
<span data-ttu-id="82c85-106">Pour obtenir un exemple plus détaillé de l’utilisation de ces méthodes, consultez [SelectStr didacticiel](selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="82c85-106">For a more detailed example of how to use these methods, see [SelectStr Tutorial](selectstr-tutorial.md).</span></span>

## <a name="pre-processing-operations"></a><span data-ttu-id="82c85-107">Opérations de prétraitement</span><span class="sxs-lookup"><span data-stu-id="82c85-107">Pre-Processing Operations</span></span>

<span data-ttu-id="82c85-108">Applets de commande doit remplacer le [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) méthode pour ajouter des opérations de prétraitement sont valides pour tous les enregistrements qui seront traités ultérieurement par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="82c85-108">Cmdlets should override the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span>
<span data-ttu-id="82c85-109">Lorsque PowerShell traite un pipeline de commande, PowerShell appelle cette méthode une fois pour chaque instance de l’applet de commande dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="82c85-109">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="82c85-110">Pour plus d’informations sur la façon dont PowerShell appelle le pipeline de commande, consultez [cycle de vie du traitement d’applet de commande](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="82c85-110">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="82c85-111">Le code suivant illustre une implémentation de la méthode BeginProcessing.</span><span class="sxs-lookup"><span data-stu-id="82c85-111">The following code shows an implementation of the BeginProcessing method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a><span data-ttu-id="82c85-112">Traitement des opérations d’entrée</span><span class="sxs-lookup"><span data-stu-id="82c85-112">Input Processing Operations</span></span>

<span data-ttu-id="82c85-113">Applets de commande peut remplacer le [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) méthode pour traiter l’entrée qui est envoyée à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="82c85-113">Cmdlets can override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the input that is sent to the cmdlet.</span></span>
<span data-ttu-id="82c85-114">Lorsque PowerShell traite un pipeline de commande, PowerShell appelle cette méthode pour chaque enregistrement d’entrée qui est traité par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="82c85-114">When PowerShell processes a command pipeline, PowerShell calls this method for each input record that is processed by the cmdlet.</span></span>
<span data-ttu-id="82c85-115">Pour plus d’informations sur la façon dont PowerShell appelle le pipeline de commande, consultez [cycle de vie du traitement d’applet de commande](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="82c85-115">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="82c85-116">Le code suivant illustre une implémentation de la méthode ProcessRecord.</span><span class="sxs-lookup"><span data-stu-id="82c85-116">The following code shows an implementation of the ProcessRecord method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a><span data-ttu-id="82c85-117">Opérations post-traitement</span><span class="sxs-lookup"><span data-stu-id="82c85-117">Post-Processing Operations</span></span>

<span data-ttu-id="82c85-118">Applets de commande doit remplacer le [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) méthode pour ajouter toutes les opérations post-traitement qui sont valides pour tous les enregistrements qui ont été traités par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="82c85-118">Cmdlets should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span>
<span data-ttu-id="82c85-119">Par exemple, votre applet de commande peut avoir nettoyer les variables d’objet après la fin de l’installation de traitement.</span><span class="sxs-lookup"><span data-stu-id="82c85-119">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="82c85-120">Lorsque PowerShell traite un pipeline de commande, PowerShell appelle cette méthode une fois pour chaque instance de l’applet de commande dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="82c85-120">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="82c85-121">Toutefois, il est important de se rappeler que le runtime PowerShell n’appelle pas la méthode EndProcessing si l’applet de commande est annulée à mi-chemin via son traitement d’entrée ou si une erreur avec fin d’exécution se produit dans n’importe quelle partie de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="82c85-121">However, it is important to remember that the PowerShell runtime will not call the EndProcessing method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span>
<span data-ttu-id="82c85-122">Pour cette raison, une applet de commande qui requiert un nettoyage de l’objet doit implémenter l’ensemble [System.IDisposable](/dotnet/api/System.IDisposable) modèle, y compris un finaliseur, afin que le runtime peut appeler à la fois le EndProcessing et [ System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) méthodes à la fin du traitement.</span><span class="sxs-lookup"><span data-stu-id="82c85-122">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the EndProcessing and [System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>
<span data-ttu-id="82c85-123">Pour plus d’informations sur la façon dont PowerShell appelle le pipeline de commande, consultez [cycle de vie du traitement d’applet de commande](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="82c85-123">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="82c85-124">Le code suivant illustre une implémentation de la méthode EndProcessing.</span><span class="sxs-lookup"><span data-stu-id="82c85-124">The following code shows an implementation of the EndProcessing method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a><span data-ttu-id="82c85-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82c85-125">See Also</span></span>

[<span data-ttu-id="82c85-126">System.Management.Automation.Cmdlet.BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="82c85-126">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="82c85-127">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="82c85-127">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="82c85-128">System.Management.Automation.Cmdlet.EndProcessing</span><span class="sxs-lookup"><span data-stu-id="82c85-128">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="82c85-129">Didacticiel de SelectStr</span><span class="sxs-lookup"><span data-stu-id="82c85-129">SelectStr Tutorial</span></span>](selectstr-tutorial.md)

[<span data-ttu-id="82c85-130">System.IDisposable</span><span class="sxs-lookup"><span data-stu-id="82c85-130">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="82c85-131">Interpréteur de commandes Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="82c85-131">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
