---
title: Déclarer des propriétés en tant que paramètres | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068264"
---
# <a name="declaring-properties-as-parameters"></a>Déclaration des propriétés en tant que paramètres

Cette rubrique fournit des informations de base que vous devez comprendre avant de déclarer les paramètres d’applet de commande.

Pour déclarer les paramètres d’applet de commande au sein de votre classe d’applet de commande, définissez les propriétés publiques qui représentent chaque paramètre et puis ajoutez un ou plusieurs attributs de paramètre pour chaque propriété. Le runtime de Windows PowerShell utilise les attributs de paramètre pour identifier la propriété comme un paramètre d’applet de commande. La syntaxe de base pour déclarer l’attribut de paramètre est `[Parameter()]`.

Voici un exemple d’une propriété définie comme un paramètre obligatoire.

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

- Un paramètre doit être explicitement marqué comme public. Paramètres qui ne sont pas marqués comme public par défaut interne et seront introuvable par le runtime de Windows PowerShell.

- Les paramètres doivent être définis en tant que types Microsoft .NET Framework pour fournir une meilleure validation de paramètre. Par exemple, les paramètres qui sont limitées à une valeur en dehors d’un ensemble de valeurs doivent être définis comme un type d’énumération. Paramètres qui acceptent une valeur de l’identificateur URI (Uniform Resource) doivent être de type [System.Uri](/dotnet/api/System.Uri).

- Éviter les paramètres de chaînes de base pour les propriétés de tout sauf texte libre.

- Vous pouvez ajouter un paramètre à un nombre quelconque de jeux de paramètres. Pour plus d’informations sur les jeux de paramètres, consultez [définit des paramètres d’applet de commande](./cmdlet-parameter-sets.md).

Windows PowerShell fournit également un ensemble de paramètres communs qui sont automatiquement disponibles pour chaque applet de commande. Pour plus d’informations sur ces paramètres et leurs alias, consultez [paramètres communs d’applet de commande](./common-parameter-names.md).

## <a name="see-also"></a>Voir aussi

[Paramètres de l’applet de commande courantes](./common-parameter-names.md)

[Types de paramètre d’applet de commande](./types-of-cmdlet-parameters.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
