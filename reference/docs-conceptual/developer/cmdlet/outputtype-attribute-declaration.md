---
ms.date: 09/13/2016
ms.topic: reference
title: Déclaration de l’attribut OutputType
description: Déclaration de l’attribut OutputType
ms.openlocfilehash: b5e33346e9ac29c13323781d62daffab892573a4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646451"
---
# <a name="outputtype-attribute-declaration"></a>Déclaration de l’attribut OutputType

L' `OutputType` attribut identifie les types de .NET Framework retournés par une applet de commande, une fonction ou un script.

## <a name="syntax"></a>Syntaxe

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a>Paramètres

Type ( `string[]` ou `Type[]` ) requis. Spécifie les types retournés par la fonction d’applet de commande, ou le script.

ParameterSetName (String []) facultatif. Spécifie les jeux de paramètres qui retournent les types spécifiés dans le `type` paramètre.

providerCmdlet facultatif. Spécifie l’applet de commande du fournisseur qui retourne les types spécifiés dans le `type` paramètre.

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
