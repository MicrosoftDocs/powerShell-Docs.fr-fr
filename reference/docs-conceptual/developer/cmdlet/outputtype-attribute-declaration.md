---
title: OutputType, déclaration d’attribut | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a4cc874031bba092cfef6041bef0e19e6af3f09c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786541"
---
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="82040-102">Déclaration de l’attribut OutputType</span><span class="sxs-lookup"><span data-stu-id="82040-102">OutputType Attribute Declaration</span></span>

<span data-ttu-id="82040-103">L' `OutputType` attribut identifie les types de .NET Framework retournés par une applet de commande, une fonction ou un script.</span><span class="sxs-lookup"><span data-stu-id="82040-103">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="82040-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82040-104">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="82040-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="82040-105">Parameters</span></span>

<span data-ttu-id="82040-106">Type ( `string[]` ou `Type[]` ) requis.</span><span class="sxs-lookup"><span data-stu-id="82040-106">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="82040-107">Spécifie les types retournés par la fonction d’applet de commande, ou le script.</span><span class="sxs-lookup"><span data-stu-id="82040-107">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="82040-108">ParameterSetName (String []) facultatif.</span><span class="sxs-lookup"><span data-stu-id="82040-108">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="82040-109">Spécifie les jeux de paramètres qui retournent les types spécifiés dans le `type` paramètre.</span><span class="sxs-lookup"><span data-stu-id="82040-109">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="82040-110">providerCmdlet facultatif.</span><span class="sxs-lookup"><span data-stu-id="82040-110">providerCmdlet Optional.</span></span> <span data-ttu-id="82040-111">Spécifie l’applet de commande du fournisseur qui retourne les types spécifiés dans le `type` paramètre.</span><span class="sxs-lookup"><span data-stu-id="82040-111">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="82040-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82040-112">See Also</span></span>

[<span data-ttu-id="82040-113">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="82040-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
