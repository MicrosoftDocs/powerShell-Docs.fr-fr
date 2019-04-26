---
title: Déclaration d’attribut alias | Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068709"
---
# <a name="alias-attribute-declaration"></a>Déclaration de l’attribut Alias

L’attribut d’Alias permet à l’utilisateur spécifier des noms différents pour un paramètre d’applet de commande. Alias peuvent être utilisés pour fournir des raccourcis pour un nom de paramètre, ou ils peuvent fournir des noms différents qui sont appropriés pour différents scénarios.

## <a name="syntax"></a>Syntaxe

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>Paramètres

`aliasName` (Qu' Obligatoire. Spécifie un ensemble de noms d’alias séparés par des virgules pour le paramètre d’applet de commande.

## <a name="remarks"></a>Remarques

- L’attribut de l’Alias est utilisé avec l’attribut de paramètre lorsque vous spécifiez un paramètre d’applet de commande. Pour plus d’informations sur la façon de déclarer ces attributs, consultez [comment déclarer des paramètres d’applet de commande](./how-to-declare-cmdlet-parameters.md).

- Chaque nom d’alias doit être unique au sein d’une applet de commande. Windows PowerShell ne vérifie pas les noms d’alias en double.

- L’attribut de l’Alias est utilisé qu’une seule fois pour chaque paramètre dans une applet de commande.

- L’attribut de l’Alias est défini par le [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) classe.

## <a name="see-also"></a>Voir aussi

[Alias de paramètre](./parameter-aliases.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
