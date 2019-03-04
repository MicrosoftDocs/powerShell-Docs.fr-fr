---
title: Attributs dans le Code de l’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853785"
---
# <a name="attributes-in-cmdlet-code"></a>Attributs dans le code des applets de commande

Pour utiliser les fonctionnalités courantes fournies par Windows PowerShell, les classes et les propriétés publiques définies dans le code de l’applet de commande sont décorées avec des attributs. Par exemple, la définition de classe suivante utilise l’attribut de l’applet de commande pour identifier la classe Microsoft .NET Framework dans lequel la **Get-Process** applet de commande est implémentée. (Cette applet de commande est utilisé comme exemple dans ce document et est similaire à la `Get-Process` applet de commande fournie par Windows PowerShell.)

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Ces attributs sont considérés comme des métadonnées, car leur implémentation est distincte de l’implémentation de code de l’applet de commande. Lorsque le runtime Windows PowerShell s’exécute l’applet de commande, il reconnaît les attributs et puis exécute l’action appropriée pour chaque attribut.

Même si vous voulez implémenter votre propre version de la fonctionnalité fournie par ces attributs, une conception de l’applet de commande bonne utilise ces fonctionnalités courantes.

Pour plus d’informations sur les différents attributs qui peuvent être déclarés dans vos applets de commande, consultez [Types d’attributs](./attribute-types.md).

## <a name="see-also"></a>Voir aussi

[Types d’attributs](./attribute-types.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
