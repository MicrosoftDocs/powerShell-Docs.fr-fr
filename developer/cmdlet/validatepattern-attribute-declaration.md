---
title: Déclaration d’attribut de ValidatePattern | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidatePattern
- ValidatePattern attribute, described
- ValidatePattern attribute
ms.assetid: 87b811be-6d93-4e7d-b9d0-c567a19bb0ef
caps.latest.revision: 13
ms.openlocfilehash: 5edcb65a6fbe1cb2fe2d0efe3f763fb84628b049
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858875"
---
# <a name="validatepattern-attribute-declaration"></a>Déclaration de l’attribut ValidatePattern

L’attribut ValidatePattern spécifie un modèle d’expression régulière qui valide l’argument d’un paramètre d’applet de commande. Cet attribut peut également être utilisé par les fonctions de Windows PowerShell.

Lorsque ValidatePattern est appelé au sein d’une applet de commande, le runtime Windows PowerShell convertit l’argument du paramètre d’applet de commande en une chaîne et compare ensuite cette chaîne pour le modèle fourni par l’attribut ValidatePattern. L’applet de commande est exécutée uniquement si correspond à la représentation sous forme de chaîne convertie de l’argument et le modèle fourni. Si elles ne correspondent pas, une erreur est levée par le runtime de Windows PowerShell.

## <a name="syntax"></a>Syntaxe

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a>Paramètres

`RegexString` ([System.String](/dotnet/api/System.String)) requis. Spécifie une expression régulière qui valide l’argument de paramètre.

Options ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) paramètre nommé facultatif. Spécifie une combinaison au niveau du bit de [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) indicateurs qui spécifient les options des expressions régulières.

## <a name="remarks"></a>Remarques

- Cet attribut peut être utilisé qu’une seule fois par le paramètre.

- Vous pouvez utiliser le `Option` paramètre de l’attribut à définir le modèle. Par exemple, vous pouvez rendre le modèle respecte la casse.

- Si cet attribut est appliqué à une collection, chaque élément dans la collection doit correspondre au modèle.

- L’attribut ValidatePattern est défini par le [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) classe.

## <a name="see-also"></a>Voir aussi

[System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
