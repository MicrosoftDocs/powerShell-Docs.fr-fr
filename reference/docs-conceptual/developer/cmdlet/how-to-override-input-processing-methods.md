---
ms.date: 09/13/2016
ms.topic: reference
title: Guide pratique pour remplacer des méthodes de traitement des entrées
description: Guide pratique pour remplacer des méthodes de traitement des entrées
ms.openlocfilehash: 4e8d71a34a1480ce63435ac6cc5dce60d4219c03
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667009"
---
# <a name="how-to-override-input-processing-methods"></a><span data-ttu-id="1655f-103">Guide pratique pour remplacer des méthodes de traitement des entrées</span><span class="sxs-lookup"><span data-stu-id="1655f-103">How to Override Input Processing Methods</span></span>

<span data-ttu-id="1655f-104">Ces exemples montrent comment remplacer les méthodes de traitement d’entrée au sein d’une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1655f-104">These examples show how to overwrite the input processing methods within a cmdlet.</span></span> <span data-ttu-id="1655f-105">Ces méthodes sont utilisées pour effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="1655f-105">These methods are used to perform the following operations:</span></span>

- <span data-ttu-id="1655f-106">La méthode [System. Management. Automation. applet de commande. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) est utilisée pour effectuer des opérations de démarrage à usage unique qui sont valides pour tous les objets traités par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1655f-106">The [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method is used to perform one-time startup operations that are valid for all the objects processed by the cmdlet.</span></span> <span data-ttu-id="1655f-107">Le runtime Windows PowerShell appelle cette méthode une seule fois.</span><span class="sxs-lookup"><span data-stu-id="1655f-107">The Windows PowerShell runtime calls this method only once.</span></span>

- <span data-ttu-id="1655f-108">La méthode [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) est utilisée pour traiter les objets passés à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1655f-108">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is used to process the objects passed to the cmdlet.</span></span> <span data-ttu-id="1655f-109">Le runtime Windows PowerShell appelle cette méthode pour chaque objet passé à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1655f-109">The Windows PowerShell runtime calls this method for each object passed to the cmdlet.</span></span>

- <span data-ttu-id="1655f-110">La méthode [System. Management. Automation. applet de commande. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) est utilisée pour effectuer des opérations de validation unique.</span><span class="sxs-lookup"><span data-stu-id="1655f-110">The [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method is used to perform one-time post processing operations.</span></span> <span data-ttu-id="1655f-111">Le runtime Windows PowerShell appelle cette méthode une seule fois.</span><span class="sxs-lookup"><span data-stu-id="1655f-111">The Windows PowerShell runtime calls this method only once.</span></span>

## <a name="to-override-the-beginprocessing-method"></a><span data-ttu-id="1655f-112">Pour substituer la méthode BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="1655f-112">To override the BeginProcessing method</span></span>

- <span data-ttu-id="1655f-113">Déclarez une substitution protégée de la méthode [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) de commande. BeginProcessing.</span><span class="sxs-lookup"><span data-stu-id="1655f-113">Declare a protected override of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

<span data-ttu-id="1655f-114">La classe suivante affiche un exemple de message.</span><span class="sxs-lookup"><span data-stu-id="1655f-114">The following class prints a sample message.</span></span> <span data-ttu-id="1655f-115">Pour utiliser cette classe, modifiez le verbe et le nom dans l’attribut de l’applet de commande, modifiez le nom de la classe pour refléter le nouveau verbe et le nom, puis ajoutez la fonctionnalité dont vous avez besoin à la substitution de la méthode [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) de commande. BeginProcessing.</span><span class="sxs-lookup"><span data-stu-id="1655f-115">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "BeginProcessingClass")]
public class TestBeginProcessingClassTemplate : Cmdlet
{
  // Override the BeginProcessing method to add preprocessing
  //operations to the cmdlet.
  protected override void BeginProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the BeginProcessing template.");
  }
}
```

## <a name="to-override-the-processrecord-method"></a><span data-ttu-id="1655f-116">Pour substituer la méthode ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="1655f-116">To override the ProcessRecord method</span></span>

- <span data-ttu-id="1655f-117">Déclarez une substitution protégée de la méthode [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) de commande. ProcessRecord.</span><span class="sxs-lookup"><span data-stu-id="1655f-117">Declare a protected override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="1655f-118">La classe suivante affiche un exemple de message.</span><span class="sxs-lookup"><span data-stu-id="1655f-118">The following class prints a sample message.</span></span> <span data-ttu-id="1655f-119">Pour utiliser cette classe, modifiez le verbe et le nom dans l’attribut de l’applet de commande, modifiez le nom de la classe pour refléter le nouveau verbe et le nom, puis ajoutez la fonctionnalité dont vous avez besoin à la substitution de la méthode [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) de commande. ProcessRecord.</span><span class="sxs-lookup"><span data-stu-id="1655f-119">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "ProcessRecordClass")]
public class TestProcessRecordClassTemplate : Cmdlet
{
    // Override the ProcessRecord method to add processing
    //operations to the cmdlet.
    protected override void ProcessRecord()
    {
        // Replace the WriteObject method with the logic required
        // by your cmdlet. It is used here to generate the following
        // output:
        // "This is a test of the ProcessRecord template."
        WriteObject("This is a test of the ProcessRecord template.");
    }
}

```

## <a name="to-override-the-endprocessing-method"></a><span data-ttu-id="1655f-120">Pour substituer la méthode EndProcessing</span><span class="sxs-lookup"><span data-stu-id="1655f-120">To override the EndProcessing method</span></span>

- <span data-ttu-id="1655f-121">Déclarez une substitution protégée de la méthode [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) de commande. EndProcessing.</span><span class="sxs-lookup"><span data-stu-id="1655f-121">Declare a protected override of the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

<span data-ttu-id="1655f-122">La classe suivante imprime un exemple.</span><span class="sxs-lookup"><span data-stu-id="1655f-122">The following class prints a sample.</span></span> <span data-ttu-id="1655f-123">Pour utiliser cette classe, modifiez le verbe et le nom dans l’attribut de l’applet de commande, modifiez le nom de la classe pour refléter le nouveau verbe et le nom, puis ajoutez la fonctionnalité dont vous avez besoin à la substitution de la méthode [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) de commande. EndProcessing.</span><span class="sxs-lookup"><span data-stu-id="1655f-123">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "EndProcessingClass")]
public class TestEndProcessingClassTemplate : Cmdlet
{
  // Override the EndProcessing method to add postprocessing
  //operations to the cmdlet.
  protected override void EndProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the EndProcessing template.");
  }
}
```

## <a name="see-also"></a><span data-ttu-id="1655f-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1655f-124">See Also</span></span>

[<span data-ttu-id="1655f-125">System. Management. Automation. applet de commande. BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="1655f-125">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="1655f-126">System. Management. Automation. applet de commande. EndProcessing</span><span class="sxs-lookup"><span data-stu-id="1655f-126">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="1655f-127">System. Management. Automation. applet de commande. ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="1655f-127">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="1655f-128">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1655f-128">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
