---
title: Attributs dans le code d’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369998"
---
# <a name="attributes-in-cmdlet-code"></a><span data-ttu-id="d0ea3-102">Attributs dans le code des applets de commande</span><span class="sxs-lookup"><span data-stu-id="d0ea3-102">Attributes in Cmdlet Code</span></span>

<span data-ttu-id="d0ea3-103">Pour utiliser les fonctionnalités communes fournies par Windows PowerShell, les classes et les propriétés publiques définies dans le code de l’applet de commande sont décorées avec des attributs.</span><span class="sxs-lookup"><span data-stu-id="d0ea3-103">To use the common functionality provided by Windows PowerShell, the classes and public properties defined in the cmdlet code are decorated with attributes.</span></span> <span data-ttu-id="d0ea3-104">Par exemple, la définition de classe suivante utilise l’attribut cmdlet pour identifier la classe Microsoft .NET Framework dans laquelle l’applet de commande **obtenir-proc** est implémentée.</span><span class="sxs-lookup"><span data-stu-id="d0ea3-104">For example, the following class definition uses the Cmdlet attribute to identify the Microsoft .NET Framework class in which the **Get-Proc** cmdlet is implemented.</span></span> <span data-ttu-id="d0ea3-105">(Cette applet de commande est utilisée comme exemple dans ce document et est semblable à l’applet de commande `Get-Process` fournie par Windows PowerShell.)</span><span class="sxs-lookup"><span data-stu-id="d0ea3-105">(This cmdlet is used as an example in this document, and is similar to the `Get-Process` cmdlet provided by Windows PowerShell.)</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="d0ea3-106">Ces attributs sont considérés comme des métadonnées, car leur implémentation est distincte de l’implémentation du code de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d0ea3-106">These attributes are considered metadata because their implementation is separate from the implementation of the cmdlet code.</span></span> <span data-ttu-id="d0ea3-107">Lorsque le runtime Windows PowerShell exécute l’applet de commande, il reconnaît les attributs, puis effectue l’action appropriée pour chaque attribut.</span><span class="sxs-lookup"><span data-stu-id="d0ea3-107">When the Windows PowerShell runtime runs the cmdlet, it recognizes the attributes and then performs the appropriate action for each attribute.</span></span>

<span data-ttu-id="d0ea3-108">Bien que vous souhaitiez implémenter votre propre version de la fonctionnalité fournie par ces attributs, une bonne conception d’applets de commande utilise ces fonctionnalités communes.</span><span class="sxs-lookup"><span data-stu-id="d0ea3-108">Although you might want to implement your own version of the functionality provided by these attributes, a good cmdlet design uses these common functionalities.</span></span>

<span data-ttu-id="d0ea3-109">Pour plus d’informations sur les différents attributs qui peuvent être déclarés dans vos applets de commande, consultez [types d’attributs](./attribute-types.md).</span><span class="sxs-lookup"><span data-stu-id="d0ea3-109">For more information about the different attributes that can be declared in your cmdlets, see [Attribute Types](./attribute-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d0ea3-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0ea3-110">See Also</span></span>

[<span data-ttu-id="d0ea3-111">Types d’attributs</span><span class="sxs-lookup"><span data-stu-id="d0ea3-111">Attribute Types</span></span>](./attribute-types.md)

[<span data-ttu-id="d0ea3-112">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d0ea3-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
