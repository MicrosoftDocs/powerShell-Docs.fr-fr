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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068162"
---
# <a name="extending-output-objects"></a>Extension des objets de sortie

Vous pouvez étendre les objets .NET Framework qui sont retournés par les applets de commande, les fonctions et les scripts à l’aide de fichiers de types (.ps1xml). Fichiers de types sont des fichiers XML qui vous permettent d’ajouter des propriétés et des méthodes aux objets existants. Par exemple, Windows PowerShell fournit le fichier Types.ps1xml, qui ajoute des éléments à plusieurs objets de .NET Framework existantes. Le fichier Types.ps1xml se trouve dans le répertoire d’installation de Windows PowerShell (`$pshome`). Vous pouvez créer votre propre fichier de types pour étendre ces objets ou pour étendre les autres objets. Lorsque vous étendez un objet à l’aide d’un fichier de types, n’importe quelle instance de l’objet est étendue avec les nouveaux éléments.

## <a name="extending-the-systemarray-object"></a>Extension de l’objet System.Array

L’exemple suivant montre comment Windows PowerShell étend la [System.Array](/dotnet/api/System.Array) objet dans le fichier Types.ps1xml. Par défaut, [System.Array](/dotnet/api/System.Array) objets ont une `Length` propriété qui indique le nombre d’objets dans le tableau. Toutefois, étant donné que la nom « longueur de » ne décrit pas clairement la propriété, Windows PowerShell ajoute le `Count` propriété d’alias, qui affiche la même valeur que le `Length` propriété. Le code XML suivant ajoute le `Count` propriété le [System.Array](/dotnet/api/System.Array) type.

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

Pour afficher cette nouvelle propriété d’alias, utilisez un [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) commande sur n’importe quel tableau, comme indiqué dans l’exemple suivant.

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
Vous pouvez utiliser la `Count` propriété ou le `Length` propriété afin de déterminer le nombre d’objets est dans un tableau. Par exemple :

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

## <a name="custom-types-files"></a>Fichiers de Types personnalisés

Pour créer un fichier de types personnalisés, démarrez en copiant un fichier de types existant. Le nouveau fichier peut avoir n’importe quel nom, mais il doit avoir une extension de nom de fichier .ps1xml. Lorsque vous copiez le fichier, vous pouvez placer le nouveau fichier dans n’importe quel répertoire est accessible à Windows PowerShell, mais il est utile de placer les fichiers dans le répertoire d’installation de Windows PowerShell (`$pshome`) ou dans un sous-répertoire du répertoire d’installation.

Pour ajouter vos propres types étendus dans le fichier, ajoutez un élément de types pour chaque objet que vous souhaitez étendre. Les rubriques suivantes fournissent des exemples.

- Pour plus d’informations sur l’ajout de propriétés et des jeux de propriétés, consultez [propriétés étendues](./extending-properties-for-objects.md)

- Pour plus d’informations sur l’ajout de méthodes, consultez [méthodes étendu](./defining-default-methods-for-objects.md).

- Pour plus d’informations sur l’ajout de jeux de membres, consultez [étendue membre définit](./defining-default-member-sets-for-objects.md).

Une fois que vous définissez vos propres types étendus, utilisez une des méthodes suivantes pour rendre vos objets étendus disponibles :

- Pour rendre votre fichier de types étendus disponibles à la session active, utilisez la [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) applet de commande pour ajouter le nouveau fichier. Si vous souhaitez que vos types sont prioritaires sur les types qui sont définis dans des autres types de fichiers (y compris le fichier Types.ps1xml), utilisez le `PrependData` paramètre de la [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) applet de commande.
- Pour rendre votre fichier de types étendus disponible pour toutes les futures sessions, ajoutez le fichier de types à un module, exporter la session active ou ajouter le [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) commande à votre profil Windows PowerShell.

## <a name="signing-types-files"></a>Signature des fichiers de Types

Fichiers de types doivent être signés numériquement pour empêcher toute falsification, car le code XML peut inclure des blocs de script. Pour plus d’informations sur l’ajout de signatures numériques, consultez [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)

## <a name="see-also"></a>Voir aussi

[Définition des propriétés par défaut des objets](./extending-properties-for-objects.md)

[Définition de méthodes par défaut des objets](./defining-default-methods-for-objects.md)

[Définition de jeux de membres par défaut des objets](./defining-default-member-sets-for-objects.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
