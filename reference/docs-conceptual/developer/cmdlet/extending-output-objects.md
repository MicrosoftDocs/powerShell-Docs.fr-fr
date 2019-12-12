---
title: Extension des objets de sortie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a252e0ec-d456-42d7-bd49-d6b8bc57f388
caps.latest.revision: 11
ms.openlocfilehash: 9c9d50c880f843e21621e5735c800e3afb48b2ad
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369718"
---
# <a name="extending-output-objects"></a>Extension des objets de sortie

Vous pouvez étendre les objets .NET Framework retournés par les applets de commande, les fonctions et les scripts à l’aide des fichiers de types (. ps1xml). Les fichiers de types sont des fichiers XML qui vous permettent d’ajouter des propriétés et des méthodes aux objets existants. Par exemple, Windows PowerShell fournit le fichier types. ps1xml, qui ajoute des éléments à plusieurs objets .NET Framework existants. Le fichier types. ps1xml se trouve dans le répertoire d’installation de Windows PowerShell (`$pshome`). Vous pouvez créer votre propre fichier de types pour étendre davantage ces objets ou pour étendre d’autres objets. Quand vous étendez un objet à l’aide d’un fichier de types, toute instance de l’objet est étendue avec les nouveaux éléments.

## <a name="extending-the-systemarray-object"></a>Extension de l’objet System. Array

L’exemple suivant montre comment Windows PowerShell étend l’objet [System. Array](/dotnet/api/System.Array) dans le fichier types. ps1xml. Par défaut, les objets [System. Array](/dotnet/api/System.Array) ont une propriété `Length` qui répertorie le nombre d’objets dans le tableau. Toutefois, étant donné que le nom « length » ne décrit pas clairement la propriété, Windows PowerShell ajoute la propriété d’alias `Count`, qui affiche la même valeur que la propriété `Length`. Le code XML suivant ajoute la propriété `Count` au type [System. Array](/dotnet/api/System.Array) .

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>

```

Pour afficher cette nouvelle propriété d’alias, utilisez une commande d' [extraction de membre](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) sur n’importe quel tableau, comme indiqué dans l’exemple suivant.

```powershell
Get-Member -InputObject (1,2,3,4)
```

La commande retourne les résultats suivants.
```output
Name           MemberType    Definition
----           ----------    ----------
Count          AliasProperty Count = Length
Address        Method        System.Object& Address(Int32 )
Clone          Method        System.Object Clone()
CopyTo         Method        System.Void CopyTo(Array array, Int32 index):
Equals         Method        System.Boolean Equals(Object obj)
Get            Method        System.Object Get(Int32 )
...
Length         Property      System.Int32 Length {get;}
```
Vous pouvez utiliser la propriété `Count` ou la propriété `Length` pour déterminer le nombre d’objets contenus dans un tableau. Par exemple :

```powershell
PS> (1, 2, 3, 4).Count
```

```output
4
```

```powershell
PS> (1, 2, 3, 4).Length
```

```output
4
```

## <a name="custom-types-files"></a>Fichiers de types personnalisés

Pour créer un fichier de types personnalisés, commencez par copier un fichier de types existant. Le nouveau fichier peut avoir n’importe quel nom, mais il doit avoir une extension de nom de fichier. ps1xml. Lorsque vous copiez le fichier, vous pouvez placer le nouveau fichier dans n’importe quel répertoire accessible à Windows PowerShell, mais il est utile de placer les fichiers dans le répertoire d’installation de Windows PowerShell (`$pshome`) ou dans un sous-répertoire du répertoire d’installation.

Pour ajouter vos propres types étendus au fichier, ajoutez un élément types pour chaque objet que vous souhaitez étendre. Les rubriques suivantes fournissent des exemples.

- Pour plus d’informations sur l’ajout de propriétés et de jeux de propriétés, consultez [propriétés étendues](./extending-properties-for-objects.md) .

- Pour plus d’informations sur l’ajout de méthodes, consultez [méthodes étendues](./defining-default-methods-for-objects.md).

- Pour plus d’informations sur l’ajout de jeux de membres, consultez [jeux de membres étendus](./defining-default-member-sets-for-objects.md).

Une fois que vous avez défini vos propres types étendus, utilisez l’une des méthodes suivantes pour rendre vos objets étendus disponibles :

- Pour mettre votre fichier de types étendus à la disposition de la session active, utilisez l’applet de commande [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) pour ajouter le nouveau fichier. Si vous souhaitez que vos types aient la priorité sur les types définis dans d’autres types de fichiers (y compris le fichier types. ps1xml), utilisez le paramètre `PrependData` de l’applet de commande [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) .
- Pour mettre votre fichier de types étendus à la disposition de toutes les sessions ultérieures, ajoutez le fichier de types à un module, exportez la session active ou ajoutez la commande [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) à votre profil Windows PowerShell.

## <a name="signing-types-files"></a>Fichiers de types de signature

Les fichiers de types doivent être signés numériquement pour empêcher la falsification, car le XML peut inclure des blocs de script. Pour plus d’informations sur l’ajout de signatures numériques, consultez [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)

## <a name="see-also"></a>Voir aussi

[Définition des propriétés par défaut des objets](./extending-properties-for-objects.md)

[Définition des méthodes par défaut pour les objets](./defining-default-methods-for-objects.md)

[Définition des jeux de membres par défaut pour les objets](./defining-default-member-sets-for-objects.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
