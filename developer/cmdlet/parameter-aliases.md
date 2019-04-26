---
title: Alias de paramètre | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067584"
---
# <a name="parameter-aliases"></a>Alias de paramètres

Paramètres de l’applet de commande peuvent également avoir des alias. Vous pouvez utiliser l’alias au lieu des noms de paramètres lorsque vous tapez, ou spécifiez le paramètre dans une commande.

## <a name="benefits-of-using-aliases"></a>Avantages de l’utilisation d’alias

Ajout d’alias aux paramètres offre les avantages suivants.

- Vous pouvez fournir un raccourci afin que l’utilisateur ne dispose pas d’utiliser le nom de paramètre complet lorsque l’applet de commande est appelée. Par exemple, vous pouvez utiliser l’alias « CN » au lieu du nom de paramètre « ComputerName ».

- Vous pouvez définir plusieurs alias si vous souhaitez fournir des noms différents pour le même paramètre. Vous souhaiterez peut-être définir plusieurs alias si vous devez travailler avec plusieurs groupes d’utilisateurs qui font référence aux mêmes données de différentes façons.

- Vous pouvez fournir descendante compatibilité pour les scripts existants si le nom d’un paramètre change.

- À l’aide de l’attribut d’Alias, ainsi que l’attribut ValueFromPipelineByName, vous pouvez définir un paramètre qui permet à votre applet de commande à lier à différents types d’objets. Par exemple, supposons que vous disposiez de deux objets de types différents et le premier objet avait une propriété de l’enregistreur et le second objet avait une propriété de l’éditeur. Si votre applet de commande a un paramètre qui avait rédacteur et alias et l’applet de commande accepté l’entrée de pipeline en fonction de noms de propriété, votre applet de commande peut lier les deux objets en utilisant les deux alias de paramètre.

Pour plus d’informations sur les alias qui peut être utilisé avec des paramètres spécifiques, consultez [les noms de paramètres courants](./common-parameter-names.md).

## <a name="defining-parameter-aliases"></a>Définition d’alias de paramètre

Pour définir un alias pour un paramètre, déclarez l’attribut Alias, comme indiqué dans la déclaration de paramètre suivantes. Dans cet exemple, plusieurs alias sont définis pour le même paramètre. (Pour plus d’informations, consultez[comment déclarer des paramètres d’applet de commande](./how-to-declare-cmdlet-parameters.md).)

```csharp
[Alias("UN","Writer","Editor")]
[Parameter()]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="see-also"></a>Voir aussi

[Noms de paramètres courants](./common-parameter-names.md)

[Comment déclarer des paramètres de l’applet de commande](./how-to-declare-cmdlet-parameters.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
