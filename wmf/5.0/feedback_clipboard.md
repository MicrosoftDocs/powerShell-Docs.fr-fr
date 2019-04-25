---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: d5ec95abb1d3160afc4179cff991cb5ef72d85fe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057296"
---
# <a name="clipboard-cmdlets"></a>Applets de commande de Presse-papiers
**Get-Clipboard** et **Set-Clipboard** simplifient le transfert de contenu vers et à partir d’une session Windows PowerShell. Par exemple, si vous utilisez l’Explorateur Windows pour copier trois fichiers dans le Presse-papiers (en les sélectionnant et en appuyant sur `ctrl-c`, par exemple), vous pouvez ensuite accéder facilement au contenu du Presse-papiers sous forme d’une liste de fichiers :

```powershell
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


Les applets de commande du Presse-papiers prennent en charge les images, les fichiers audio, les listes de fichiers et le texte.
