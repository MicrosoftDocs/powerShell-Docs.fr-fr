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
ms.openlocfilehash: 065214647dfa6d376b727930fe75140911095faf
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059369"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="71be4-102">Méthodes de traitement des entrées des applets de commande</span><span class="sxs-lookup"><span data-stu-id="71be4-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="71be4-103">Applets de commande doit remplacer une ou plusieurs des méthodes décrites dans cette rubrique pour effectuer leur travail de traitement d’entrée.</span><span class="sxs-lookup"><span data-stu-id="71be4-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span> <span data-ttu-id="71be4-104">Ces méthodes permettent de l’applet de commande effectuer le prétraitement opérations d’entrée opérations et le traitement après les opérations de traitement.</span><span class="sxs-lookup"><span data-stu-id="71be4-104">These methods allow the cmdlet to perform pre-processing operations, input processing operations, and post-processing operations.</span></span> <span data-ttu-id="71be4-105">Ces méthodes vous permettent également d’arrêter le traitement de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="71be4-105">These methods also allow you to stop cmdlet processing.</span></span>

## <a name="pre-processing-tasks"></a><span data-ttu-id="71be4-106">Tâches de prétraitement</span><span class="sxs-lookup"><span data-stu-id="71be4-106">Pre-Processing Tasks</span></span>

<span data-ttu-id="71be4-107">Applets de commande doit remplacer le [System.Management.Automation.Cmdlet.Beginprocessing%2A ? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) méthode pour ajouter des opérations de prétraitement sont valides pour tous les enregistrements qui seront traités ultérieurement par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="71be4-107">Cmdlets should override the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span> <span data-ttu-id="71be4-108">Lorsque Windows PowerShell traite un pipeline de commande, Windows PowerShell appelle cette méthode une fois pour chaque instance de l’applet de commande dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="71be4-108">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span> <span data-ttu-id="71be4-109">Pour plus d’informations sur la façon dont Windows PowerShell appelle le pipeline de commande, consultez [cycle de vie du traitement d’applet de commande](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="71be4-109">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="71be4-110">Le code suivant illustre une implémentation de la [System.Management.Automation.Cmdlet.Beginprocessing%2A ? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) (méthode).</span><span class="sxs-lookup"><span data-stu-id="71be4-110">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the BeginProcessing template."
  WriteObject("This is a test of the BeginProcessing template.");
}
```

<span data-ttu-id="71be4-111">Pour obtenir un exemple plus détaillé de l’utilisation de la [System.Management.Automation.Cmdlet.Beginprocessing%2A ? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) (méthode), consultez [SelectStr didacticiel](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="71be4-111">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span> <span data-ttu-id="71be4-112">Dans ce didacticiel, le **sélectionnez-Str** applet de commande utilise le [System.Management.Automation.Cmdlet.Beginprocessing%2A ? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) méthode permettant de générer l’expression régulière qui est utilisée pour rechercher les enregistrements de traitement d’entrée.</span><span class="sxs-lookup"><span data-stu-id="71be4-112">In this tutorial, the **Select-Str** cmdlet uses the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method to generate the regular expression that is used to search the input processing records.</span></span>

## <a name="input-processing-tasks"></a><span data-ttu-id="71be4-113">Tâches de traitement d’entrée</span><span class="sxs-lookup"><span data-stu-id="71be4-113">Input Processing Tasks</span></span>

<span data-ttu-id="71be4-114">Applets de commande peut remplacer le [System.Management.Automation.Cmdlet.Processrecord%2A ? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) méthode pour traiter l’entrée qui est envoyée à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="71be4-114">Cmdlets can override the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method to process the input that is sent to the cmdlet.</span></span> <span data-ttu-id="71be4-115">Lorsque Windows PowerShell traite un pipeline de commande, Windows PowerShell appelle cette méthode pour chaque enregistrement d’entrée qui est traité par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="71be4-115">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method for each input record that is processed by the cmdlet.</span></span> <span data-ttu-id="71be4-116">Pour plus d’informations sur la façon dont Windows PowerShell appelle le pipeline de commande, consultez [cycle de vie du traitement d’applet de commande](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="71be4-116">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="71be4-117">Le code suivant illustre une implémentation de la [System.Management.Automation.Cmdlet.Processrecord%2A ? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) (méthode).</span><span class="sxs-lookup"><span data-stu-id="71be4-117">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the ProcessRecord template."
  WriteObject("This is a test of the ProcessRecord template.");
}
```

<span data-ttu-id="71be4-118">Pour obtenir un exemple plus détaillé de l’utilisation de la [System.Management.Automation.Cmdlet.Processrecord%2A ? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) (méthode), consultez [SelectStr didacticiel](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="71be4-118">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span>

## <a name="post-processing-tasks"></a><span data-ttu-id="71be4-119">Tâches de post-traitement</span><span class="sxs-lookup"><span data-stu-id="71be4-119">Post-Processing Tasks</span></span>

<span data-ttu-id="71be4-120">Applets de commande doit remplacer le [System.Management.Automation.Cmdlet.Endprocessing%2A ? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) méthode pour ajouter toutes les opérations post-traitement qui sont valides pour tous les enregistrements qui ont été traités par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="71be4-120">Cmdlets should override the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span> <span data-ttu-id="71be4-121">Par exemple, votre applet de commande peut avoir nettoyer les variables d’objet après la fin de l’installation de traitement.</span><span class="sxs-lookup"><span data-stu-id="71be4-121">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="71be4-122">Lorsque Windows PowerShell traite un pipeline de commande, Windows PowerShell appelle cette méthode une fois pour chaque instance de l’applet de commande dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="71be4-122">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span> <span data-ttu-id="71be4-123">Toutefois, il est important de se rappeler que le runtime Windows PowerShell n’appelle pas le [System.Management.Automation.Cmdlet.Endprocessing%2A ? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) méthode si l’applet de commande est annulée à mi-chemin via son traitement d’entrée ou si un arrêt de l’erreur se produit dans n’importe quelle partie de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="71be4-123">However, it is important to remember that the Windows PowerShell runtime will not call the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="71be4-124">Pour cette raison, une applet de commande qui requiert un nettoyage de l’objet doit implémenter l’ensemble [System.IDisposable](/dotnet/api/System.IDisposable) modèle, y compris un finaliseur, afin que le runtime peut appeler à la fois le [ System.Management.Automation.Cmdlet.Endprocessing%2A ? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) et [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) méthodes à la fin du traitement.</span><span class="sxs-lookup"><span data-stu-id="71be4-124">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span> <span data-ttu-id="71be4-125">Pour plus d’informations sur la façon dont Windows PowerShell appelle le pipeline de commande, consultez [cycle de vie du traitement d’applet de commande](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="71be4-125">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="71be4-126">Le code suivant illustre une implémentation de la [System.Management.Automation.Cmdlet.Processrecord%2A ? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) (méthode).</span><span class="sxs-lookup"><span data-stu-id="71be4-126">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the EndProcessing template."
  WriteObject("This is a test of the EndProcessing template.");
}
```

<span data-ttu-id="71be4-127">Pour obtenir un exemple plus détaillé de l’utilisation de la [System.Management.Automation.Cmdlet.Processrecord%2A ? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) (méthode), consultez [SelectStr didacticiel](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="71be4-127">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="71be4-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71be4-128">See Also</span></span>

[<span data-ttu-id="71be4-129">System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="71be4-129">System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)

[<span data-ttu-id="71be4-130">System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="71be4-130">System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)

[<span data-ttu-id="71be4-131">System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="71be4-131">System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)

[<span data-ttu-id="71be4-132">System.IDisposable</span><span class="sxs-lookup"><span data-stu-id="71be4-132">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="71be4-133">Interpréteur de commandes Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="71be4-133">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
