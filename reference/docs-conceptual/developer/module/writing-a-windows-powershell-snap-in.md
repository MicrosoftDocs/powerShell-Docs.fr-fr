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
# <a name="writing-a-windows-powershell-snap-in"></a>Écriture d’un composant logiciel enfichable Windows PowerShell

Cet exemple montre comment écrire un composant logiciel enfichable Windows PowerShell qui peut être utilisé pour inscrire toutes les applets de commande et tous les fournisseurs Windows PowerShell dans un assembly.

Avec ce type de composant logiciel enfichable, vous ne sélectionnez pas les applets de commande et les fournisseurs que vous souhaitez inscrire. Pour écrire un composant logiciel enfichable qui vous permet de sélectionner les éléments inscrits, consultez [écriture d’un composant logiciel enfichable Windows PowerShell personnalisé](./writing-a-custom-windows-powershell-snap-in.md).

### <a name="writing-a-windows-powershell-snap-in"></a>Écriture d’un composant logiciel enfichable Windows PowerShell

1. Ajoutez l’attribut RunInstallerAttribute.

2. Créez une classe publique qui dérive de la classe [System. Management. Automation. PSSnapin](/dotnet/api/System.Management.Automation.PSSnapIn) .

    Dans cet exemple, le nom de la classe est « GetProcPSSnapIn01 ».

3. Ajoutez une propriété publique pour le nom du composant logiciel enfichable (obligatoire). Quand vous nommez des composants logiciels enfichables, n’utilisez pas les caractères suivants : `#` ,,,, `.` `,` `(` `)` , `{` , `}` , `[` , `]` , `&` , `-` , `/` , `\` , `$` , `;` , `:` ,,,,,,,,,,,,,,, `"` , `'` ,,, `<` `>` `|` , `?` , `@` , `` ` `` , `*`

    Dans cet exemple, le nom du composant logiciel enfichable est « GetProcPSSnapIn01 ».

4. Ajoutez une propriété publique pour le fournisseur du composant logiciel enfichable (obligatoire).

    Dans cet exemple, le fournisseur est « Microsoft ».

5. Ajoutez une propriété publique pour la ressource fournisseur du composant logiciel enfichable (facultatif).

    Dans cet exemple, la ressource Vendor est « GetProcPSSnapIn01, Microsoft ».

6. Ajoutez une propriété publique pour la description du composant logiciel enfichable (obligatoire).

    Dans cet exemple, la description est « il s’agit d’un composant logiciel enfichable Windows PowerShell qui inscrit l’applet de commande «obtenir-proc »».

7. Ajoutez une propriété publique pour la ressource Description du composant logiciel enfichable (facultatif).

    Dans cet exemple, la ressource Vendor est « GetProcPSSnapIn01, il s’agit d’un composant logiciel enfichable Windows PowerShell qui inscrit l’applet de commande «obtenir-proc »».

## <a name="example"></a>Exemple

Cet exemple montre comment écrire un composant logiciel enfichable Windows PowerShell qui peut être utilisé pour inscrire l’applet de commande Get-Proc dans le shell Windows PowerShell. Sachez que dans cet exemple, l’assembly complet contient uniquement la classe de composant logiciel enfichable GetProcPSSnapIn01 et la classe d’applet de commande `Get-Proc` .

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

## <a name="see-also"></a>Voir aussi

[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions/ms714644(v=vs.85))

[Kit SDK Windows PowerShell](../windows-powershell-reference.md)
