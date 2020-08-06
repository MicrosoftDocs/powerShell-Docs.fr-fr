---
title: Déclaration de l’attribut alias | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.openlocfilehash: 4c1ff34a244611173ca919a44d6598189b19dc98
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782410"
---
# <a name="alias-attribute-declaration"></a>Déclaration de l’attribut Alias

L’attribut alias permet à l’utilisateur de spécifier des noms différents pour un paramètre d’applet de commande. Les alias peuvent être utilisés pour fournir des raccourcis pour un nom de paramètre, ou ils peuvent fournir des noms différents qui conviennent à différents scénarios.

## <a name="syntax"></a>Syntaxe

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>Paramètres

`aliasName`(String []) Obligatoire. Spécifie un jeu de noms d’alias séparés par des virgules pour le paramètre d’applet de commande.

## <a name="remarks"></a>Notes

- L’attribut alias est utilisé avec l’attribut Parameter lorsque vous spécifiez un paramètre d’applet de commande. Pour plus d’informations sur la façon de déclarer ces attributs, consultez [comment déclarer des paramètres d’applet de](./how-to-declare-cmdlet-parameters.md)commande.

- Chaque nom d’alias doit être unique au sein d’une applet de commande. Windows PowerShell ne vérifie pas les noms d’alias en double.

- L’attribut alias est utilisé une fois pour chaque paramètre d’une applet de commande.

- L’attribut alias est défini par la classe [System. Management. Automation. AliasAttribute](/dotnet/api/System.Management.Automation.AliasAttribute) .

## <a name="see-also"></a>Voir aussi

[Alias de paramètres](./parameter-aliases.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
