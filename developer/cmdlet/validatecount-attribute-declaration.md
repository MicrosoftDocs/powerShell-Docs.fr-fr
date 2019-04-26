---
title: Déclaration d’attribut de ValidateCount | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: ffc45f6b80a2b7ed22f27d083d042b1de7f353f6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067176"
---
# <a name="validatecount-attribute-declaration"></a>Déclaration de l’attribut ValidateCount

L’attribut ValidateCount Spécifie le nombre minimal et maximal d’arguments autorisés pour un paramètre d’applet de commande.

## <a name="syntax"></a>Syntaxe

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Paramètres

`MinLength` ([System.Int32][]) requis. Spécifie le nombre minimal d’arguments.

`MaxLength`([System.Int32][]) requis. Spécifie le nombre maximal d’arguments.

## <a name="remarks"></a>Remarques

- Pour plus d’informations sur la façon de déclarer cet attribut, consultez [comment valider un nombre d’arguments][].

- Lorsque cet attribut n’est pas appelé, le paramètre d’applet de commande correspondant peut avoir n’importe quel nombre d’arguments.

- Le runtime Windows PowerShell génère une erreur dans les conditions suivantes :

    - Le `MinLength` et `MaxLength` des paramètres d’attribut ne sont pas de type [System.Int32][].

    - La valeur de la `MaxLength` paramètre d’attribut est inférieure à la valeur de la `MinLength` paramètre d’attribut.

- L’attribut ValidateCount est défini par le [System.Management.Automation.ValidateCountAttribute][] classe.

## <a name="see-also"></a>Voir aussi

[System.Management.Automation.ValidateCountAttribute][]

[Comment valider un nombre d’arguments][]

[Écriture d’une applet de commande Windows PowerShell][]

[Comment valider un nombre d’arguments]: how-to-validate-an-argument-count.md
[Écriture d’une applet de commande Windows PowerShell]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
