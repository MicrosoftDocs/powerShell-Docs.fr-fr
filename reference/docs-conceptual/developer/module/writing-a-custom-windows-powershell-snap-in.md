---
title: Écriture d’un composant logiciel enfichable Windows PowerShell personnalisé | Microsoft Docs
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
ms.openlocfilehash: 9cf4499ec2992c6cfea83fc5d0bf51d0bbfaa96a
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811628"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a><span data-ttu-id="0dc88-102">Écriture d’un composant logiciel enfichable Windows PowerShell personnalisé</span><span class="sxs-lookup"><span data-stu-id="0dc88-102">Writing a Custom Windows PowerShell Snap-in</span></span>

<span data-ttu-id="0dc88-103">Cet exemple montre comment écrire un composant logiciel enfichable Windows PowerShell qui inscrit des applets de commande spécifiques.</span><span class="sxs-lookup"><span data-stu-id="0dc88-103">This example shows how to write a Windows PowerShell snap-in that registers specific cmdlets.</span></span>

<span data-ttu-id="0dc88-104">Avec ce type de composant logiciel enfichable, vous spécifiez les applets de commande, fournisseurs, types ou formats à inscrire.</span><span class="sxs-lookup"><span data-stu-id="0dc88-104">With this type of snap-in, you specify which cmdlets, providers, types, or formats to register.</span></span> <span data-ttu-id="0dc88-105">Pour plus d’informations sur l’écriture d’un composant logiciel enfichable qui inscrit toutes les applets de commande et tous les fournisseurs dans un assembly, consultez [écriture d’un composant logiciel enfichable Windows PowerShell](./writing-a-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="0dc88-105">For more information about how to write a snap-in that registers all the cmdlets and providers in an assembly, see [Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md).</span></span>

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a><span data-ttu-id="0dc88-106">Pour écrire un composant logiciel enfichable Windows PowerShell qui inscrit des applets de commande spécifiques.</span><span class="sxs-lookup"><span data-stu-id="0dc88-106">To write a Windows PowerShell Snap-in that registers specific cmdlets.</span></span>

1. <span data-ttu-id="0dc88-107">Ajoutez l’attribut RunInstallerAttribute.</span><span class="sxs-lookup"><span data-stu-id="0dc88-107">Add the RunInstallerAttribute attribute.</span></span>
2. <span data-ttu-id="0dc88-108">Créez une classe publique qui dérive de la classe [System. Management. Automation. CustomPSSnapIn](/dotnet/api/System.Management.Automation.CustomPSSnapIn) .</span><span class="sxs-lookup"><span data-stu-id="0dc88-108">Create a public class that derives from the [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) class.</span></span>

   <span data-ttu-id="0dc88-109">Dans cet exemple, le nom de la classe est « CustomPSSnapinTest ».</span><span class="sxs-lookup"><span data-stu-id="0dc88-109">In this example, the class name is "CustomPSSnapinTest".</span></span>

3. <span data-ttu-id="0dc88-110">Ajoutez une propriété publique pour le nom du composant logiciel enfichable (obligatoire).</span><span class="sxs-lookup"><span data-stu-id="0dc88-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="0dc88-111">Quand vous nommez des composants logiciels enfichables, n’utilisez pas les caractères suivants : `#` ,,,, `.` `,` `(` `)` , `{` , `}` , `[` , `]` , `&` , `-` , `/` , `\` , `$` , `;` , `:` ,,,,,,,,,,,,,,, `"` , `'` ,,, `<` `>` `|` , `?` , `@` , `` ` `` ,`*`</span><span class="sxs-lookup"><span data-stu-id="0dc88-111">When naming snap-ins, do not use any of the following characters: `#`, `.`, `,`, `(`, `)`, `{`, `}`, `[`, `]`, `&`, `-`, `/`, `\`, `$`, `;`, `:`, `"`, `'`, `<`, `>`, `|`, `?`, `@`, `` ` ``, `*`</span></span>

   <span data-ttu-id="0dc88-112">Dans cet exemple, le nom du composant logiciel enfichable est « CustomPSSnapInTest ».</span><span class="sxs-lookup"><span data-stu-id="0dc88-112">In this example, the name of the snap-in is "CustomPSSnapInTest".</span></span>

4. <span data-ttu-id="0dc88-113">Ajoutez une propriété publique pour le fournisseur du composant logiciel enfichable (obligatoire).</span><span class="sxs-lookup"><span data-stu-id="0dc88-113">Add a public property for the vendor of the snap-in (required).</span></span>

   <span data-ttu-id="0dc88-114">Dans cet exemple, le fournisseur est « Microsoft ».</span><span class="sxs-lookup"><span data-stu-id="0dc88-114">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="0dc88-115">Ajoutez une propriété publique pour la ressource fournisseur du composant logiciel enfichable (facultatif).</span><span class="sxs-lookup"><span data-stu-id="0dc88-115">Add a public property for the vendor resource of the snap-in (optional).</span></span>

   <span data-ttu-id="0dc88-116">Dans cet exemple, la ressource Vendor est « CustomPSSnapInTest, Microsoft ».</span><span class="sxs-lookup"><span data-stu-id="0dc88-116">In this example, the vendor resource is "CustomPSSnapInTest,Microsoft".</span></span>

6. <span data-ttu-id="0dc88-117">Ajoutez une propriété publique pour la description du composant logiciel enfichable (obligatoire).</span><span class="sxs-lookup"><span data-stu-id="0dc88-117">Add a public property for the description of the snap-in (required).</span></span>

   <span data-ttu-id="0dc88-118">Dans cet exemple, la description est : « il s’agit d’un composant logiciel enfichable Windows PowerShell personnalisé qui comprend les `Test-HelloWorld` applets de commande et `Test-CustomSnapinTest` ».</span><span class="sxs-lookup"><span data-stu-id="0dc88-118">In this example, the description is: "This is a custom Windows PowerShell snap-in that includes the `Test-HelloWorld` and `Test-CustomSnapinTest` cmdlets".</span></span>

7. <span data-ttu-id="0dc88-119">Ajoutez une propriété publique pour la ressource Description du composant logiciel enfichable (facultatif).</span><span class="sxs-lookup"><span data-stu-id="0dc88-119">Add a public property for the description resource of the snap-in (optional).</span></span>

   <span data-ttu-id="0dc88-120">Dans cet exemple, la ressource Vendor est :</span><span class="sxs-lookup"><span data-stu-id="0dc88-120">In this example, the vendor resource is:</span></span>

   > <span data-ttu-id="0dc88-121">CustomPSSnapInTest, il s’agit d’un composant logiciel enfichable Windows PowerShell personnalisé qui comprend les applets de commande test-HelloWorld et test-CustomSnapinTest».</span><span class="sxs-lookup"><span data-stu-id="0dc88-121">CustomPSSnapInTest, This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

8. <span data-ttu-id="0dc88-122">Spécifiez les applets de commande qui appartiennent au composant logiciel enfichable personnalisé (facultatif) à l’aide de la classe [System. Management. Automation. instances d’exécution. Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) .</span><span class="sxs-lookup"><span data-stu-id="0dc88-122">Specify the cmdlets that belong to the custom snap-in (optional) using the [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) class.</span></span> <span data-ttu-id="0dc88-123">Les informations ajoutées ici incluent le nom de l’applet de commande, son type .NET et le nom du fichier d’aide de l’applet de commande (le format du nom du fichier d’aide de l’applet de commande doit être `name.dll-help.xml` ).</span><span class="sxs-lookup"><span data-stu-id="0dc88-123">The information added here includes the name of the cmdlet, its .NET type, and the cmdlet Help file name (the format of the cmdlet Help file name should be `name.dll-help.xml`).</span></span>

   <span data-ttu-id="0dc88-124">Cet exemple ajoute les applets de commande test-HelloWorld et TestCustomSnapinTest.</span><span class="sxs-lookup"><span data-stu-id="0dc88-124">This example adds the Test-HelloWorld and TestCustomSnapinTest cmdlets.</span></span>

9. <span data-ttu-id="0dc88-125">Spécifiez les fournisseurs qui appartiennent au composant logiciel enfichable personnalisé (facultatif).</span><span class="sxs-lookup"><span data-stu-id="0dc88-125">Specify the providers that belong to the custom snap-in (optional).</span></span>

   <span data-ttu-id="0dc88-126">Cet exemple ne spécifie aucun fournisseur.</span><span class="sxs-lookup"><span data-stu-id="0dc88-126">This example does not specify any providers.</span></span>

10. <span data-ttu-id="0dc88-127">Spécifiez les types qui appartiennent au composant logiciel enfichable personnalisé (facultatif).</span><span class="sxs-lookup"><span data-stu-id="0dc88-127">Specify the types that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="0dc88-128">Cet exemple ne spécifie aucun type.</span><span class="sxs-lookup"><span data-stu-id="0dc88-128">This example does not specify any types.</span></span>

11. <span data-ttu-id="0dc88-129">Spécifiez les formats qui appartiennent au composant logiciel enfichable personnalisé (facultatif).</span><span class="sxs-lookup"><span data-stu-id="0dc88-129">Specify the formats that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="0dc88-130">Cet exemple ne spécifie aucun format.</span><span class="sxs-lookup"><span data-stu-id="0dc88-130">This example does not specify any formats.</span></span>

## <a name="example"></a><span data-ttu-id="0dc88-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="0dc88-131">Example</span></span>

<span data-ttu-id="0dc88-132">Cet exemple montre comment écrire un composant logiciel enfichable Windows PowerShell personnalisé qui peut être utilisé pour inscrire les `Test-HelloWorld` applets de commande et `Test-CustomSnapinTest` .</span><span class="sxs-lookup"><span data-stu-id="0dc88-132">This example shows how to write a Custom Windows PowerShell snap-in that can be used to register the `Test-HelloWorld` and `Test-CustomSnapinTest` cmdlets.</span></span> <span data-ttu-id="0dc88-133">Sachez que dans cet exemple, l’assembly complet peut contenir d’autres applets de commande et fournisseurs qui ne seraient pas inscrits par ce composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="0dc88-133">Be aware that in this example, the complete assembly could contain other cmdlets and providers that would not be registered by this snap-in.</span></span>

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

<span data-ttu-id="0dc88-134">Pour plus d’informations sur l’inscription des composants logiciels enfichables, consultez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions/ms714644(v=vs.85)) dans le [Guide du programmeur Windows PowerShell](../prog-guide/windows-powershell-programmer-s-guide.md).</span><span class="sxs-lookup"><span data-stu-id="0dc88-134">For more information about registering snap-ins, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85)) in the [Windows PowerShell Programmer's Guide](../prog-guide/windows-powershell-programmer-s-guide.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0dc88-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0dc88-135">See Also</span></span>

<span data-ttu-id="0dc88-136">[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions/ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="0dc88-136">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85))</span></span>

[<span data-ttu-id="0dc88-137">Kit de développement logiciel Windows PowerShell Shell</span><span class="sxs-lookup"><span data-stu-id="0dc88-137">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
