---
title: OutputType, déclaration d’attribut | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a4cc874031bba092cfef6041bef0e19e6af3f09c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786541"
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
