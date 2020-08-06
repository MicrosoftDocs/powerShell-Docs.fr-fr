---
title: Déclaration des propriétés en tant que paramètres | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 63113f541df534b1f720ceb06e14b5031f2311b2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774641"
---
# <a name="declaring-properties-as-parameters"></a>Déclaration des propriétés en tant que paramètres

Cette rubrique fournit des informations de base que vous devez comprendre avant de déclarer les paramètres d’une applet de commande.

Pour déclarer les paramètres d’une applet de commande dans votre classe d’applet de commande, définissez les propriétés publiques qui représentent chaque paramètre, puis ajoutez un ou plusieurs attributs de paramètre à chaque propriété. Le runtime Windows PowerShell utilise les attributs de paramètre pour identifier la propriété en tant que paramètre d’applet de commande. La syntaxe de base pour déclarer l’attribut de paramètre est `[Parameter()]` .

Voici un exemple de propriété définie en tant que paramètre obligatoire.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Voici quelques points à retenir sur les paramètres.

- Un paramètre doit être explicitement marqué comme public. Les paramètres qui ne sont pas marqués comme étant par défaut publics comme internes et ne seront pas trouvés par le runtime Windows PowerShell.

- Les paramètres doivent être définis en tant que types Microsoft .NET Framework pour fournir une meilleure validation des paramètres. Par exemple, les paramètres qui sont limités à une valeur d’un ensemble de valeurs doivent être définis en tant que type énumération. Les paramètres qui acceptent une valeur Uniform Resource Identifier (URI) doivent être de type [System. Uri](/dotnet/api/System.Uri).

- Évitez les paramètres de chaîne de base pour toutes les propriétés de texte de forme libre.

- Vous pouvez ajouter un paramètre à un nombre quelconque de jeux de paramètres. Pour plus d’informations sur les jeux de paramètres, consultez [jeux de paramètres d’applet](./cmdlet-parameter-sets.md)de commande.

Windows PowerShell fournit également un ensemble de paramètres communs qui sont automatiquement disponibles pour chaque applet de commande. Pour plus d’informations sur ces paramètres et leurs alias, consultez [paramètres communs des applets](./common-parameter-names.md)de commande.

## <a name="see-also"></a>Voir aussi

[Paramètres communs de l’applet de commande](./common-parameter-names.md)

[Types de paramètre d’applet de commande](./types-of-cmdlet-parameters.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
