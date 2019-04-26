---
title: Déclaration d’attribut de ValidateRange | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.assetid: 1f8066e6-e5d3-4f4e-8948-a90af5dace82
caps.latest.revision: 11
ms.openlocfilehash: 155a406b9855c435041fe175ac7d983a4b4eb8b7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067108"
---
# <a name="validaterange-attribute-declaration"></a>Déclaration de l’attribut ValidateRange

L’attribut ValidateRange spécifie les valeurs minimales et maximales (plage) pour l’argument de paramètre d’applet de commande. Cet attribut peut également être utilisé par les fonctions de Windows PowerShell.

## <a name="syntax"></a>Syntaxe

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>Paramètres

`MinRange` ([System.Object](/dotnet/api/system.object)) requis. Spécifie la valeur minimale autorisée.

`MaxRange` ([System.Object](/dotnet/api/system.object)) requis. Spécifie la valeur maximale autorisée.

## <a name="remarks"></a>Remarques

- Le runtime Windows PowerShell génère une erreur de construction lorsque la valeur de la `MinRange` paramètre est supérieur à la valeur de la `MaxRange` paramètre.

- Le runtime de Windows PowerShell lève une erreur de validation dans les conditions suivantes :

    - Lorsque la valeur de l’argument est inférieure à la `MinRange` limite ou supérieur à la `MaxRange` limite.

    - Lorsque l’argument n’est pas du même type que le `MinRange` et le `MaxRange` paramètres.

- L’attribut ValidateRange est défini par le [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) classe.

## <a name="see-also"></a>Voir aussi

[System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
