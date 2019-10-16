---
title: Méthodes de traitement d’entrée des applets de commande | Microsoft Docs
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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369868"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="a21b1-102">Méthodes de traitement des entrées des applets de commande</span><span class="sxs-lookup"><span data-stu-id="a21b1-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="a21b1-103">Les applets de commande doivent remplacer une ou plusieurs des méthodes de traitement d’entrée décrites dans cette rubrique pour effectuer leur travail.</span><span class="sxs-lookup"><span data-stu-id="a21b1-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span>
<span data-ttu-id="a21b1-104">Ces méthodes permettent à l’applet de commande d’effectuer des opérations de pré-traitement, de traitement d’entrée et de traitement.</span><span class="sxs-lookup"><span data-stu-id="a21b1-104">These methods allow the cmdlet to perform operations of pre-processing, input processing, and post-processing.</span></span>
<span data-ttu-id="a21b1-105">Ces méthodes vous permettent également d’arrêter le traitement des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="a21b1-105">These methods also allow you to stop cmdlet processing.</span></span>
<span data-ttu-id="a21b1-106">Pour obtenir un exemple plus détaillé de l’utilisation de ces méthodes, consultez le [didacticiel SelectStr](selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="a21b1-106">For a more detailed example of how to use these methods, see [SelectStr Tutorial](selectstr-tutorial.md).</span></span>

## <a name="pre-processing-operations"></a><span data-ttu-id="a21b1-107">Opérations de prétraitement</span><span class="sxs-lookup"><span data-stu-id="a21b1-107">Pre-Processing Operations</span></span>

<span data-ttu-id="a21b1-108">Les applets de commande doivent remplacer la méthode [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) pour ajouter des opérations de prétraitement valides pour tous les enregistrements qui seront traités ultérieurement par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a21b1-108">Cmdlets should override the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span>
<span data-ttu-id="a21b1-109">Lorsque PowerShell traite un pipeline de commande, PowerShell appelle cette méthode une fois pour chaque instance de l’applet de commande dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="a21b1-109">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="a21b1-110">Pour plus d’informations sur la façon dont PowerShell appelle le pipeline de commande, consultez [cycle de vie du traitement des applets](/previous-versions/ms714429(v=vs.85))de commande.</span><span class="sxs-lookup"><span data-stu-id="a21b1-110">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="a21b1-111">Le code suivant illustre une implémentation de la méthode BeginProcessing.</span><span class="sxs-lookup"><span data-stu-id="a21b1-111">The following code shows an implementation of the BeginProcessing method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a><span data-ttu-id="a21b1-112">Opérations de traitement d’entrée</span><span class="sxs-lookup"><span data-stu-id="a21b1-112">Input Processing Operations</span></span>

<span data-ttu-id="a21b1-113">Les applets de commande peuvent remplacer la méthode [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) pour traiter l’entrée envoyée à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a21b1-113">Cmdlets can override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the input that is sent to the cmdlet.</span></span>
<span data-ttu-id="a21b1-114">Lorsque PowerShell traite un pipeline de commande, PowerShell appelle cette méthode pour chaque enregistrement d’entrée traité par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a21b1-114">When PowerShell processes a command pipeline, PowerShell calls this method for each input record that is processed by the cmdlet.</span></span>
<span data-ttu-id="a21b1-115">Pour plus d’informations sur la façon dont PowerShell appelle le pipeline de commande, consultez [cycle de vie du traitement des applets](/previous-versions/ms714429(v=vs.85))de commande.</span><span class="sxs-lookup"><span data-stu-id="a21b1-115">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="a21b1-116">Le code suivant illustre une implémentation de la méthode ProcessRecord.</span><span class="sxs-lookup"><span data-stu-id="a21b1-116">The following code shows an implementation of the ProcessRecord method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a><span data-ttu-id="a21b1-117">Opérations de postérieure au traitement</span><span class="sxs-lookup"><span data-stu-id="a21b1-117">Post-Processing Operations</span></span>

<span data-ttu-id="a21b1-118">Les applets de commande doivent remplacer la méthode [System. Management. Automation. applet de commande. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) pour ajouter toutes les opérations de publication qui sont valides pour tous les enregistrements traités par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a21b1-118">Cmdlets should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span>
<span data-ttu-id="a21b1-119">Par exemple, votre applet de commande peut être obligée de nettoyer les variables d’objet une fois le traitement terminé.</span><span class="sxs-lookup"><span data-stu-id="a21b1-119">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="a21b1-120">Lorsque PowerShell traite un pipeline de commande, PowerShell appelle cette méthode une fois pour chaque instance de l’applet de commande dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="a21b1-120">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="a21b1-121">Toutefois, il est important de se souvenir que le runtime PowerShell n’appellera pas la méthode EndProcessing si l’applet de commande est annulée à mi-chemin dans son traitement d’entrée ou si une erreur d’arrêt se produit dans n’importe quelle partie de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a21b1-121">However, it is important to remember that the PowerShell runtime will not call the EndProcessing method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span>
<span data-ttu-id="a21b1-122">Pour cette raison, une applet de commande qui requiert le nettoyage d’objets doit implémenter le modèle [System. IDisposable](/dotnet/api/System.IDisposable) complet, y compris un finaliseur, afin que le runtime puisse appeler à la fois les méthodes EndProcessing et [System. IDisposable. dispose](/dotnet/api/System.IDisposable.Dispose) à la fin de traitée.</span><span class="sxs-lookup"><span data-stu-id="a21b1-122">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the EndProcessing and [System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>
<span data-ttu-id="a21b1-123">Pour plus d’informations sur la façon dont PowerShell appelle le pipeline de commande, consultez [cycle de vie du traitement des applets](/previous-versions/ms714429(v=vs.85))de commande.</span><span class="sxs-lookup"><span data-stu-id="a21b1-123">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="a21b1-124">Le code suivant illustre une implémentation de la méthode EndProcessing.</span><span class="sxs-lookup"><span data-stu-id="a21b1-124">The following code shows an implementation of the EndProcessing method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a><span data-ttu-id="a21b1-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a21b1-125">See Also</span></span>

[<span data-ttu-id="a21b1-126">System. Management. Automation. applet de commande. BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="a21b1-126">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="a21b1-127">System. Management. Automation. applet de commande. ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="a21b1-127">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="a21b1-128">System. Management. Automation. applet de commande. EndProcessing</span><span class="sxs-lookup"><span data-stu-id="a21b1-128">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="a21b1-129">Didacticiel SelectStr</span><span class="sxs-lookup"><span data-stu-id="a21b1-129">SelectStr Tutorial</span></span>](selectstr-tutorial.md)

[<span data-ttu-id="a21b1-130">System. IDisposable</span><span class="sxs-lookup"><span data-stu-id="a21b1-130">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="a21b1-131">Kit de développement logiciel Windows PowerShell Shell</span><span class="sxs-lookup"><span data-stu-id="a21b1-131">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
