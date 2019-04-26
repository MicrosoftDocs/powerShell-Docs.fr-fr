---
title: Déclaration d’attribut OutputType | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97a98ee-ffc0-42f0-a9a6-b0717b39c798
caps.latest.revision: 5
ms.openlocfilehash: 7aa6fa407e509a31c4066c4f73ae01b02b2f338c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067601"
---
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="b0465-102">Déclaration de l’attribut OutputType</span><span class="sxs-lookup"><span data-stu-id="b0465-102">OutputType Attribute Declaration</span></span>

<span data-ttu-id="b0465-103">Le `OutputType` attribut identifie les types .NET Framework retournés par une applet de commande, une fonction ou un script.</span><span class="sxs-lookup"><span data-stu-id="b0465-103">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="b0465-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0465-104">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="b0465-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b0465-105">Parameters</span></span>

<span data-ttu-id="b0465-106">Type (`string[]` ou `Type[]`) requis.</span><span class="sxs-lookup"><span data-stu-id="b0465-106">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="b0465-107">Spécifie les types retournés par la fonction de l’applet de commande, ou un script.</span><span class="sxs-lookup"><span data-stu-id="b0465-107">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="b0465-108">ParameterSetName (que facultatif.</span><span class="sxs-lookup"><span data-stu-id="b0465-108">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="b0465-109">Spécifie les jeux de paramètres qui retournent les types spécifiés dans le `type` paramètre.</span><span class="sxs-lookup"><span data-stu-id="b0465-109">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="b0465-110">providerCmdlet facultatif.</span><span class="sxs-lookup"><span data-stu-id="b0465-110">providerCmdlet Optional.</span></span> <span data-ttu-id="b0465-111">Spécifie l’applet de commande fournisseur qui retourne les types spécifiés dans le `type` paramètre.</span><span class="sxs-lookup"><span data-stu-id="b0465-111">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0465-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0465-112">See Also</span></span>

[<span data-ttu-id="b0465-113">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b0465-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
