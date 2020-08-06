---
title: Déclaration de l’attribut alias | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.openlocfilehash: 4c1ff34a244611173ca919a44d6598189b19dc98
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782410"
---
# <a name="alias-attribute-declaration"></a><span data-ttu-id="73d8e-102">Déclaration de l’attribut Alias</span><span class="sxs-lookup"><span data-stu-id="73d8e-102">Alias Attribute Declaration</span></span>

<span data-ttu-id="73d8e-103">L’attribut alias permet à l’utilisateur de spécifier des noms différents pour un paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="73d8e-103">The Alias attribute allows the user to specify different names for a cmdlet parameter.</span></span> <span data-ttu-id="73d8e-104">Les alias peuvent être utilisés pour fournir des raccourcis pour un nom de paramètre, ou ils peuvent fournir des noms différents qui conviennent à différents scénarios.</span><span class="sxs-lookup"><span data-stu-id="73d8e-104">Aliases can be used to provide shortcuts for a parameter name, or they can provide different names that are appropriate for different scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="73d8e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73d8e-105">Syntax</span></span>

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a><span data-ttu-id="73d8e-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="73d8e-106">Parameters</span></span>

<span data-ttu-id="73d8e-107">`aliasName`(String []) Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="73d8e-107">`aliasName` (String[]) Required.</span></span> <span data-ttu-id="73d8e-108">Spécifie un jeu de noms d’alias séparés par des virgules pour le paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="73d8e-108">Specifies a set of comma-separated alias names for the cmdlet parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="73d8e-109">Notes</span><span class="sxs-lookup"><span data-stu-id="73d8e-109">Remarks</span></span>

- <span data-ttu-id="73d8e-110">L’attribut alias est utilisé avec l’attribut Parameter lorsque vous spécifiez un paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="73d8e-110">The Alias attribute is used with the Parameter attribute when you specify a cmdlet parameter.</span></span> <span data-ttu-id="73d8e-111">Pour plus d’informations sur la façon de déclarer ces attributs, consultez [comment déclarer des paramètres d’applet de](./how-to-declare-cmdlet-parameters.md)commande.</span><span class="sxs-lookup"><span data-stu-id="73d8e-111">For more information about how to declare these attributes, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="73d8e-112">Chaque nom d’alias doit être unique au sein d’une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="73d8e-112">Each alias name must be unique within a cmdlet.</span></span> <span data-ttu-id="73d8e-113">Windows PowerShell ne vérifie pas les noms d’alias en double.</span><span class="sxs-lookup"><span data-stu-id="73d8e-113">Windows PowerShell does not check for duplicate alias names.</span></span>

- <span data-ttu-id="73d8e-114">L’attribut alias est utilisé une fois pour chaque paramètre d’une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="73d8e-114">The Alias attribute is used once for each parameter in a cmdlet.</span></span>

- <span data-ttu-id="73d8e-115">L’attribut alias est défini par la classe [System. Management. Automation. AliasAttribute](/dotnet/api/System.Management.Automation.AliasAttribute) .</span><span class="sxs-lookup"><span data-stu-id="73d8e-115">The Alias attribute is defined by the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="73d8e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73d8e-116">See Also</span></span>

[<span data-ttu-id="73d8e-117">Alias de paramètres</span><span class="sxs-lookup"><span data-stu-id="73d8e-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="73d8e-118">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="73d8e-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
