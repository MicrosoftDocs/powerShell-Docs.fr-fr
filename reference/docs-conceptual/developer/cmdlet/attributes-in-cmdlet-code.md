---
title: Attributs dans le code d’applet de commande | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1f92e329d304754d5596cef0c95dc597aca3a538
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774913"
---
# <a name="attributes-in-cmdlet-code"></a>Attributs dans le code des applets de commande

Pour utiliser les fonctionnalités communes fournies par Windows PowerShell, les classes et les propriétés publiques définies dans le code de l’applet de commande sont décorées avec des attributs. Par exemple, la définition de classe suivante utilise l’attribut cmdlet pour identifier la classe Microsoft .NET Framework dans laquelle l’applet de commande **obtenir-proc** est implémentée. (Cette applet de commande est utilisée comme exemple dans ce document et est semblable à l' `Get-Process` applet de commande fournie par Windows PowerShell.)

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Ces attributs sont considérés comme des métadonnées, car leur implémentation est distincte de l’implémentation du code de l’applet de commande. Lorsque le runtime Windows PowerShell exécute l’applet de commande, il reconnaît les attributs, puis effectue l’action appropriée pour chaque attribut.

Bien que vous souhaitiez implémenter votre propre version de la fonctionnalité fournie par ces attributs, une bonne conception d’applets de commande utilise ces fonctionnalités communes.

Pour plus d’informations sur les différents attributs qui peuvent être déclarés dans vos applets de commande, consultez [types d’attributs](./attribute-types.md).

## <a name="see-also"></a>Voir aussi

[Types d’attributs](./attribute-types.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
