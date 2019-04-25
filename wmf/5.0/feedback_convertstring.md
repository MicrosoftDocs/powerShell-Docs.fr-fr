---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 27541d903748738675917941dc6b60bc9acdc3f4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057789"
---
# <a name="convert-string"></a>Convert-String
**Convert-String** expose une fonctionnalité de « remplacement par magie ». Fournissez des exemples indiquant l’aspect souhaité du texte avant et après l’opération, et l’applet de commande **Convert-String** met automatiquement en forme le texte. Voici un exemple qui prend un prénom et un nom, et les remplace par le nom, une virgule, l’initiale du prénom, puis un point. Essayez avec une expression régulière et regardez combien de temps cela vous prend.

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
