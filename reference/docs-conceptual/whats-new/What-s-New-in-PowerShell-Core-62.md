---
title: Nouveautés de PowerShell Core 6.2
description: Nouvelles fonctionnalités et modifications de PowerShell Core 6.2
ms.date: 03/28/2019
ms.openlocfilehash: 2224d23a244175059a705c07001e8ad8d6ab3aa0
ms.sourcegitcommit: 8dd4394cf867005a8b9ef0bb74b744c964fbc332
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2019
ms.locfileid: "58750050"
---
# <a name="whats-new-in-powershell-core-62"></a><span data-ttu-id="9b271-103">Nouveautés de PowerShell Core 6.2</span><span class="sxs-lookup"><span data-stu-id="9b271-103">What's New in PowerShell Core 6.2</span></span>

<span data-ttu-id="9b271-104">Vous trouverez dans cet article une sélection des principales nouvelles fonctionnalités et modifications introduites dans PowerShell Core 6.2.</span><span class="sxs-lookup"><span data-stu-id="9b271-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.2.</span></span>

<span data-ttu-id="9b271-105">Mais il y a aussi des **tonnes** d’autres « choses ennuyeuses » qui rendent PowerShell plus rapide et plus stable (ainsi que de nombreux correctifs de bogues) !</span><span class="sxs-lookup"><span data-stu-id="9b271-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span>
<span data-ttu-id="9b271-106">Pour obtenir la liste complète des modifications, consultez le [journal des modifications sur GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span><span class="sxs-lookup"><span data-stu-id="9b271-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="9b271-107">Nous profitons pour remercier [l’ensemble de la communauté des contributeurs](https://github.com/PowerShell/PowerShell/graphs/contributors) qui ont permis à cette version de voir le jour.</span><span class="sxs-lookup"><span data-stu-id="9b271-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="engine-updates-and-fixes"></a><span data-ttu-id="9b271-108">Mises à jour et correctifs du moteur</span><span class="sxs-lookup"><span data-stu-id="9b271-108">Engine Updates and Fixes</span></span>

- <span data-ttu-id="9b271-109">Ajout de messages d’avertissement d'activation/de désactivation de la télécommande PowerShell ([#9203][])</span><span class="sxs-lookup"><span data-stu-id="9b271-109">Add PowerShell remoting enable/disable cmdlet warning messages ([#9203][])</span></span>
- <span data-ttu-id="9b271-110">Correctif pour `FormatTable` régression de la désérialisation à distance ([#9116][])</span><span class="sxs-lookup"><span data-stu-id="9b271-110">Fix for `FormatTable` remote deserialization regression ([#9116][])</span></span>
- <span data-ttu-id="9b271-111">Mise à jour des API `async` basées sur la tâche ajoutées à PowerShell pour retourner directement un objet de tâche ([#9079][])</span><span class="sxs-lookup"><span data-stu-id="9b271-111">Update the task-based `async` APIs added to PowerShell to return a Task object directly ([#9079][])</span></span>
- <span data-ttu-id="9b271-112">Ajout de 5 surcharges `InvokeAsync` et de `StopAsync` au type `PowerShell` ([#8056][]) (Merci @KirkMunro !)</span><span class="sxs-lookup"><span data-stu-id="9b271-112">Add 5 `InvokeAsync` overloads and `StopAsync` to the `PowerShell` type ([#8056][]) (Thanks @KirkMunro!)</span></span>

## <a name="general-cmdlet-updates-and-fixes"></a><span data-ttu-id="9b271-113">Mises à jour et correctifs d’applets de commande générales</span><span class="sxs-lookup"><span data-stu-id="9b271-113">General Cmdlet Updates and Fixes</span></span>

- <span data-ttu-id="9b271-114">Activation des applets de commande `SecureString` pour Non-Windows en stockant le texte brut ([#9199][])</span><span class="sxs-lookup"><span data-stu-id="9b271-114">Enable `SecureString` cmdlets for non-Windows by storing the plain text ([#9199][])</span></span>
- <span data-ttu-id="9b271-115">Ajout d’un message obsolète à `Send-MailMessage` ([#9178][])</span><span class="sxs-lookup"><span data-stu-id="9b271-115">Add Obsolete message to `Send-MailMessage` ([#9178][])</span></span>
- <span data-ttu-id="9b271-116">Correctif `Restart-Computer` pour travailler sur `localhost` en l’absence de WinRM ([#9160][])</span><span class="sxs-lookup"><span data-stu-id="9b271-116">Fix `Restart-Computer` to work on `localhost` when WinRM is not present ([#9160][])</span></span>
- <span data-ttu-id="9b271-117">Amener `Start-Job` à générer une erreur de fin d’exécution lorsque PowerShell est hébergé ([#9128][])</span><span class="sxs-lookup"><span data-stu-id="9b271-117">Make `Start-Job` throw terminating error when PowerShell is being hosted ([#9128][])</span></span>
- <span data-ttu-id="9b271-118">Mise à jour de la version pour `PowerShell.Native` et l’hébergement des tests ([#8983][])</span><span class="sxs-lookup"><span data-stu-id="9b271-118">Update version for `PowerShell.Native` and hosting tests ([#8983][])</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="9b271-119">Modifications importantes</span><span class="sxs-lookup"><span data-stu-id="9b271-119">Breaking Changes</span></span>

<span data-ttu-id="9b271-120">Correctif du comportement -NoEnumerate dans Write-Output pour être cohérent avec Windows PowerShell ([#9069][]) (Merci @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="9b271-120">Fix -NoEnumerate behavior in Write-Output to be consistent with Windows PowerShell ([#9069][]) (Thanks @vexx32!)</span></span>

<!-- Link references -->
[#8056]: https://github.com/PowerShell/PowerShell/pull/8056
[#8983]: https://github.com/PowerShell/PowerShell/pull/8983
[#9069]: https://github.com/PowerShell/PowerShell/pull/9069
[#9079]: https://github.com/PowerShell/PowerShell/pull/9079
[#9116]: https://github.com/PowerShell/PowerShell/pull/9116
[#9128]: https://github.com/PowerShell/PowerShell/pull/9128
[#9160]: https://github.com/PowerShell/PowerShell/pull/9160
[#9178]: https://github.com/PowerShell/PowerShell/pull/9178
[#9199]: https://github.com/PowerShell/PowerShell/pull/9199
[#9203]: https://github.com/PowerShell/PowerShell/pull/9203
