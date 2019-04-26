---
title: Déclaration d’attribut OutputType | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97a98ee-ffc0-42f0-a9a6-b0717b39c798
caps.latest.revision: 5
ms.openlocfilehash: 7aa6fa407e509a31c4066c4f73ae01b02b2f338c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067601"
---
# <a name="outputtype-attribute-declaration"></a>Déclaration de l’attribut OutputType

Le `OutputType` attribut identifie les types .NET Framework retournés par une applet de commande, une fonction ou un script.

## <a name="syntax"></a>Syntaxe

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a>Paramètres

Type (`string[]` ou `Type[]`) requis. Spécifie les types retournés par la fonction de l’applet de commande, ou un script.

ParameterSetName (que facultatif. Spécifie les jeux de paramètres qui retournent les types spécifiés dans le `type` paramètre.

providerCmdlet facultatif. Spécifie l’applet de commande fournisseur qui retourne les types spécifiés dans le `type` paramètre.

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
