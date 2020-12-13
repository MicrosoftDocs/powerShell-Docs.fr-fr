---
ms.date: 09/13/2016
ms.topic: reference
title: Déclaration de l’attribut OutputType
description: Déclaration de l’attribut OutputType
ms.openlocfilehash: b5e33346e9ac29c13323781d62daffab892573a4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646451"
---
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="548e3-103">Déclaration de l’attribut OutputType</span><span class="sxs-lookup"><span data-stu-id="548e3-103">OutputType Attribute Declaration</span></span>

<span data-ttu-id="548e3-104">L' `OutputType` attribut identifie les types de .NET Framework retournés par une applet de commande, une fonction ou un script.</span><span class="sxs-lookup"><span data-stu-id="548e3-104">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="548e3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="548e3-105">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="548e3-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="548e3-106">Parameters</span></span>

<span data-ttu-id="548e3-107">Type ( `string[]` ou `Type[]` ) requis.</span><span class="sxs-lookup"><span data-stu-id="548e3-107">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="548e3-108">Spécifie les types retournés par la fonction d’applet de commande, ou le script.</span><span class="sxs-lookup"><span data-stu-id="548e3-108">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="548e3-109">ParameterSetName (String []) facultatif.</span><span class="sxs-lookup"><span data-stu-id="548e3-109">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="548e3-110">Spécifie les jeux de paramètres qui retournent les types spécifiés dans le `type` paramètre.</span><span class="sxs-lookup"><span data-stu-id="548e3-110">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="548e3-111">providerCmdlet facultatif.</span><span class="sxs-lookup"><span data-stu-id="548e3-111">providerCmdlet Optional.</span></span> <span data-ttu-id="548e3-112">Spécifie l’applet de commande du fournisseur qui retourne les types spécifiés dans le `type` paramètre.</span><span class="sxs-lookup"><span data-stu-id="548e3-112">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="548e3-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="548e3-113">See Also</span></span>

[<span data-ttu-id="548e3-114">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="548e3-114">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
