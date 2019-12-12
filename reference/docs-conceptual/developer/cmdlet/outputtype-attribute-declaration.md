---
title: OutputType, déclaration d’attribut | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97a98ee-ffc0-42f0-a9a6-b0717b39c798
caps.latest.revision: 5
ms.openlocfilehash: 7aa6fa407e509a31c4066c4f73ae01b02b2f338c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365338"
---
# <a name="outputtype-attribute-declaration"></a>Déclaration de l’attribut OutputType

L’attribut `OutputType` identifie les types de .NET Framework retournés par une applet de commande, une fonction ou un script.

## <a name="syntax"></a>Syntaxe

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a>Paramètres

Type (`string[]` ou `Type[]`) requis. Spécifie les types retournés par la fonction d’applet de commande, ou le script.

ParameterSetName (String []) facultatif. Spécifie les jeux de paramètres qui retournent les types spécifiés dans le paramètre `type`.

providerCmdlet facultatif. Spécifie l’applet de commande du fournisseur qui retourne les types spécifiés dans le paramètre `type`.

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
