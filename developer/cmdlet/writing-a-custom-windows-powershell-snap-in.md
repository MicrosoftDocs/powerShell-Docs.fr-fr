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
ms.openlocfilehash: 4d50ef4dcd75d5c0ba802fbcfe2d7d1d7c954707
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795587"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a>Écriture d’un composant logiciel enfichable Windows PowerShell personnalisé

Cet exemple montre comment écrire un composant logiciel enfichable Windows PowerShell qui inscrit les applets de commande spécifique.

Avec ce type de composant logiciel enfichable, vous spécifiez les applets de commande, les fournisseurs, les types ou les formats à inscrire. Pour plus d’informations sur l’écriture d’un composant logiciel enfichable qui enregistre toutes les applets de commande et les fournisseurs dans un assembly, consultez [écrire un Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md).

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a>Pour écrire un Windows PowerShell Snap-in qui inscrit les applets de commande spécifique.

1. Ajoutez l’attribut RunInstallerAttribute.

2. Créez une classe publique qui dérive de la [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classe.

   Dans cet exemple, le nom de classe est « CustomPSSnapinTest ».

3. Ajouter une propriété publique pour le nom du composant logiciel enfichable (obligatoire). Lorsque vous nommez des composants logiciel enfichables, n’utilisez pas les caractères suivants : #. , ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ? @ ` *

   Dans cet exemple, le nom du composant logiciel enfichable est « CustomPSSnapInTest ».

4. Ajouter une propriété publique pour le fournisseur du composant logiciel enfichable (obligatoire).

   Dans cet exemple, le fournisseur est « Microsoft ».

5. Ajouter une propriété publique pour la ressource du fournisseur du composant logiciel enfichable (facultatif).

   Dans cet exemple, la ressource de fournisseur est « CustomPSSnapInTest, Microsoft ».

6. Ajouter une propriété publique pour la description du composant logiciel enfichable en (obligatoire).

   Dans cet exemple, la description est : « Voici un personnalisé composant logiciel enfichable Windows PowerShell qui inclut les applets de commande Test-CustomSnapinTest Test-HelloWorld ».

7. Ajouter une propriété publique pour la ressource de description du composant logiciel enfichable (facultatif).

   Dans cet exemple, la ressource de fournisseur est « CustomPSSnapInTest, Voici un personnalisé composant logiciel enfichable Windows PowerShell qui inclut les applets de commande Test-HelloWorld et Test-CustomSnapinTest ».

8. Spécifiez les applets de commande qui appartiennent au personnalisée enfichable (facultatif) en utilisant le [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) classe. Les informations ajoutées ici incluent le nom de l’applet de commande, son type .NET et le nom de fichier applet de commande (le format du nom du fichier d’aide applet de commande doit être name.dll-help.xml).

   Cet exemple ajoute les applets de commande Test-HelloWorld et TestCustomSnapinTest.

9. Spécifiez les fournisseurs qui appartiennent à l’enfichable personnalisé (facultatif).

   Cet exemple ne spécifie pas de tous les fournisseurs.

10. Spécifier les types qui appartiennent à l’enfichable personnalisé (facultatif).

    Cet exemple ne spécifie pas de tous les types.

11. Spécifier les formats qui appartiennent à l’enfichable personnalisé (facultatif).

    Cet exemple ne spécifie pas de tous les formats.

## <a name="example"></a>Exemple

Cet exemple montre comment écrire un composant logiciel enfichable personnalisé Windows PowerShell qui peut être utilisé pour inscrire les applets de commande Test-CustomSnapinTest Test-HelloWorld. N’oubliez pas que dans cet exemple, l’assembly complet peut contenir d’autres applets de commande et les fournisseurs qui ne peut pas être inscrit par ce composant logiciel enfichable.

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

Pour plus d’informations sur l’inscription des composants logiciel enfichables, consultez [comment inscrire les applets de commande, fournisseurs et héberger des Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) dans le [-Guide du programmeur Windows PowerShell](../prog-guide/windows-powershell-programmer-s-guide.md).

## <a name="see-also"></a>Voir aussi

[Comment inscrire les applets de commande, fournisseurs et héberger des Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Interpréteur de commandes Windows PowerShell SDK](../windows-powershell-reference.md)
