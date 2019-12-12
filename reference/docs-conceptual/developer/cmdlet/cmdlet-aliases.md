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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369978"
---
# <a name="cmdlet-aliases"></a><span data-ttu-id="6b1bc-102">Alias des applets de commande</span><span class="sxs-lookup"><span data-stu-id="6b1bc-102">Cmdlet Aliases</span></span>

<span data-ttu-id="6b1bc-103">Vous pouvez utiliser des alias d’applet de commande pour améliorer l’expérience utilisateur de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6b1bc-103">You can use cmdlet aliases to improve the cmdlet user experience.</span></span> <span data-ttu-id="6b1bc-104">Vous pouvez ajouter des alias aux cmdlets fréquemment utilisées pour réduire la saisie et faciliter l’exécution rapide des tâches.</span><span class="sxs-lookup"><span data-stu-id="6b1bc-104">You can add aliases to frequently used cmdlets to reduce typing and to make it easier to complete tasks quickly.</span></span> <span data-ttu-id="6b1bc-105">Vous pouvez inclure des alias intégrés dans vos applets de commande ou les utilisateurs peuvent définir leurs propres alias personnalisés.</span><span class="sxs-lookup"><span data-stu-id="6b1bc-105">You can include built-in aliases in your cmdlets, or users can define their own custom aliases.</span></span>

<span data-ttu-id="6b1bc-106">Par exemple, l’applet de [commande obtenir-Command](/powershell/module/microsoft.powershell.core/get-command) a un alias de `gcm` intégré.</span><span class="sxs-lookup"><span data-stu-id="6b1bc-106">For example, the [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet has a built-in `gcm` alias.</span></span> <span data-ttu-id="6b1bc-107">Vous pouvez également utiliser des alias pour ajouter des noms de commande d’autres langues afin que les utilisateurs n’aient pas à apprendre de nouvelles commandes.</span><span class="sxs-lookup"><span data-stu-id="6b1bc-107">You can also use aliases to add command names from other languages so that users do not have to learn new commands.</span></span>

## <a name="alias-guidelines"></a><span data-ttu-id="6b1bc-108">Instructions relatives aux alias</span><span class="sxs-lookup"><span data-stu-id="6b1bc-108">Alias Guidelines</span></span>

<span data-ttu-id="6b1bc-109">Suivez ces instructions lorsque vous créez des alias intégrés pour vos applets de commande :</span><span class="sxs-lookup"><span data-stu-id="6b1bc-109">Follow these guidelines when you create built-in aliases for your cmdlets:</span></span>

- <span data-ttu-id="6b1bc-110">Avant d’assigner des alias, démarrez Windows PowerShell, puis exécutez l’applet de commande [obtenir-alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) pour voir les alias déjà utilisés.</span><span class="sxs-lookup"><span data-stu-id="6b1bc-110">Before you assign aliases, start Windows PowerShell, and then run the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet to see the aliases that are already used.</span></span>

- <span data-ttu-id="6b1bc-111">Incluez un préfixe d’alias qui référence le verbe du nom de l’applet de commande et un suffixe d’alias qui référence le nom du nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6b1bc-111">Include an alias prefix that references the verb of the cmdlet name and an alias suffix that references the noun of the cmdlet name.</span></span> <span data-ttu-id="6b1bc-112">Par exemple, l’alias de l’applet de commande `Import-Module` est « Bureau à pas ».</span><span class="sxs-lookup"><span data-stu-id="6b1bc-112">For example, the alias for the `Import-Module` cmdlet is "ipmo".</span></span> <span data-ttu-id="6b1bc-113">Pour obtenir la liste de tous les verbes et leurs alias, consultez [verbes d’applet](./approved-verbs-for-windows-powershell-commands.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="6b1bc-113">For a list of all the verbs and their aliases, see [Cmdlet Verbs](./approved-verbs-for-windows-powershell-commands.md).</span></span>

- <span data-ttu-id="6b1bc-114">Pour les applets de commande qui ont le même verbe, incluez le même préfixe d’alias.</span><span class="sxs-lookup"><span data-stu-id="6b1bc-114">For cmdlets that have the same verb, include the same alias prefix.</span></span> <span data-ttu-id="6b1bc-115">Par exemple, les alias de toutes les applets de commande Windows PowerShell dont le nom contient le verbe « obtenir » utilisent le préfixe « g ».</span><span class="sxs-lookup"><span data-stu-id="6b1bc-115">For example, the aliases for all the Windows PowerShell cmdlets that have the "Get" verb in their name use the "g" prefix.</span></span>

- <span data-ttu-id="6b1bc-116">Pour les applets de commande qui ont le même nom, incluez le même suffixe d’alias.</span><span class="sxs-lookup"><span data-stu-id="6b1bc-116">For cmdlets that have the same noun, include the same alias suffix.</span></span> <span data-ttu-id="6b1bc-117">Par exemple, les alias de toutes les applets de commande Windows PowerShell qui ont le nom « session » dans leur nom utilisent le suffixe « SN ».</span><span class="sxs-lookup"><span data-stu-id="6b1bc-117">For example, the aliases for all the Windows PowerShell cmdlets that have the "Session" noun in their name use the "sn" suffix.</span></span>

- <span data-ttu-id="6b1bc-118">Pour les applets de commande équivalentes aux commandes dans d’autres langues, utilisez le nom de la commande.</span><span class="sxs-lookup"><span data-stu-id="6b1bc-118">For cmdlets that are equivalent to commands in other languages, use the name of the command.</span></span>

- <span data-ttu-id="6b1bc-119">En général, rendez les alias aussi courts que possible.</span><span class="sxs-lookup"><span data-stu-id="6b1bc-119">In general, make aliases as short as possible.</span></span> <span data-ttu-id="6b1bc-120">Assurez-vous que l’alias a au moins un caractère distinct pour le verbe et un caractère distinct pour le nom.</span><span class="sxs-lookup"><span data-stu-id="6b1bc-120">Make sure the alias has at least one distinct character for the verb and one distinct character for the noun.</span></span> <span data-ttu-id="6b1bc-121">Ajoutez autant de caractères que nécessaire pour rendre l’alias unique.</span><span class="sxs-lookup"><span data-stu-id="6b1bc-121">Add more characters as needed to make the alias unique.</span></span>

## <a name="see-also"></a><span data-ttu-id="6b1bc-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b1bc-122">See Also</span></span>

[<span data-ttu-id="6b1bc-123">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6b1bc-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
