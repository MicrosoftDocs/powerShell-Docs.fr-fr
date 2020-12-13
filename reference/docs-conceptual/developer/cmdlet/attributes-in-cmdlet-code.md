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
# <a name="attributes-in-cmdlet-code"></a><span data-ttu-id="ea2be-103">Attributs dans le code des applets de commande</span><span class="sxs-lookup"><span data-stu-id="ea2be-103">Attributes in Cmdlet Code</span></span>

<span data-ttu-id="ea2be-104">Pour utiliser les fonctionnalités communes fournies par Windows PowerShell, les classes et les propriétés publiques définies dans le code de l’applet de commande sont décorées avec des attributs.</span><span class="sxs-lookup"><span data-stu-id="ea2be-104">To use the common functionality provided by Windows PowerShell, the classes and public properties defined in the cmdlet code are decorated with attributes.</span></span> <span data-ttu-id="ea2be-105">Par exemple, la définition de classe suivante utilise l’attribut cmdlet pour identifier la classe Microsoft .NET Framework dans laquelle l’applet de commande **obtenir-proc** est implémentée.</span><span class="sxs-lookup"><span data-stu-id="ea2be-105">For example, the following class definition uses the Cmdlet attribute to identify the Microsoft .NET Framework class in which the **Get-Proc** cmdlet is implemented.</span></span> <span data-ttu-id="ea2be-106">(Cette applet de commande est utilisée comme exemple dans ce document et est semblable à l' `Get-Process` applet de commande fournie par Windows PowerShell.)</span><span class="sxs-lookup"><span data-stu-id="ea2be-106">(This cmdlet is used as an example in this document, and is similar to the `Get-Process` cmdlet provided by Windows PowerShell.)</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="ea2be-107">Ces attributs sont considérés comme des métadonnées, car leur implémentation est distincte de l’implémentation du code de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ea2be-107">These attributes are considered metadata because their implementation is separate from the implementation of the cmdlet code.</span></span> <span data-ttu-id="ea2be-108">Lorsque le runtime Windows PowerShell exécute l’applet de commande, il reconnaît les attributs, puis effectue l’action appropriée pour chaque attribut.</span><span class="sxs-lookup"><span data-stu-id="ea2be-108">When the Windows PowerShell runtime runs the cmdlet, it recognizes the attributes and then performs the appropriate action for each attribute.</span></span>

<span data-ttu-id="ea2be-109">Bien que vous souhaitiez implémenter votre propre version de la fonctionnalité fournie par ces attributs, une bonne conception d’applets de commande utilise ces fonctionnalités communes.</span><span class="sxs-lookup"><span data-stu-id="ea2be-109">Although you might want to implement your own version of the functionality provided by these attributes, a good cmdlet design uses these common functionalities.</span></span>

<span data-ttu-id="ea2be-110">Pour plus d’informations sur les différents attributs qui peuvent être déclarés dans vos applets de commande, consultez [types d’attributs](./attribute-types.md).</span><span class="sxs-lookup"><span data-stu-id="ea2be-110">For more information about the different attributes that can be declared in your cmdlets, see [Attribute Types](./attribute-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ea2be-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea2be-111">See Also</span></span>

[<span data-ttu-id="ea2be-112">Types d’attributs</span><span class="sxs-lookup"><span data-stu-id="ea2be-112">Attribute Types</span></span>](./attribute-types.md)

[<span data-ttu-id="ea2be-113">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ea2be-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
