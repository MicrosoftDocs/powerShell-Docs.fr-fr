---
title: Déclaration d’attribut de ValidateSet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.assetid: 4a6f97ab-45b2-4f3d-84d4-30acf8e074d0
caps.latest.revision: 12
ms.openlocfilehash: b036f39cd01ffe4b4ce7db9627cb6da0d5327190
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067062"
---
# <a name="validateset-attribute-declaration"></a>Déclaration de l’attribut ValidateSet

L’attribut ValidateSetAttribute spécifie un ensemble de valeurs possibles pour un argument de paramètre d’applet de commande. Cet attribut peut également être utilisé par les fonctions de Windows PowerShell.

Lorsque cet attribut est spécifié, le runtime Windows PowerShell détermine si l’argument fourni pour le paramètre d’applet de commande correspond à un élément dans l’ensemble de l’élément fourni. L’applet de commande est exécutée uniquement si l’argument de paramètre correspond à un élément dans le jeu. Si aucune correspondance n’est trouvée, une erreur est levée par le runtime de Windows PowerShell.

## <a name="syntax"></a>Syntaxe

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a>Paramètres

`ValidValues` ([System.String](/dotnet/api/System.String)) requis. Spécifie les valeurs d’élément de paramètre valide. L’exemple suivant montre comment spécifier un seul élément ou plusieurs éléments.

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif. La valeur par défaut `true` indique que la casse est ignorée. La valeur `false` rend l’applet de commande qui respecte la casse.

## <a name="remarks"></a>Remarques

- Cet attribut peut être utilisé qu’une seule fois par le paramètre.

- Si la valeur du paramètre est un tableau, chaque élément du tableau doit correspondre à un élément de l’ensemble d’attributs.

- L’attribut ValidateSetAttribute est défini par le [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) classe.

## <a name="see-also"></a>Voir aussi

[System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
