---
ms.date: 09/13/2016
ms.topic: reference
title: Attributs des applets de commande
description: Attributs des applets de commande
ms.openlocfilehash: 6a106f33cb34c6c33b88a981815543bc9af4e4ba
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653518"
---
# <a name="cmdlet-attributes"></a>Attributs des applets de commande

Windows PowerShell définit plusieurs attributs que vous pouvez utiliser pour ajouter des fonctionnalités communes à vos applets de commande sans implémenter cette fonctionnalité dans votre propre code. Cela comprend l’attribut d’applet de commande qui identifie une classe d’infrastructure Microsoft .NET en tant que classe d’applet de commande, l’attribut OutputType qui spécifie les types de .NET Framework retournés par l’applet de commande, l’attribut de paramètre qui identifie les propriétés publiques comme paramètres d’applet de commande, et bien plus encore.

## <a name="in-this-section"></a>Dans cette section

[Attributs dans le code d’applet de](./attributes-in-cmdlet-code.md) commande Décrit l’avantage de l’utilisation d’attributs dans le code de l’applet de commande.

[Types d’attributs](./attribute-types.md) Décrit les différents attributs qui peuvent décorer une classe d’applet de commande.

[Déclaration d’attribut d’alias](./alias-attribute-declaration.md) Décrit comment définir des alias pour un nom de paramètre d’applet de commande.

[Déclaration d’attribut d’applet](./cmdlet-attribute-declaration.md) de commande Décrit comment définir une classe .NET Framework en tant qu’applet de commande.

[Déclaration d’attribut Credential](./credential-attribute-declaration.md) Décrit comment ajouter la prise en charge de la conversion de l’entrée de chaîne en objet [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) .

[OutputType (déclaration d’attribut](./outputtype-attribute-declaration.md) ) Décrit comment spécifier les types de .NET Framework retournés par l’applet de commande.

[Déclaration d’attribut de paramètre](./parameter-attribute-declaration.md) Décrit comment définir les paramètres d’une applet de commande.

[Déclaration d’attribut ValidateCount](./validatecount-attribute-declaration.md) Décrit comment définir le nombre d’arguments autorisés pour un paramètre.

[Déclaration d’attribut ValidateLength](./validatelength-attribute-declaration.md) Décrit comment définir la longueur (en caractères) d’un argument de paramètre.

[Déclaration d’attribut ValidatePattern](./validatepattern-attribute-declaration.md) Décrit comment définir les modèles valides pour un argument de paramètre.

[Déclaration d’attribut ValidateRange](./validaterange-attribute-declaration.md) Décrit comment définir la plage valide pour un argument de paramètre.

[Déclaration d’attribut ValidateSet](./validateset-attribute-declaration.md) Décrit comment définir les valeurs possibles pour un argument de paramètre.

## <a name="reference"></a>Informations de référence

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
