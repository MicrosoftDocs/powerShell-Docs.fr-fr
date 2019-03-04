---
title: Écriture d’un composant logiciel enfichable PowerShell Windows personnalisée | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], custom PSSnapin example
- cmdlets [PowerShell SDK], specified in snap-ins
ms.assetid: 55c8b5cb-8ee2-4080-afc4-3f09c9f20128
caps.latest.revision: 6
ms.openlocfilehash: 20b7fdce1d31e3dee4598a7595962fca1c99d80a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863345"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a><span data-ttu-id="2a876-102">Écriture d’un composant logiciel enfichable Windows PowerShell personnalisé</span><span class="sxs-lookup"><span data-stu-id="2a876-102">Writing a Custom Windows PowerShell Snap-in</span></span>

<span data-ttu-id="2a876-103">Cet exemple montre comment écrire un composant logiciel enfichable Windows PowerShell qui inscrit les applets de commande spécifique.</span><span class="sxs-lookup"><span data-stu-id="2a876-103">This example shows how to write a Windows PowerShell snap-in that registers specific cmdlets.</span></span>

<span data-ttu-id="2a876-104">Avec ce type de composant logiciel enfichable, vous spécifiez les applets de commande, les fournisseurs, les types ou les formats à inscrire.</span><span class="sxs-lookup"><span data-stu-id="2a876-104">With this type of snap-in, you specify which cmdlets, providers, types, or formats to register.</span></span> <span data-ttu-id="2a876-105">Pour plus d’informations sur l’écriture d’un composant logiciel enfichable qui enregistre toutes les applets de commande et les fournisseurs dans un assembly, consultez [écrire un Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="2a876-105">For more information about how to write a snap-in that registers all the cmdlets and providers in an assembly, see [Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md).</span></span>

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a><span data-ttu-id="2a876-106">Pour écrire un Windows PowerShell Snap-in qui inscrit les applets de commande spécifique.</span><span class="sxs-lookup"><span data-stu-id="2a876-106">To write a Windows PowerShell Snap-in that registers specific cmdlets.</span></span>

1. <span data-ttu-id="2a876-107">Ajoutez l’attribut RunInstallerAttribute.</span><span class="sxs-lookup"><span data-stu-id="2a876-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="2a876-108">Créez une classe publique qui dérive de la [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classe.</span><span class="sxs-lookup"><span data-stu-id="2a876-108">Create a public class that derives from the [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) class.</span></span>

   <span data-ttu-id="2a876-109">Dans cet exemple, le nom de classe est « CustomPSSnapinTest ».</span><span class="sxs-lookup"><span data-stu-id="2a876-109">In this example, the class name is "CustomPSSnapinTest".</span></span>

3. <span data-ttu-id="2a876-110">Ajouter une propriété publique pour le nom du composant logiciel enfichable (obligatoire).</span><span class="sxs-lookup"><span data-stu-id="2a876-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="2a876-111">Lorsque vous nommez des composants logiciel enfichables, n’utilisez pas les caractères suivants : #.</span><span class="sxs-lookup"><span data-stu-id="2a876-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="2a876-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ?</span><span class="sxs-lookup"><span data-stu-id="2a876-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ?</span></span> <span data-ttu-id="2a876-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="2a876-113">@ \` \*</span></span>

   <span data-ttu-id="2a876-114">Dans cet exemple, le nom du composant logiciel enfichable est « CustomPSSnapInTest ».</span><span class="sxs-lookup"><span data-stu-id="2a876-114">In this example, the name of the snap-in is "CustomPSSnapInTest".</span></span>

4. <span data-ttu-id="2a876-115">Ajouter une propriété publique pour le fournisseur du composant logiciel enfichable (obligatoire).</span><span class="sxs-lookup"><span data-stu-id="2a876-115">Add a public property for the vendor of the snap-in (required).</span></span>

   <span data-ttu-id="2a876-116">Dans cet exemple, le fournisseur est « Microsoft ».</span><span class="sxs-lookup"><span data-stu-id="2a876-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="2a876-117">Ajouter une propriété publique pour la ressource du fournisseur du composant logiciel enfichable (facultatif).</span><span class="sxs-lookup"><span data-stu-id="2a876-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

   <span data-ttu-id="2a876-118">Dans cet exemple, la ressource de fournisseur est « CustomPSSnapInTest, Microsoft ».</span><span class="sxs-lookup"><span data-stu-id="2a876-118">In this example, the vendor resource is "CustomPSSnapInTest,Microsoft".</span></span>

6. <span data-ttu-id="2a876-119">Ajouter une propriété publique pour la description du composant logiciel enfichable en (obligatoire).</span><span class="sxs-lookup"><span data-stu-id="2a876-119">Add a public property for the description of the snap-in (required).</span></span>

   <span data-ttu-id="2a876-120">Dans cet exemple, la description est : « Voici un personnalisé composant logiciel enfichable Windows PowerShell qui inclut les applets de commande Test-CustomSnapinTest Test-HelloWorld ».</span><span class="sxs-lookup"><span data-stu-id="2a876-120">In this example, the description is: "This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

7. <span data-ttu-id="2a876-121">Ajouter une propriété publique pour la ressource de description du composant logiciel enfichable (facultatif).</span><span class="sxs-lookup"><span data-stu-id="2a876-121">Add a public property for the description resource of the snap-in (optional).</span></span>

   <span data-ttu-id="2a876-122">Dans cet exemple, la ressource de fournisseur est « CustomPSSnapInTest, Voici un personnalisé composant logiciel enfichable Windows PowerShell qui inclut les applets de commande Test-HelloWorld et Test-CustomSnapinTest ».</span><span class="sxs-lookup"><span data-stu-id="2a876-122">In this example, the vendor resource is "CustomPSSnapInTest, This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

8. <span data-ttu-id="2a876-123">Spécifiez les applets de commande qui appartiennent au personnalisée enfichable (facultatif) en utilisant le [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) classe.</span><span class="sxs-lookup"><span data-stu-id="2a876-123">Specify the cmdlets that belong to the custom snap-in (optional) using the [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) class.</span></span> <span data-ttu-id="2a876-124">Les informations ajoutées ici incluent le nom de l’applet de commande, son type .NET et le nom de fichier applet de commande (le format du nom du fichier d’aide applet de commande doit être name.dll-help.xml).</span><span class="sxs-lookup"><span data-stu-id="2a876-124">The information added here includes the name of the cmdlet, its .NET type, and the cmdlet Help file name (the format of the cmdlet Help file name should be name.dll-help.xml).</span></span>

   <span data-ttu-id="2a876-125">Cet exemple ajoute les applets de commande Test-HelloWorld et TestCustomSnapinTest.</span><span class="sxs-lookup"><span data-stu-id="2a876-125">This example adds the Test-HelloWorld and TestCustomSnapinTest cmdlets.</span></span>

9. <span data-ttu-id="2a876-126">Spécifiez les fournisseurs qui appartiennent à l’enfichable personnalisé (facultatif).</span><span class="sxs-lookup"><span data-stu-id="2a876-126">Specify the providers that belong to the custom snap-in (optional).</span></span>

   <span data-ttu-id="2a876-127">Cet exemple ne spécifie pas de tous les fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="2a876-127">This example does not specify any providers.</span></span>

10. <span data-ttu-id="2a876-128">Spécifier les types qui appartiennent à l’enfichable personnalisé (facultatif).</span><span class="sxs-lookup"><span data-stu-id="2a876-128">Specify the types that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="2a876-129">Cet exemple ne spécifie pas de tous les types.</span><span class="sxs-lookup"><span data-stu-id="2a876-129">This example does not specify any types.</span></span>

11. <span data-ttu-id="2a876-130">Spécifier les formats qui appartiennent à l’enfichable personnalisé (facultatif).</span><span class="sxs-lookup"><span data-stu-id="2a876-130">Specify the formats that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="2a876-131">Cet exemple ne spécifie pas de tous les formats.</span><span class="sxs-lookup"><span data-stu-id="2a876-131">This example does not specify any formats.</span></span>

## <a name="example"></a><span data-ttu-id="2a876-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="2a876-132">Example</span></span>

<span data-ttu-id="2a876-133">Cet exemple montre comment écrire un composant logiciel enfichable personnalisé Windows PowerShell qui peut être utilisé pour inscrire les applets de commande Test-CustomSnapinTest Test-HelloWorld.</span><span class="sxs-lookup"><span data-stu-id="2a876-133">This example shows how to write a Custom Windows PowerShell snap-in that can be used to register the Test-HelloWorld and Test-CustomSnapinTest cmdlets.</span></span> <span data-ttu-id="2a876-134">N’oubliez pas que dans cet exemple, l’assembly complet peut contenir d’autres applets de commande et les fournisseurs qui ne peut pas être inscrit par ce composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="2a876-134">Be aware that in this example, the complete assembly could contain other cmdlets and providers that would not be registered by this snap-in.</span></span>

```csharp
[RunInstaller(true)]
public class CustomPSSnapinTest : CustomPSSnapIn
{
  /// <summary>
  /// Creates an instance of CustomPSSnapInTest class.
  /// </summary>
  public CustomPSSnapinTest()
          : base()
  {
  }

  /// <summary>
  /// Specify the name of the custom PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "CustomPSSnapInTest";
    }
  }

  /// <summary>
  /// Specify the vendor for the custom PowerShell snap-in.
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
  /// Use the format: resourceBaseName,resourceName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
        return "CustomPSSnapInTest,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the custom PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
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
        return "CustomPSSnapInTest,This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
    }
  }

  /// <summary>
  /// Specify the cmdlets that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<CmdletConfigurationEntry> _cmdlets;
  public override Collection<CmdletConfigurationEntry> Cmdlets
  {
    get
    {
      if (_cmdlets == null)
      {
        _cmdlets = new Collection<CmdletConfigurationEntry>();
        _cmdlets.Add(new CmdletConfigurationEntry("test-customsnapintest", typeof(TestCustomSnapinTest), "TestCmdletHelp.dll-help.xml"));
        _cmdlets.Add(new CmdletConfigurationEntry("test-helloworld", typeof(TestHelloWorld), "HelloWorldHelp.dll-help.xml"));
      }

      return _cmdlets;
    }
  }

  /// <summary>
  /// Specify the providers that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<ProviderConfigurationEntry> _providers;
  public override Collection<ProviderConfigurationEntry> Providers
  {
    get
    {
      if (_providers == null)
      {
        _providers = new Collection<ProviderConfigurationEntry>();
      }

      return _providers;
    }
  }

  /// <summary>
  /// Specify the types that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<TypeConfigurationEntry> _types;
  public override Collection<TypeConfigurationEntry> Types
  {
    get
    {
      if (_types == null)
      {
        _types = new Collection<TypeConfigurationEntry>();
      }

      return _types;
    }
  }

  /// <summary>
  /// Specify the formats that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<FormatConfigurationEntry> _formats;
  public override Collection<FormatConfigurationEntry> Formats
  {
    get
    {
      if (_formats == null)
      {
        _formats = new Collection<FormatConfigurationEntry>();
      }

      return _formats;
    }
  }
}
```

<span data-ttu-id="2a876-135">Pour plus d’informations sur l’inscription des composants logiciel enfichables, consultez [comment inscrire les applets de commande, fournisseurs et héberger des Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) dans le [-Guide du programmeur Windows PowerShell](../prog-guide/windows-powershell-programmer-s-guide.md).</span><span class="sxs-lookup"><span data-stu-id="2a876-135">For more information about registering snap-ins, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) in the [Windows PowerShell Programmer's Guide](../prog-guide/windows-powershell-programmer-s-guide.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2a876-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a876-136">See Also</span></span>

[<span data-ttu-id="2a876-137">Comment inscrire les applets de commande, fournisseurs et héberger des Applications</span><span class="sxs-lookup"><span data-stu-id="2a876-137">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="2a876-138">Comment inscrire les applets de commande, fournisseurs et héberger des Applications</span><span class="sxs-lookup"><span data-stu-id="2a876-138">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="2a876-139">Interpréteur de commandes Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="2a876-139">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
