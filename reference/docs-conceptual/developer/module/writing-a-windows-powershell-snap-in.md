---
ms.date: 09/13/2016
ms.topic: reference
title: Écriture d’un composant logiciel enfichable Windows PowerShell
description: Écriture d’un composant logiciel enfichable Windows PowerShell
ms.openlocfilehash: f658c2fa1211bfb77d2e8edd3999ce7f92df13bb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659445"
---
# <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="62c14-103">Écriture d’un composant logiciel enfichable Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="62c14-103">Writing a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="62c14-104">Cet exemple montre comment écrire un composant logiciel enfichable Windows PowerShell qui peut être utilisé pour inscrire toutes les applets de commande et tous les fournisseurs Windows PowerShell dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="62c14-104">This example shows how to write a Windows PowerShell snap-in that can be used to register all the cmdlets and Windows PowerShell providers in an assembly.</span></span>

<span data-ttu-id="62c14-105">Avec ce type de composant logiciel enfichable, vous ne sélectionnez pas les applets de commande et les fournisseurs que vous souhaitez inscrire.</span><span class="sxs-lookup"><span data-stu-id="62c14-105">With this type of snap-in, you do not select which cmdlets and providers you want to register.</span></span> <span data-ttu-id="62c14-106">Pour écrire un composant logiciel enfichable qui vous permet de sélectionner les éléments inscrits, consultez [écriture d’un composant logiciel enfichable Windows PowerShell personnalisé](./writing-a-custom-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="62c14-106">To write a snap-in that allows you to select what is registered, see [Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span></span>

### <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="62c14-107">Écriture d’un composant logiciel enfichable Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="62c14-107">Writing a Windows PowerShell Snap-in</span></span>

1. <span data-ttu-id="62c14-108">Ajoutez l’attribut RunInstallerAttribute.</span><span class="sxs-lookup"><span data-stu-id="62c14-108">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="62c14-109">Créez une classe publique qui dérive de la classe [System. Management. Automation. PSSnapin](/dotnet/api/System.Management.Automation.PSSnapIn) .</span><span class="sxs-lookup"><span data-stu-id="62c14-109">Create a public class that derives from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) class.</span></span>

    <span data-ttu-id="62c14-110">Dans cet exemple, le nom de la classe est « GetProcPSSnapIn01 ».</span><span class="sxs-lookup"><span data-stu-id="62c14-110">In this example, the class name is "GetProcPSSnapIn01".</span></span>

3. <span data-ttu-id="62c14-111">Ajoutez une propriété publique pour le nom du composant logiciel enfichable (obligatoire).</span><span class="sxs-lookup"><span data-stu-id="62c14-111">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="62c14-112">Quand vous nommez des composants logiciels enfichables, n’utilisez pas les caractères suivants : `#` ,,,, `.` `,` `(` `)` , `{` , `}` , `[` , `]` , `&` , `-` , `/` , `\` , `$` , `;` , `:` ,,,,,,,,,,,,,,, `"` , `'` ,,, `<` `>` `|` , `?` , `@` , `` ` `` , `*`</span><span class="sxs-lookup"><span data-stu-id="62c14-112">When naming snap-ins, do not use any of the following characters: `#`, `.`, `,`, `(`, `)`, `{`, `}`, `[`, `]`, `&`, `-`, `/`, `\`, `$`, `;`, `:`, `"`, `'`, `<`, `>`, `|`, `?`, `@`, `` ` ``, `*`</span></span>

    <span data-ttu-id="62c14-113">Dans cet exemple, le nom du composant logiciel enfichable est « GetProcPSSnapIn01 ».</span><span class="sxs-lookup"><span data-stu-id="62c14-113">In this example, the name of the snap-in is "GetProcPSSnapIn01".</span></span>

4. <span data-ttu-id="62c14-114">Ajoutez une propriété publique pour le fournisseur du composant logiciel enfichable (obligatoire).</span><span class="sxs-lookup"><span data-stu-id="62c14-114">Add a public property for the vendor of the snap-in (required).</span></span>

    <span data-ttu-id="62c14-115">Dans cet exemple, le fournisseur est « Microsoft ».</span><span class="sxs-lookup"><span data-stu-id="62c14-115">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="62c14-116">Ajoutez une propriété publique pour la ressource fournisseur du composant logiciel enfichable (facultatif).</span><span class="sxs-lookup"><span data-stu-id="62c14-116">Add a public property for the vendor resource of the snap-in (optional).</span></span>

    <span data-ttu-id="62c14-117">Dans cet exemple, la ressource Vendor est « GetProcPSSnapIn01, Microsoft ».</span><span class="sxs-lookup"><span data-stu-id="62c14-117">In this example, the vendor resource is "GetProcPSSnapIn01,Microsoft".</span></span>

6. <span data-ttu-id="62c14-118">Ajoutez une propriété publique pour la description du composant logiciel enfichable (obligatoire).</span><span class="sxs-lookup"><span data-stu-id="62c14-118">Add a public property for the description of the snap-in (required).</span></span>

    <span data-ttu-id="62c14-119">Dans cet exemple, la description est « il s’agit d’un composant logiciel enfichable Windows PowerShell qui inscrit l’applet de commande «obtenir-proc »».</span><span class="sxs-lookup"><span data-stu-id="62c14-119">In this example, the description is "This is a Windows PowerShell snap-in that registers the  get-proc cmdlet".</span></span>

7. <span data-ttu-id="62c14-120">Ajoutez une propriété publique pour la ressource Description du composant logiciel enfichable (facultatif).</span><span class="sxs-lookup"><span data-stu-id="62c14-120">Add a public property for the description resource of the snap-in (optional).</span></span>

    <span data-ttu-id="62c14-121">Dans cet exemple, la ressource Vendor est « GetProcPSSnapIn01, il s’agit d’un composant logiciel enfichable Windows PowerShell qui inscrit l’applet de commande «obtenir-proc »».</span><span class="sxs-lookup"><span data-stu-id="62c14-121">In this example, the vendor resource is "GetProcPSSnapIn01,This is a Windows PowerShell snap-in  that registers the get-proc cmdlet".</span></span>

## <a name="example"></a><span data-ttu-id="62c14-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="62c14-122">Example</span></span>

<span data-ttu-id="62c14-123">Cet exemple montre comment écrire un composant logiciel enfichable Windows PowerShell qui peut être utilisé pour inscrire l’applet de commande Get-Proc dans le shell Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="62c14-123">This example shows how to write a Windows PowerShell snap-in that can be used to register the Get-Proc cmdlet in the Windows PowerShell shell.</span></span> <span data-ttu-id="62c14-124">Sachez que dans cet exemple, l’assembly complet contient uniquement la classe de composant logiciel enfichable GetProcPSSnapIn01 et la classe d’applet de commande `Get-Proc` .</span><span class="sxs-lookup"><span data-stu-id="62c14-124">Be aware that in this example, the complete assembly would contain only the GetProcPSSnapIn01 snap-in class and the `Get-Proc` cmdlet class.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="62c14-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62c14-125">See Also</span></span>

<span data-ttu-id="62c14-126">[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions/ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="62c14-126">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85))</span></span>

[<span data-ttu-id="62c14-127">Kit SDK Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="62c14-127">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
