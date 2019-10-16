---
title: Déclaration de l’attribut alias | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.assetid: d0df3a46-b1cc-42b9-beb1-e16bce254007
caps.latest.revision: 10
ms.openlocfilehash: 4d20672c5181c994c1b53624f6c42a301db11f26
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72370018"
---
# <a name="alias-attribute-declaration"></a>Déclaration de l’attribut Alias

L’attribut alias permet à l’utilisateur de spécifier des noms différents pour un paramètre d’applet de commande. Les alias peuvent être utilisés pour fournir des raccourcis pour un nom de paramètre, ou ils peuvent fournir des noms différents qui conviennent à différents scénarios.

## <a name="syntax"></a>Syntaxe

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>Paramètres

`aliasName` (String []) requis. Spécifie un jeu de noms d’alias séparés par des virgules pour le paramètre d’applet de commande.

## <a name="remarks"></a>Remarks

- L’attribut alias est utilisé avec l’attribut Parameter lorsque vous spécifiez un paramètre d’applet de commande. Pour plus d’informations sur la façon de déclarer ces attributs, consultez [comment déclarer des paramètres d’applet de](./how-to-declare-cmdlet-parameters.md)commande.

- Chaque nom d’alias doit être unique au sein d’une applet de commande. Windows PowerShell ne vérifie pas les noms d’alias en double.

- L’attribut alias est utilisé une fois pour chaque paramètre d’une applet de commande.

- L’attribut alias est défini par la classe [System. Management. Automation. AliasAttribute](/dotnet/api/System.Management.Automation.AliasAttribute) .

## <a name="see-also"></a>Voir aussi

[Alias de paramètres](./parameter-aliases.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
