---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 7730912707bb14e90a9926b387fb3a859d7ca26d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219264"
---
# <a name="convert-string"></a>Convert-String
**Convert-String** expose une fonctionnalité de « remplacement par magie ». Fournissez des exemples indiquant l’aspect souhaité du texte avant et après l’opération, et l’applet de commande **Convert-String** met automatiquement en forme le texte. Voici un exemple qui prend un prénom et un nom, et les remplace par le nom, une virgule, l’initiale du prénom, puis un point. Essayez avec une expression régulière et regardez combien de temps cela vous prend.

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
