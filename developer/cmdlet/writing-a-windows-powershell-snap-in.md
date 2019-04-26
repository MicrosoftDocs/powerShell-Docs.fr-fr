---
title: Écriture d’un composant logiciel enfichable PowerShell Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], PSSnapin example
ms.assetid: 875024f4-e02b-4416-80b9-af5e5b50aad6
caps.latest.revision: 7
ms.openlocfilehash: 0c99f4bcfe5e2d34d31714dc85a53b5e8abe0925
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066955"
---
# <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="e0393-102">Écriture d’un composant logiciel enfichable Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e0393-102">Writing a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="e0393-103">Cet exemple montre comment écrire un composant logiciel enfichable Windows PowerShell qui peut être utilisé pour enregistrer toutes les applets de commande et les fournisseurs Windows PowerShell dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="e0393-103">This example shows how to write a Windows PowerShell snap-in that can be used to register all the cmdlets and Windows PowerShell providers in an assembly.</span></span>

<span data-ttu-id="e0393-104">Avec ce type de composant logiciel enfichable, vous ne sélectionnez pas les applets de commande et les fournisseurs que vous souhaitez inscrire.</span><span class="sxs-lookup"><span data-stu-id="e0393-104">With this type of snap-in, you do not select which cmdlets and providers you want to register.</span></span> <span data-ttu-id="e0393-105">Pour écrire un composant logiciel enfichable qui vous permet de sélectionner ce qui est inscrit, consultez [écrire un personnalisé Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="e0393-105">To write a snap-in that allows you to select what is registered, see [Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span></span>

### <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="e0393-106">Écriture d’un composant logiciel enfichable Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e0393-106">Writing a Windows PowerShell Snap-in</span></span>

1. <span data-ttu-id="e0393-107">Ajoutez l’attribut RunInstallerAttribute.</span><span class="sxs-lookup"><span data-stu-id="e0393-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="e0393-108">Créez une classe publique qui dérive de la [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) classe.</span><span class="sxs-lookup"><span data-stu-id="e0393-108">Create a public class that derives from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) class.</span></span>

    <span data-ttu-id="e0393-109">Dans cet exemple, le nom de classe est « GetProcPSSnapIn01 ».</span><span class="sxs-lookup"><span data-stu-id="e0393-109">In this example, the class name is "GetProcPSSnapIn01".</span></span>

3. <span data-ttu-id="e0393-110">Ajouter une propriété publique pour le nom du composant logiciel enfichable (obligatoire).</span><span class="sxs-lookup"><span data-stu-id="e0393-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="e0393-111">Lorsque vous nommez des composants logiciel enfichables, n’utilisez pas les caractères suivants : #.</span><span class="sxs-lookup"><span data-stu-id="e0393-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="e0393-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span><span class="sxs-lookup"><span data-stu-id="e0393-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span></span> <span data-ttu-id="e0393-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="e0393-113">@ \` \*</span></span>

    <span data-ttu-id="e0393-114">Dans cet exemple, le nom du composant logiciel enfichable est « GetProcPSSnapIn01 ».</span><span class="sxs-lookup"><span data-stu-id="e0393-114">In this example, the name of the snap-in is "GetProcPSSnapIn01".</span></span>

4. <span data-ttu-id="e0393-115">Ajouter une propriété publique pour le fournisseur du composant logiciel enfichable (obligatoire).</span><span class="sxs-lookup"><span data-stu-id="e0393-115">Add a public property for the vendor of the snap-in (required).</span></span>

    <span data-ttu-id="e0393-116">Dans cet exemple, le fournisseur est « Microsoft ».</span><span class="sxs-lookup"><span data-stu-id="e0393-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="e0393-117">Ajouter une propriété publique pour la ressource du fournisseur du composant logiciel enfichable (facultatif).</span><span class="sxs-lookup"><span data-stu-id="e0393-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

    <span data-ttu-id="e0393-118">Dans cet exemple, la ressource de fournisseur est « GetProcPSSnapIn01, Microsoft ».</span><span class="sxs-lookup"><span data-stu-id="e0393-118">In this example, the vendor resource is "GetProcPSSnapIn01,Microsoft".</span></span>

6. <span data-ttu-id="e0393-119">Ajouter une propriété publique pour la description du composant logiciel enfichable en (obligatoire).</span><span class="sxs-lookup"><span data-stu-id="e0393-119">Add a public property for the description of the snap-in (required).</span></span>

    <span data-ttu-id="e0393-120">Dans cet exemple, la description est « Est un composant logiciel enfichable Windows PowerShell qui inscrit l’applet de commande get-Process ».</span><span class="sxs-lookup"><span data-stu-id="e0393-120">In this example, the description is "This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

7. <span data-ttu-id="e0393-121">Ajouter une propriété publique pour la ressource de description du composant logiciel enfichable (facultatif).</span><span class="sxs-lookup"><span data-stu-id="e0393-121">Add a public property for the description resource of the snap-in (optional).</span></span>

    <span data-ttu-id="e0393-122">Dans cet exemple, la ressource de fournisseur est « GetProcPSSnapIn01, ceci est un composant logiciel enfichable Windows PowerShell qui inscrit l’applet de commande get-Process ».</span><span class="sxs-lookup"><span data-stu-id="e0393-122">In this example, the vendor resource is "GetProcPSSnapIn01,This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

## <a name="example"></a><span data-ttu-id="e0393-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="e0393-123">Example</span></span>

<span data-ttu-id="e0393-124">Cet exemple montre comment écrire un composant logiciel enfichable Windows PowerShell qui peut être utilisé pour inscrire l’applet de commande Get-Process dans l’interpréteur de commandes Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0393-124">This example shows how to write a Windows PowerShell snap-in that can be used to register the Get-Proc cmdlet in the Windows PowerShell shell.</span></span> <span data-ttu-id="e0393-125">N’oubliez pas que dans cet exemple, l’assembly complet contient uniquement la GetProcPSSnapIn01 classe snap-in et la classe d’applet de commande Get-Process.</span><span class="sxs-lookup"><span data-stu-id="e0393-125">Be aware that in this example, the complete assembly would contain only the GetProcPSSnapIn01 snap-in class and the Get-Proc cmdlet class.</span></span>

```csharp
[RunInstaller(true)]
public class GetProcPSSnapIn01 : PSSnapIn
{
  /// <summary>
  /// Create an instance of the GetProcPSSnapIn01 class.
  /// </summary>
  public GetProcPSSnapIn01()
         : base()
  {
  }

  /// <summary>
  /// Specify the name of the PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "GetProcPSSnapIn01";
    }
  }

  /// <summary>
  /// Specify the vendor for the PowerShell snap-in.
  /// </summary>
  public override string Vendor
  {
    get
    {
      return "Microsoft";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the vendor.
  /// Use the format: resourceBaseName,VendorName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
      return "GetProcPSSnapIn01,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the description.
  /// Use the format: resourceBaseName,Description.
  /// </summary>
  public override string DescriptionResource
  {
    get
    {
      return "GetProcPSSnapIn01,This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="e0393-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0393-126">See Also</span></span>

[<span data-ttu-id="e0393-127">Comment inscrire les applets de commande, fournisseurs et héberger des Applications</span><span class="sxs-lookup"><span data-stu-id="e0393-127">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="e0393-128">Interpréteur de commandes Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e0393-128">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
