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
# <a name="writing-a-windows-powershell-snap-in"></a>Écriture d’un composant logiciel enfichable Windows PowerShell

Cet exemple montre comment écrire un composant logiciel enfichable Windows PowerShell qui peut être utilisé pour enregistrer toutes les applets de commande et les fournisseurs Windows PowerShell dans un assembly.

Avec ce type de composant logiciel enfichable, vous ne sélectionnez pas les applets de commande et les fournisseurs que vous souhaitez inscrire. Pour écrire un composant logiciel enfichable qui vous permet de sélectionner ce qui est inscrit, consultez [écrire un personnalisé Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).

### <a name="writing-a-windows-powershell-snap-in"></a>Écriture d’un composant logiciel enfichable Windows PowerShell

1. Ajoutez l’attribut RunInstallerAttribute.

2. Créez une classe publique qui dérive de la [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) classe.

    Dans cet exemple, le nom de classe est « GetProcPSSnapIn01 ».

3. Ajouter une propriété publique pour le nom du composant logiciel enfichable (obligatoire). Lorsque vous nommez des composants logiciel enfichables, n’utilisez pas les caractères suivants : #. , ( ) { } [ ] & - /\ $ ; : " ' \< > ; ? @ ` *

    Dans cet exemple, le nom du composant logiciel enfichable est « GetProcPSSnapIn01 ».

4. Ajouter une propriété publique pour le fournisseur du composant logiciel enfichable (obligatoire).

    Dans cet exemple, le fournisseur est « Microsoft ».

5. Ajouter une propriété publique pour la ressource du fournisseur du composant logiciel enfichable (facultatif).

    Dans cet exemple, la ressource de fournisseur est « GetProcPSSnapIn01, Microsoft ».

6. Ajouter une propriété publique pour la description du composant logiciel enfichable en (obligatoire).

    Dans cet exemple, la description est « Est un composant logiciel enfichable Windows PowerShell qui inscrit l’applet de commande get-Process ».

7. Ajouter une propriété publique pour la ressource de description du composant logiciel enfichable (facultatif).

    Dans cet exemple, la ressource de fournisseur est « GetProcPSSnapIn01, ceci est un composant logiciel enfichable Windows PowerShell qui inscrit l’applet de commande get-Process ».

## <a name="example"></a>Exemple

Cet exemple montre comment écrire un composant logiciel enfichable Windows PowerShell qui peut être utilisé pour inscrire l’applet de commande Get-Process dans l’interpréteur de commandes Windows PowerShell. N’oubliez pas que dans cet exemple, l’assembly complet contient uniquement la GetProcPSSnapIn01 classe snap-in et la classe d’applet de commande Get-Process.

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

[Comment inscrire les applets de commande, fournisseurs et héberger des Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Interpréteur de commandes Windows PowerShell SDK](../windows-powershell-reference.md)
