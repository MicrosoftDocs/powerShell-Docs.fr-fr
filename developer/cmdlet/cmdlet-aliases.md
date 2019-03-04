---
title: Alias d’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d70864-33fb-49ce-8054-c41ba19fd554
caps.latest.revision: 11
ms.openlocfilehash: 32f45702cc0d28e6652ef61ebdbe085291013408
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860505"
---
# <a name="cmdlet-aliases"></a><span data-ttu-id="cde2a-102">Alias des applets de commande</span><span class="sxs-lookup"><span data-stu-id="cde2a-102">Cmdlet Aliases</span></span>

<span data-ttu-id="cde2a-103">Vous pouvez utiliser des alias d’applet de commande pour améliorer l’expérience utilisateur de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="cde2a-103">You can use cmdlet aliases to improve the cmdlet user experience.</span></span> <span data-ttu-id="cde2a-104">Vous pouvez ajouter des alias pour les applets de commande fréquemment utilisées pour réduire la frappe et pour le rendre plus facile à effectuer des tâches rapidement.</span><span class="sxs-lookup"><span data-stu-id="cde2a-104">You can add aliases to frequently used cmdlets to reduce typing and to make it easier to complete tasks quickly.</span></span> <span data-ttu-id="cde2a-105">Vous pouvez inclure les alias intégrés dans vos applets de commande, ou les utilisateurs peuvent définir leurs propres alias personnalisés.</span><span class="sxs-lookup"><span data-stu-id="cde2a-105">You can include built-in aliases in your cmdlets, or users can define their own custom aliases.</span></span>

<span data-ttu-id="cde2a-106">Par exemple, le [Get-Command](/powershell/module/microsoft.powershell.core/get-command) applet de commande intègre `gcm` alias.</span><span class="sxs-lookup"><span data-stu-id="cde2a-106">For example, the [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet has a built-in `gcm` alias.</span></span> <span data-ttu-id="cde2a-107">Vous pouvez également utiliser des alias pour ajouter des noms de commande à partir d’autres langages afin que les utilisateurs n’ont pas à apprendre de nouvelles commandes.</span><span class="sxs-lookup"><span data-stu-id="cde2a-107">You can also use aliases to add command names from other languages so that users do not have to learn new commands.</span></span>

## <a name="alias-guidelines"></a><span data-ttu-id="cde2a-108">Instructions d’alias</span><span class="sxs-lookup"><span data-stu-id="cde2a-108">Alias Guidelines</span></span>

<span data-ttu-id="cde2a-109">Suivez ces instructions lorsque vous créez des alias intégrés pour vos applets de commande :</span><span class="sxs-lookup"><span data-stu-id="cde2a-109">Follow these guidelines when you create built-in aliases for your cmdlets:</span></span>

- <span data-ttu-id="cde2a-110">Avant de vous attribuez les alias, démarrez Windows PowerShell et exécutez le [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) applet de commande pour afficher les alias qui sont déjà utilisés.</span><span class="sxs-lookup"><span data-stu-id="cde2a-110">Before you assign aliases, start Windows PowerShell, and then run the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet to see the aliases that are already used.</span></span>

- <span data-ttu-id="cde2a-111">Inclure un préfixe d’alias qui référence le verbe du nom d’applet de commande et un suffixe d’alias qui référence le substantif du nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="cde2a-111">Include an alias prefix that references the verb of the cmdlet name and an alias suffix that references the noun of the cmdlet name.</span></span> <span data-ttu-id="cde2a-112">Par exemple, l’alias pour le `Import-Module` applet de commande est « ipmo ».</span><span class="sxs-lookup"><span data-stu-id="cde2a-112">For example, the alias for the `Import-Module` cmdlet is "ipmo".</span></span> <span data-ttu-id="cde2a-113">Pour obtenir la liste de tous les verbes et de leurs alias, consultez [verbes d’applet de commande](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="cde2a-113">For a list of all the verbs and their aliases, see [Cmdlet Verbs](./approved-verbs-for-windows-powershell-commands.md).</span></span>

- <span data-ttu-id="cde2a-114">Pour les applets de commande qui ont le même verbe incluent le même préfixe de l’alias.</span><span class="sxs-lookup"><span data-stu-id="cde2a-114">For cmdlets that have the same verb, include the same alias prefix.</span></span> <span data-ttu-id="cde2a-115">Par exemple, les alias de toutes les cmdlets Windows PowerShell qui ont le verbe « Get » dans leur nom utilisent le préfixe « g ».</span><span class="sxs-lookup"><span data-stu-id="cde2a-115">For example, the aliases for all the Windows PowerShell cmdlets that have the "Get" verb in their name use the "g" prefix.</span></span>

- <span data-ttu-id="cde2a-116">Pour les applets de commande qui ont le même nom, inclure le même suffixe de l’alias.</span><span class="sxs-lookup"><span data-stu-id="cde2a-116">For cmdlets that have the same noun, include the same alias suffix.</span></span> <span data-ttu-id="cde2a-117">Par exemple, les alias de toutes les cmdlets Windows PowerShell qui comportent le mot « Session » dans leur nom utilisent le suffixe « sn ».</span><span class="sxs-lookup"><span data-stu-id="cde2a-117">For example, the aliases for all the Windows PowerShell cmdlets that have the "Session" noun in their name use the "sn" suffix.</span></span>

- <span data-ttu-id="cde2a-118">Pour les applets de commande qui sont équivalentes aux commandes dans d’autres langages, utilisez le nom de la commande.</span><span class="sxs-lookup"><span data-stu-id="cde2a-118">For cmdlets that are equivalent to commands in other languages, use the name of the command.</span></span>

- <span data-ttu-id="cde2a-119">En général, rendre aussi courte que possible.</span><span class="sxs-lookup"><span data-stu-id="cde2a-119">In general, make aliases as short as possible.</span></span> <span data-ttu-id="cde2a-120">Vérifiez que l’alias a au moins un caractère distinct pour le verbe et un caractère distinct pour le substantif.</span><span class="sxs-lookup"><span data-stu-id="cde2a-120">Make sure the alias has at least one distinct character for the verb and one distinct character for the noun.</span></span> <span data-ttu-id="cde2a-121">Ajouter plus de caractères que nécessaire pour rendre l’alias unique.</span><span class="sxs-lookup"><span data-stu-id="cde2a-121">Add more characters as needed to make the alias unique.</span></span>

## <a name="see-also"></a><span data-ttu-id="cde2a-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cde2a-122">See Also</span></span>

[<span data-ttu-id="cde2a-123">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cde2a-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
