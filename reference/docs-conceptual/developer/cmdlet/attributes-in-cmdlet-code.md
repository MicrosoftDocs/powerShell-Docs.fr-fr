---
ms.date: 09/13/2016
ms.topic: reference
title: Attributs dans le code des applets de commande
description: Attributs dans le code des applets de commande
ms.openlocfilehash: 296bb8bcb06ef660e97dc792d1ecf596cc7c2930
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653643"
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
