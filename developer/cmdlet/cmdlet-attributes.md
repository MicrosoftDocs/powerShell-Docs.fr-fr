---
title: Attributs de l’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [PowerShell SDK]
- attributes [PowerShell SDK], described
ms.assetid: d3f4f652-d929-4c27-9358-9baa390a094c
caps.latest.revision: 14
ms.openlocfilehash: b06faf7204213b383b25685837941ad63dcb225b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853915"
---
# <a name="cmdlet-attributes"></a>Attributs des applets de commande

Windows PowerShell définit plusieurs attributs que vous pouvez utiliser pour ajouter des fonctionnalités communes à vos applets de commande sans avoir à implémenter cette fonctionnalité dans votre propre code. Cela inclut l’attribut de l’applet de commande qui identifie une classe Microsoft .NET Framework en tant qu’une classe d’applet de commande, l’attribut OutputType qui spécifie les types .NET Framework retournés par l’applet de commande, l’attribut de paramètre qui identifie les propriétés publiques en tant qu’applet de commande paramètres et bien plus encore.

## <a name="in-this-section"></a>Dans cette section

[Attributs dans le Code de l’applet de commande](./attributes-in-cmdlet-code.md) décrit l’avantage d’utiliser des attributs dans le code de l’applet de commande.

[Types d’attributs](./attribute-types.md) décrit les différents attributs peuvent décorer une classe de l’applet de commande.

[Déclaration d’attribut alias](./alias-attribute-declaration.md) explique comment définir des alias pour un nom de paramètre d’applet de commande.

[Déclaration d’attribut cmdlet](./cmdlet-attribute-declaration.md) explique comment définir une classe .NET Framework en tant qu’une applet de commande.

[Informations d’identification de la déclaration d’attribut](./credential-attribute-declaration.md) décrit comment ajouter la prise en charge pour la conversion d’entrée de chaîne dans un [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objet.

[L’attribut OutputType déclaration](./outputtype-attribute-declaration.md) explique comment spécifier les types .NET Framework retournés par l’applet de commande.

[Déclaration d’attribut de paramètre](./parameter-attribute-declaration.md) explique comment définir les paramètres d’applet de commande.

[Déclaration d’attribut ValidateCount](./validatecount-attribute-declaration.md) décrit comment définir le nombre d’arguments est autorisé pour un paramètre.

[Déclaration d’attribut ValidateLength](./validatelength-attribute-declaration.md) explique comment définir la longueur (en caractères) d’un argument de paramètre.

[Déclaration d’attribut ValidatePattern](./validatepattern-attribute-declaration.md) explique comment définir des modèles pour un argument de paramètre valides.

[Déclaration d’attribut ValidateRange](./validaterange-attribute-declaration.md) décrit comment définir la plage valide pour un argument de paramètre.

[Déclaration d’attribut ValidateSet](./validateset-attribute-declaration.md) décrit comment définir les valeurs possibles pour un argument de paramètre.

## <a name="reference"></a>Référence

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
