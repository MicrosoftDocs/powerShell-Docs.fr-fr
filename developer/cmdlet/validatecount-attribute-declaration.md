---
title: Déclaration d’attribut de ValidateCount | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: ffc45f6b80a2b7ed22f27d083d042b1de7f353f6
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59983896"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="b2159-102">Déclaration de l’attribut ValidateCount</span><span class="sxs-lookup"><span data-stu-id="b2159-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="b2159-103">L’attribut ValidateCount Spécifie le nombre minimal et maximal d’arguments autorisés pour un paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b2159-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="b2159-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2159-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="b2159-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b2159-105">Parameters</span></span>

<span data-ttu-id="b2159-106">`MinLength` ([System.Int32][]) requis.</span><span class="sxs-lookup"><span data-stu-id="b2159-106">`MinLength` ([System.Int32][]) Required.</span></span> <span data-ttu-id="b2159-107">Spécifie le nombre minimal d’arguments.</span><span class="sxs-lookup"><span data-stu-id="b2159-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="b2159-108">`MaxLength`([System.Int32][]) requis.</span><span class="sxs-lookup"><span data-stu-id="b2159-108">`MaxLength`([System.Int32][]) Required.</span></span> <span data-ttu-id="b2159-109">Spécifie le nombre maximal d’arguments.</span><span class="sxs-lookup"><span data-stu-id="b2159-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="b2159-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="b2159-110">Remarks</span></span>

- <span data-ttu-id="b2159-111">Pour plus d’informations sur la façon de déclarer cet attribut, consultez [comment valider un nombre d’arguments][].</span><span class="sxs-lookup"><span data-stu-id="b2159-111">For more information about how to declare this attribute, see [How to Validate an Argument Count][].</span></span>

- <span data-ttu-id="b2159-112">Lorsque cet attribut n’est pas appelé, le paramètre d’applet de commande correspondant peut avoir n’importe quel nombre d’arguments.</span><span class="sxs-lookup"><span data-stu-id="b2159-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="b2159-113">Le runtime Windows PowerShell génère une erreur dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="b2159-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="b2159-114">Le `MinLength` et `MaxLength` des paramètres d’attribut ne sont pas de type [System.Int32][].</span><span class="sxs-lookup"><span data-stu-id="b2159-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32][].</span></span>

    - <span data-ttu-id="b2159-115">La valeur de la `MaxLength` paramètre d’attribut est inférieure à la valeur de la `MinLength` paramètre d’attribut.</span><span class="sxs-lookup"><span data-stu-id="b2159-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="b2159-116">L’attribut ValidateCount est défini par le [System.Management.Automation.ValidateCountAttribute][] classe.</span><span class="sxs-lookup"><span data-stu-id="b2159-116">The ValidateCount attribute is defined by the [System.Management.Automation.ValidateCountAttribute][] class.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2159-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2159-117">See Also</span></span>

<span data-ttu-id="b2159-118">[System.Management.Automation.ValidateCountAttribute][]</span><span class="sxs-lookup"><span data-stu-id="b2159-118">[System.Management.Automation.ValidateCountAttribute][]</span></span>

<span data-ttu-id="b2159-119">[Comment valider un nombre d’arguments][]</span><span class="sxs-lookup"><span data-stu-id="b2159-119">[How to Validate an Argument Count][]</span></span>

<span data-ttu-id="b2159-120">[Écriture d’une applet de commande Windows PowerShell][]</span><span class="sxs-lookup"><span data-stu-id="b2159-120">[Writing a Windows PowerShell Cmdlet][]</span></span>

[Comment valider un nombre d’arguments]: how-to-validate-an-argument-count.md
[How to Validate an Argument Count]: how-to-validate-an-argument-count.md
[Écriture d’une applet de commande Windows PowerShell]: writing-a-windows-powershell-cmdlet.md
[Writing a Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
