---
ms.date: 09/13/2016
ms.topic: reference
title: Écriture d’un composant logiciel enfichable Windows PowerShell personnalisé
description: Écriture d’un composant logiciel enfichable Windows PowerShell personnalisé
ms.openlocfilehash: e79c0c3db583fa0add9287745e97958a71360592
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659532"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a>Écriture d’un composant logiciel enfichable Windows PowerShell personnalisé

Cet exemple montre comment écrire un composant logiciel enfichable Windows PowerShell qui inscrit des applets de commande spécifiques.

Avec ce type de composant logiciel enfichable, vous spécifiez les applets de commande, fournisseurs, types ou formats à inscrire. Pour plus d’informations sur l’écriture d’un composant logiciel enfichable qui inscrit toutes les applets de commande et tous les fournisseurs dans un assembly, consultez [écriture d’un composant logiciel enfichable Windows PowerShell](./writing-a-windows-powershell-snap-in.md).

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a>Pour écrire un composant logiciel enfichable Windows PowerShell qui inscrit des applets de commande spécifiques.

1. Ajoutez l’attribut RunInstallerAttribute.
2. Créez une classe publique qui dérive de la classe [System. Management. Automation. CustomPSSnapIn](/dotnet/api/System.Management.Automation.CustomPSSnapIn) .

   Dans cet exemple, le nom de la classe est « CustomPSSnapinTest ».

3. Ajoutez une propriété publique pour le nom du composant logiciel enfichable (obligatoire). Quand vous nommez des composants logiciels enfichables, n’utilisez pas les caractères suivants : `#` ,,,, `.` `,` `(` `)` , `{` , `}` , `[` , `]` , `&` , `-` , `/` , `\` , `$` , `;` , `:` ,,,,,,,,,,,,,,, `"` , `'` ,,, `<` `>` `|` , `?` , `@` , `` ` `` , `*`

   Dans cet exemple, le nom du composant logiciel enfichable est « CustomPSSnapInTest ».

4. Ajoutez une propriété publique pour le fournisseur du composant logiciel enfichable (obligatoire).

   Dans cet exemple, le fournisseur est « Microsoft ».

5. Ajoutez une propriété publique pour la ressource fournisseur du composant logiciel enfichable (facultatif).

   Dans cet exemple, la ressource Vendor est « CustomPSSnapInTest, Microsoft ».

6. Ajoutez une propriété publique pour la description du composant logiciel enfichable (obligatoire).

   Dans cet exemple, la description est : « il s’agit d’un composant logiciel enfichable Windows PowerShell personnalisé qui comprend les `Test-HelloWorld` applets de commande et `Test-CustomSnapinTest` ».

7. Ajoutez une propriété publique pour la ressource Description du composant logiciel enfichable (facultatif).

   Dans cet exemple, la ressource Vendor est :

   > CustomPSSnapInTest, il s’agit d’un composant logiciel enfichable Windows PowerShell personnalisé qui comprend les applets de commande Test-HelloWorld et Test-CustomSnapinTest».

8. Spécifiez les applets de commande qui appartiennent au composant logiciel enfichable personnalisé (facultatif) à l’aide de la classe [System. Management. Automation. instances d’exécution. Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) . Les informations ajoutées ici incluent le nom de l’applet de commande, son type .NET et le nom du fichier d’aide de l’applet de commande (le format du nom du fichier d’aide de l’applet de commande doit être `name.dll-help.xml` ).

   Cet exemple ajoute les applets de commande Test-HelloWorld et TestCustomSnapinTest.

9. Spécifiez les fournisseurs qui appartiennent au composant logiciel enfichable personnalisé (facultatif).

   Cet exemple ne spécifie aucun fournisseur.

10. Spécifiez les types qui appartiennent au composant logiciel enfichable personnalisé (facultatif).

    Cet exemple ne spécifie aucun type.

11. Spécifiez les formats qui appartiennent au composant logiciel enfichable personnalisé (facultatif).

    Cet exemple ne spécifie aucun format.

## <a name="example"></a>Exemple

Cet exemple montre comment écrire un composant logiciel enfichable Windows PowerShell personnalisé qui peut être utilisé pour inscrire les `Test-HelloWorld` applets de commande et `Test-CustomSnapinTest` . Sachez que dans cet exemple, l’assembly complet peut contenir d’autres applets de commande et fournisseurs qui ne seraient pas inscrits par ce composant logiciel enfichable.

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

Pour plus d’informations sur l’inscription des composants logiciels enfichables, consultez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions/ms714644(v=vs.85)) dans le [Guide du programmeur Windows PowerShell](../prog-guide/windows-powershell-programmer-s-guide.md).

## <a name="see-also"></a>Voir aussi

[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions/ms714644(v=vs.85))

[Kit SDK Windows PowerShell](../windows-powershell-reference.md)
