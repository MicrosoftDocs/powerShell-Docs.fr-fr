---
title: Déclaration d’attribut alias | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.assetid: d0df3a46-b1cc-42b9-beb1-e16bce254007
caps.latest.revision: 10
ms.openlocfilehash: 4d20672c5181c994c1b53624f6c42a301db11f26
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855045"
---
# <a name="alias-attribute-declaration"></a><span data-ttu-id="db76b-102">Déclaration de l’attribut Alias</span><span class="sxs-lookup"><span data-stu-id="db76b-102">Alias Attribute Declaration</span></span>

<span data-ttu-id="db76b-103">L’attribut d’Alias permet à l’utilisateur spécifier des noms différents pour un paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="db76b-103">The Alias attribute allows the user to specify different names for a cmdlet parameter.</span></span> <span data-ttu-id="db76b-104">Alias peuvent être utilisés pour fournir des raccourcis pour un nom de paramètre, ou ils peuvent fournir des noms différents qui sont appropriés pour différents scénarios.</span><span class="sxs-lookup"><span data-stu-id="db76b-104">Aliases can be used to provide shortcuts for a parameter name, or they can provide different names that are appropriate for different scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="db76b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db76b-105">Syntax</span></span>

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a><span data-ttu-id="db76b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="db76b-106">Parameters</span></span>

<span data-ttu-id="db76b-107">`aliasName` (Qu' Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="db76b-107">`aliasName` (String[]) Required.</span></span> <span data-ttu-id="db76b-108">Spécifie un ensemble de noms d’alias séparés par des virgules pour le paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="db76b-108">Specifies a set of comma-separated alias names for the cmdlet parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="db76b-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="db76b-109">Remarks</span></span>

- <span data-ttu-id="db76b-110">L’attribut de l’Alias est utilisé avec l’attribut de paramètre lorsque vous spécifiez un paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="db76b-110">The Alias attribute is used with the Parameter attribute when you specify a cmdlet parameter.</span></span> <span data-ttu-id="db76b-111">Pour plus d’informations sur la façon de déclarer ces attributs, consultez [comment déclarer des paramètres d’applet de commande](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="db76b-111">For more information about how to declare these attributes, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="db76b-112">Chaque nom d’alias doit être unique au sein d’une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="db76b-112">Each alias name must be unique within a cmdlet.</span></span> <span data-ttu-id="db76b-113">Windows PowerShell ne vérifie pas les noms d’alias en double.</span><span class="sxs-lookup"><span data-stu-id="db76b-113">Windows PowerShell does not check for duplicate alias names.</span></span>

- <span data-ttu-id="db76b-114">L’attribut de l’Alias est utilisé qu’une seule fois pour chaque paramètre dans une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="db76b-114">The Alias attribute is used once for each parameter in a cmdlet.</span></span>

- <span data-ttu-id="db76b-115">L’attribut de l’Alias est défini par le [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="db76b-115">The Alias attribute is defined by the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="db76b-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db76b-116">See Also</span></span>

[<span data-ttu-id="db76b-117">Alias de paramètre</span><span class="sxs-lookup"><span data-stu-id="db76b-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="db76b-118">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="db76b-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
