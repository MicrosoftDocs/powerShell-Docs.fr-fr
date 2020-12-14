---
ms.date: 09/13/2016
ms.topic: reference
title: Déclaration de l’attribut Alias
description: Déclaration de l’attribut Alias
ms.openlocfilehash: f2fe49578da2c795643b1f80fa44deefe1dbff09
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668301"
---
# <a name="alias-attribute-declaration"></a><span data-ttu-id="09db4-103">Déclaration de l’attribut Alias</span><span class="sxs-lookup"><span data-stu-id="09db4-103">Alias Attribute Declaration</span></span>

<span data-ttu-id="09db4-104">L’attribut alias permet à l’utilisateur de spécifier des noms différents pour un paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="09db4-104">The Alias attribute allows the user to specify different names for a cmdlet parameter.</span></span> <span data-ttu-id="09db4-105">Les alias peuvent être utilisés pour fournir des raccourcis pour un nom de paramètre, ou ils peuvent fournir des noms différents qui conviennent à différents scénarios.</span><span class="sxs-lookup"><span data-stu-id="09db4-105">Aliases can be used to provide shortcuts for a parameter name, or they can provide different names that are appropriate for different scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="09db4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09db4-106">Syntax</span></span>

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a><span data-ttu-id="09db4-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="09db4-107">Parameters</span></span>

<span data-ttu-id="09db4-108">`aliasName` (String []) Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="09db4-108">`aliasName` (String[]) Required.</span></span> <span data-ttu-id="09db4-109">Spécifie un jeu de noms d’alias séparés par des virgules pour le paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="09db4-109">Specifies a set of comma-separated alias names for the cmdlet parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="09db4-110">Notes</span><span class="sxs-lookup"><span data-stu-id="09db4-110">Remarks</span></span>

- <span data-ttu-id="09db4-111">L’attribut alias est utilisé avec l’attribut Parameter lorsque vous spécifiez un paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="09db4-111">The Alias attribute is used with the Parameter attribute when you specify a cmdlet parameter.</span></span> <span data-ttu-id="09db4-112">Pour plus d’informations sur la façon de déclarer ces attributs, consultez [comment déclarer des paramètres d’applet de](./how-to-declare-cmdlet-parameters.md)commande.</span><span class="sxs-lookup"><span data-stu-id="09db4-112">For more information about how to declare these attributes, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="09db4-113">Chaque nom d’alias doit être unique au sein d’une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="09db4-113">Each alias name must be unique within a cmdlet.</span></span> <span data-ttu-id="09db4-114">Windows PowerShell ne vérifie pas les noms d’alias en double.</span><span class="sxs-lookup"><span data-stu-id="09db4-114">Windows PowerShell does not check for duplicate alias names.</span></span>

- <span data-ttu-id="09db4-115">L’attribut alias est utilisé une fois pour chaque paramètre d’une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="09db4-115">The Alias attribute is used once for each parameter in a cmdlet.</span></span>

- <span data-ttu-id="09db4-116">L’attribut alias est défini par la classe [System. Management. Automation. AliasAttribute](/dotnet/api/System.Management.Automation.AliasAttribute) .</span><span class="sxs-lookup"><span data-stu-id="09db4-116">The Alias attribute is defined by the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="09db4-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09db4-117">See Also</span></span>

[<span data-ttu-id="09db4-118">Alias de paramètres</span><span class="sxs-lookup"><span data-stu-id="09db4-118">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="09db4-119">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="09db4-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
