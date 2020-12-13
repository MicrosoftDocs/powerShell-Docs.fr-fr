---
ms.date: 09/13/2016
ms.topic: reference
title: Alias des applets de commande
description: Alias des applets de commande
ms.openlocfilehash: 734553a9911aef256df563afa6abcdb23d7a62e6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660797"
---
# <a name="cmdlet-aliases"></a><span data-ttu-id="297ba-103">Alias des applets de commande</span><span class="sxs-lookup"><span data-stu-id="297ba-103">Cmdlet Aliases</span></span>

<span data-ttu-id="297ba-104">Vous pouvez utiliser des alias d’applet de commande pour améliorer l’expérience utilisateur de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="297ba-104">You can use cmdlet aliases to improve the cmdlet user experience.</span></span> <span data-ttu-id="297ba-105">Vous pouvez ajouter des alias aux cmdlets fréquemment utilisées pour réduire la saisie et faciliter l’exécution rapide des tâches.</span><span class="sxs-lookup"><span data-stu-id="297ba-105">You can add aliases to frequently used cmdlets to reduce typing and to make it easier to complete tasks quickly.</span></span> <span data-ttu-id="297ba-106">Vous pouvez inclure des alias intégrés dans vos applets de commande ou les utilisateurs peuvent définir leurs propres alias personnalisés.</span><span class="sxs-lookup"><span data-stu-id="297ba-106">You can include built-in aliases in your cmdlets, or users can define their own custom aliases.</span></span>

<span data-ttu-id="297ba-107">Par exemple, l’applet de [commande obtenir-Command](/powershell/module/microsoft.powershell.core/get-command) a un `gcm` alias intégré.</span><span class="sxs-lookup"><span data-stu-id="297ba-107">For example, the [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet has a built-in `gcm` alias.</span></span> <span data-ttu-id="297ba-108">Vous pouvez également utiliser des alias pour ajouter des noms de commande d’autres langues afin que les utilisateurs n’aient pas à apprendre de nouvelles commandes.</span><span class="sxs-lookup"><span data-stu-id="297ba-108">You can also use aliases to add command names from other languages so that users do not have to learn new commands.</span></span>

## <a name="alias-guidelines"></a><span data-ttu-id="297ba-109">Instructions relatives aux alias</span><span class="sxs-lookup"><span data-stu-id="297ba-109">Alias Guidelines</span></span>

<span data-ttu-id="297ba-110">Suivez ces instructions lorsque vous créez des alias intégrés pour vos applets de commande :</span><span class="sxs-lookup"><span data-stu-id="297ba-110">Follow these guidelines when you create built-in aliases for your cmdlets:</span></span>

- <span data-ttu-id="297ba-111">Avant d’assigner des alias, démarrez Windows PowerShell, puis exécutez l’applet de commande [obtenir-alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) pour voir les alias déjà utilisés.</span><span class="sxs-lookup"><span data-stu-id="297ba-111">Before you assign aliases, start Windows PowerShell, and then run the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet to see the aliases that are already used.</span></span>

- <span data-ttu-id="297ba-112">Incluez un préfixe d’alias qui référence le verbe du nom de l’applet de commande et un suffixe d’alias qui référence le nom du nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="297ba-112">Include an alias prefix that references the verb of the cmdlet name and an alias suffix that references the noun of the cmdlet name.</span></span> <span data-ttu-id="297ba-113">Par exemple, l’alias de l' `Import-Module` applet de commande est « Bureau à pas ».</span><span class="sxs-lookup"><span data-stu-id="297ba-113">For example, the alias for the `Import-Module` cmdlet is "ipmo".</span></span> <span data-ttu-id="297ba-114">Pour obtenir la liste de tous les verbes et leurs alias, consultez [verbes d’applet](./approved-verbs-for-windows-powershell-commands.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="297ba-114">For a list of all the verbs and their aliases, see [Cmdlet Verbs](./approved-verbs-for-windows-powershell-commands.md).</span></span>

- <span data-ttu-id="297ba-115">Pour les applets de commande qui ont le même verbe, incluez le même préfixe d’alias.</span><span class="sxs-lookup"><span data-stu-id="297ba-115">For cmdlets that have the same verb, include the same alias prefix.</span></span> <span data-ttu-id="297ba-116">Par exemple, les alias de toutes les applets de commande Windows PowerShell dont le nom contient le verbe « obtenir » utilisent le préfixe « g ».</span><span class="sxs-lookup"><span data-stu-id="297ba-116">For example, the aliases for all the Windows PowerShell cmdlets that have the "Get" verb in their name use the "g" prefix.</span></span>

- <span data-ttu-id="297ba-117">Pour les applets de commande qui ont le même nom, incluez le même suffixe d’alias.</span><span class="sxs-lookup"><span data-stu-id="297ba-117">For cmdlets that have the same noun, include the same alias suffix.</span></span> <span data-ttu-id="297ba-118">Par exemple, les alias de toutes les applets de commande Windows PowerShell qui ont le nom « session » dans leur nom utilisent le suffixe « SN ».</span><span class="sxs-lookup"><span data-stu-id="297ba-118">For example, the aliases for all the Windows PowerShell cmdlets that have the "Session" noun in their name use the "sn" suffix.</span></span>

- <span data-ttu-id="297ba-119">Pour les applets de commande équivalentes aux commandes dans d’autres langues, utilisez le nom de la commande.</span><span class="sxs-lookup"><span data-stu-id="297ba-119">For cmdlets that are equivalent to commands in other languages, use the name of the command.</span></span>

- <span data-ttu-id="297ba-120">En général, rendez les alias aussi courts que possible.</span><span class="sxs-lookup"><span data-stu-id="297ba-120">In general, make aliases as short as possible.</span></span> <span data-ttu-id="297ba-121">Assurez-vous que l’alias a au moins un caractère distinct pour le verbe et un caractère distinct pour le nom.</span><span class="sxs-lookup"><span data-stu-id="297ba-121">Make sure the alias has at least one distinct character for the verb and one distinct character for the noun.</span></span> <span data-ttu-id="297ba-122">Ajoutez autant de caractères que nécessaire pour rendre l’alias unique.</span><span class="sxs-lookup"><span data-stu-id="297ba-122">Add more characters as needed to make the alias unique.</span></span>

## <a name="see-also"></a><span data-ttu-id="297ba-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="297ba-123">See Also</span></span>

[<span data-ttu-id="297ba-124">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="297ba-124">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
