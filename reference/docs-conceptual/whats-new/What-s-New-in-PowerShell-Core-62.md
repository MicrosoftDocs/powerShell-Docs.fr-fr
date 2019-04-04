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
# <a name="whats-new-in-powershell-core-62"></a>Nouveautés de PowerShell Core 6.2

Vous trouverez dans cet article une sélection des principales nouvelles fonctionnalités et modifications introduites dans PowerShell Core 6.2.

Mais il y a aussi des **tonnes** d’autres « choses ennuyeuses » qui rendent PowerShell plus rapide et plus stable (ainsi que de nombreux correctifs de bogues) !
Pour obtenir la liste complète des modifications, consultez le [journal des modifications sur GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).

Nous profitons pour remercier [l’ensemble de la communauté des contributeurs](https://github.com/PowerShell/PowerShell/graphs/contributors) qui ont permis à cette version de voir le jour.

## <a name="engine-updates-and-fixes"></a>Mises à jour et correctifs du moteur

- Ajout de messages d’avertissement d'activation/de désactivation de la télécommande PowerShell ([#9203][])
- Correctif pour `FormatTable` régression de la désérialisation à distance ([#9116][])
- Mise à jour des API `async` basées sur la tâche ajoutées à PowerShell pour retourner directement un objet de tâche ([#9079][])
- Ajout de 5 surcharges `InvokeAsync` et de `StopAsync` au type `PowerShell` ([#8056][]) (Merci @KirkMunro !)

## <a name="general-cmdlet-updates-and-fixes"></a>Mises à jour et correctifs d’applets de commande générales

- Activation des applets de commande `SecureString` pour Non-Windows en stockant le texte brut ([#9199][])
- Ajout d’un message obsolète à `Send-MailMessage` ([#9178][])
- Correctif `Restart-Computer` pour travailler sur `localhost` en l’absence de WinRM ([#9160][])
- Amener `Start-Job` à générer une erreur de fin d’exécution lorsque PowerShell est hébergé ([#9128][])
- Mise à jour de la version pour `PowerShell.Native` et l’hébergement des tests ([#8983][])

## <a name="breaking-changes"></a>Modifications importantes

Correctif du comportement -NoEnumerate dans Write-Output pour être cohérent avec Windows PowerShell ([#9069][]) (Merci @vexx32 !)

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
