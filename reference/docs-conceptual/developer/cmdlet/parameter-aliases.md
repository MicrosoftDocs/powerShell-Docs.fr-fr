---
title: Alias de paramètres | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e320eeb4d2ab91acf2116fdc817a50e93c82aead
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781985"
---
# <a name="parameter-aliases"></a>Alias de paramètres

Les paramètres d’applet de commande peuvent également avoir des alias. Vous pouvez utiliser les alias à la place des noms de paramètres lorsque vous tapez ou spécifiez le paramètre dans une commande.

## <a name="benefits-of-using-aliases"></a>Avantages de l’utilisation d’alias

L’ajout d’alias aux paramètres offre les avantages suivants.

- Vous pouvez fournir un raccourci pour que l’utilisateur n’ait pas à utiliser le nom de paramètre complet lorsque l’applet de commande est appelée. Par exemple, vous pouvez utiliser l’alias « CN » à la place du nom de paramètre « ComputerName ».

- Vous pouvez définir plusieurs alias si vous souhaitez fournir des noms différents pour le même paramètre. Vous pouvez définir plusieurs alias si vous devez utiliser plusieurs groupes d’utilisateurs qui font référence aux mêmes données de différentes façons.

- Vous pouvez fournir une compatibilité descendante pour les scripts existants si le nom d’un paramètre change.

- En utilisant l’attribut alias avec l’attribut ValueFromPipelineByName, vous pouvez définir un paramètre qui permet à votre applet de commande de créer une liaison avec différents types d’objets. Par exemple, imaginons que vous disposiez de deux objets de types différents et que le premier objet comportait une propriété Writer et que le deuxième objet contenait une propriété Editor. Si votre applet de commande avait un paramètre qui avait des alias de Writer et d’éditeur et que l’applet de commande acceptait l’entrée de pipeline en fonction des noms de propriété, votre applet de commande pourrait lier les deux objets à l’aide des deux alias de paramètres.

Pour plus d’informations sur les alias qui peuvent être utilisés avec des paramètres spécifiques, consultez [noms de paramètres communs](./common-parameter-names.md).

## <a name="defining-parameter-aliases"></a>Définition des alias de paramètres

Pour définir un alias pour un paramètre, déclarez l’attribut alias, comme indiqué dans la déclaration de paramètre suivante. Dans cet exemple, plusieurs alias sont définis pour le même paramètre. (Pour plus d’informations, consultez[comment déclarer des paramètres d’applet de](./how-to-declare-cmdlet-parameters.md)commande.)

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

[Guide pratique pour déclarer des paramètres d’applet de commande](./how-to-declare-cmdlet-parameters.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
