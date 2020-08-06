---
title: Écriture d’un composant logiciel enfichable Windows PowerShell personnalisé | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- snap-ins [PowerShell SDK], custom PSSnapin example
- cmdlets [PowerShell SDK], specified in snap-ins
ms.openlocfilehash: 3672dcc2e962b6795888ab5be3d461380e379315
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779214"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a><span data-ttu-id="df58f-102">Écriture d’un composant logiciel enfichable Windows PowerShell personnalisé</span><span class="sxs-lookup"><span data-stu-id="df58f-102">Writing a Custom Windows PowerShell Snap-in</span></span>

<span data-ttu-id="df58f-103">Cet exemple montre comment écrire un composant logiciel enfichable Windows PowerShell qui inscrit des applets de commande spécifiques.</span><span class="sxs-lookup"><span data-stu-id="df58f-103">This example shows how to write a Windows PowerShell snap-in that registers specific cmdlets.</span></span>

<span data-ttu-id="df58f-104">Avec ce type de composant logiciel enfichable, vous spécifiez les applets de commande, fournisseurs, types ou formats à inscrire.</span><span class="sxs-lookup"><span data-stu-id="df58f-104">With this type of snap-in, you specify which cmdlets, providers, types, or formats to register.</span></span> <span data-ttu-id="df58f-105">Pour plus d’informations sur l’écriture d’un composant logiciel enfichable qui inscrit toutes les applets de commande et tous les fournisseurs dans un assembly, consultez [écriture d’un composant logiciel enfichable Windows PowerShell](./writing-a-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="df58f-105">For more information about how to write a snap-in that registers all the cmdlets and providers in an assembly, see [Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md).</span></span>

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a><span data-ttu-id="df58f-106">Pour écrire un composant logiciel enfichable Windows PowerShell qui inscrit des applets de commande spécifiques.</span><span class="sxs-lookup"><span data-stu-id="df58f-106">To write a Windows PowerShell Snap-in that registers specific cmdlets.</span></span>

1. <span data-ttu-id="df58f-107">Ajoutez l’attribut RunInstallerAttribute.</span><span class="sxs-lookup"><span data-stu-id="df58f-107">Add the RunInstallerAttribute attribute.</span></span>
2. <span data-ttu-id="df58f-108">Créez une classe publique qui dérive de la classe [System. Management. Automation. CustomPSSnapIn](/dotnet/api/System.Management.Automation.CustomPSSnapIn) .</span><span class="sxs-lookup"><span data-stu-id="df58f-108">Create a public class that derives from the [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) class.</span></span>

   <span data-ttu-id="df58f-109">Dans cet exemple, le nom de la classe est « CustomPSSnapinTest ».</span><span class="sxs-lookup"><span data-stu-id="df58f-109">In this example, the class name is "CustomPSSnapinTest".</span></span>

3. <span data-ttu-id="df58f-110">Ajoutez une propriété publique pour le nom du composant logiciel enfichable (obligatoire).</span><span class="sxs-lookup"><span data-stu-id="df58f-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="df58f-111">Quand vous nommez des composants logiciels enfichables, n’utilisez pas les caractères suivants : `#` ,,,, `.` `,` `(` `)` , `{` , `}` , `[` , `]` , `&` , `-` , `/` , `\` , `$` , `;` , `:` ,,,,,,,,,,,,,,, `"` , `'` ,,, `<` `>` `|` , `?` , `@` , `` ` `` ,`*`</span><span class="sxs-lookup"><span data-stu-id="df58f-111">When naming snap-ins, do not use any of the following characters: `#`, `.`, `,`, `(`, `)`, `{`, `}`, `[`, `]`, `&`, `-`, `/`, `\`, `$`, `;`, `:`, `"`, `'`, `<`, `>`, `|`, `?`, `@`, `` ` ``, `*`</span></span>

   <span data-ttu-id="df58f-112">Dans cet exemple, le nom du composant logiciel enfichable est « CustomPSSnapInTest ».</span><span class="sxs-lookup"><span data-stu-id="df58f-112">In this example, the name of the snap-in is "CustomPSSnapInTest".</span></span>

4. <span data-ttu-id="df58f-113">Ajoutez une propriété publique pour le fournisseur du composant logiciel enfichable (obligatoire).</span><span class="sxs-lookup"><span data-stu-id="df58f-113">Add a public property for the vendor of the snap-in (required).</span></span>

   <span data-ttu-id="df58f-114">Dans cet exemple, le fournisseur est « Microsoft ».</span><span class="sxs-lookup"><span data-stu-id="df58f-114">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="df58f-115">Ajoutez une propriété publique pour la ressource fournisseur du composant logiciel enfichable (facultatif).</span><span class="sxs-lookup"><span data-stu-id="df58f-115">Add a public property for the vendor resource of the snap-in (optional).</span></span>

   <span data-ttu-id="df58f-116">Dans cet exemple, la ressource Vendor est « CustomPSSnapInTest, Microsoft ».</span><span class="sxs-lookup"><span data-stu-id="df58f-116">In this example, the vendor resource is "CustomPSSnapInTest,Microsoft".</span></span>

6. <span data-ttu-id="df58f-117">Ajoutez une propriété publique pour la description du composant logiciel enfichable (obligatoire).</span><span class="sxs-lookup"><span data-stu-id="df58f-117">Add a public property for the description of the snap-in (required).</span></span>

   <span data-ttu-id="df58f-118">Dans cet exemple, la description est : « il s’agit d’un composant logiciel enfichable Windows PowerShell personnalisé qui comprend les `Test-HelloWorld` applets de commande et `Test-CustomSnapinTest` ».</span><span class="sxs-lookup"><span data-stu-id="df58f-118">In this example, the description is: "This is a custom Windows PowerShell snap-in that includes the `Test-HelloWorld` and `Test-CustomSnapinTest` cmdlets".</span></span>

7. <span data-ttu-id="df58f-119">Ajoutez une propriété publique pour la ressource Description du composant logiciel enfichable (facultatif).</span><span class="sxs-lookup"><span data-stu-id="df58f-119">Add a public property for the description resource of the snap-in (optional).</span></span>

   <span data-ttu-id="df58f-120">Dans cet exemple, la ressource Vendor est :</span><span class="sxs-lookup"><span data-stu-id="df58f-120">In this example, the vendor resource is:</span></span>

   > <span data-ttu-id="df58f-121">CustomPSSnapInTest, il s’agit d’un composant logiciel enfichable Windows PowerShell personnalisé qui comprend les applets de commande test-HelloWorld et test-CustomSnapinTest».</span><span class="sxs-lookup"><span data-stu-id="df58f-121">CustomPSSnapInTest, This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

8. <span data-ttu-id="df58f-122">Spécifiez les applets de commande qui appartiennent au composant logiciel enfichable personnalisé (facultatif) à l’aide de la classe [System. Management. Automation. instances d’exécution. Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) .</span><span class="sxs-lookup"><span data-stu-id="df58f-122">Specify the cmdlets that belong to the custom snap-in (optional) using the [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) class.</span></span> <span data-ttu-id="df58f-123">Les informations ajoutées ici incluent le nom de l’applet de commande, son type .NET et le nom du fichier d’aide de l’applet de commande (le format du nom du fichier d’aide de l’applet de commande doit être `name.dll-help.xml` ).</span><span class="sxs-lookup"><span data-stu-id="df58f-123">The information added here includes the name of the cmdlet, its .NET type, and the cmdlet Help file name (the format of the cmdlet Help file name should be `name.dll-help.xml`).</span></span>

   <span data-ttu-id="df58f-124">Cet exemple ajoute les applets de commande test-HelloWorld et TestCustomSnapinTest.</span><span class="sxs-lookup"><span data-stu-id="df58f-124">This example adds the Test-HelloWorld and TestCustomSnapinTest cmdlets.</span></span>

9. <span data-ttu-id="df58f-125">Spécifiez les fournisseurs qui appartiennent au composant logiciel enfichable personnalisé (facultatif).</span><span class="sxs-lookup"><span data-stu-id="df58f-125">Specify the providers that belong to the custom snap-in (optional).</span></span>

   <span data-ttu-id="df58f-126">Cet exemple ne spécifie aucun fournisseur.</span><span class="sxs-lookup"><span data-stu-id="df58f-126">This example does not specify any providers.</span></span>

10. <span data-ttu-id="df58f-127">Spécifiez les types qui appartiennent au composant logiciel enfichable personnalisé (facultatif).</span><span class="sxs-lookup"><span data-stu-id="df58f-127">Specify the types that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="df58f-128">Cet exemple ne spécifie aucun type.</span><span class="sxs-lookup"><span data-stu-id="df58f-128">This example does not specify any types.</span></span>

11. <span data-ttu-id="df58f-129">Spécifiez les formats qui appartiennent au composant logiciel enfichable personnalisé (facultatif).</span><span class="sxs-lookup"><span data-stu-id="df58f-129">Specify the formats that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="df58f-130">Cet exemple ne spécifie aucun format.</span><span class="sxs-lookup"><span data-stu-id="df58f-130">This example does not specify any formats.</span></span>

## <a name="example"></a><span data-ttu-id="df58f-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="df58f-131">Example</span></span>

<span data-ttu-id="df58f-132">Cet exemple montre comment écrire un composant logiciel enfichable Windows PowerShell personnalisé qui peut être utilisé pour inscrire les `Test-HelloWorld` applets de commande et `Test-CustomSnapinTest` .</span><span class="sxs-lookup"><span data-stu-id="df58f-132">This example shows how to write a Custom Windows PowerShell snap-in that can be used to register the `Test-HelloWorld` and `Test-CustomSnapinTest` cmdlets.</span></span> <span data-ttu-id="df58f-133">Sachez que dans cet exemple, l’assembly complet peut contenir d’autres applets de commande et fournisseurs qui ne seraient pas inscrits par ce composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="df58f-133">Be aware that in this example, the complete assembly could contain other cmdlets and providers that would not be registered by this snap-in.</span></span>

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

<span data-ttu-id="df58f-134">Pour plus d’informations sur l’inscription des composants logiciels enfichables, consultez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions/ms714644(v=vs.85)) dans le [Guide du programmeur Windows PowerShell](../prog-guide/windows-powershell-programmer-s-guide.md).</span><span class="sxs-lookup"><span data-stu-id="df58f-134">For more information about registering snap-ins, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85)) in the [Windows PowerShell Programmer's Guide](../prog-guide/windows-powershell-programmer-s-guide.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="df58f-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df58f-135">See Also</span></span>

<span data-ttu-id="df58f-136">[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions/ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="df58f-136">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85))</span></span>

[<span data-ttu-id="df58f-137">Kit de développement logiciel Windows PowerShell Shell</span><span class="sxs-lookup"><span data-stu-id="df58f-137">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
