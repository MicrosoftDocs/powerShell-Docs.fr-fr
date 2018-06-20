---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 08f431c27cd0ee769518b5246af2fa95aa499d54
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34217989"
---
# <a name="new-temporaryfile"></a>New-TemporaryFile
Parfois, dans vos scripts, vous devez créer un fichier temporaire. Avec l’applet de commande **New-TemporaryFile**, cette opération est très simple :

PS C:\\&gt; $tempFile = New-TemporaryFile

PS C:\\&gt; $tempFile.FullName

C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp
