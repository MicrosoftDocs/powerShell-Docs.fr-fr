---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,configuration
ms.openlocfilehash: 4185d9395f2f3e5ba1c8daa0c365cb2bf322936b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="get-childitem-has--depth-parameter"></a>Get-ChildItem a un paramètre -Depth
**Get-ChildItem** a maintenant un paramètre **–Depth** que vous pouvez utiliser avec **– Recurse** pour limiter la récursivité :

PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

d----- 4/14/2015 5:36 PM Depth0

-a---- 4/14/2015 1:19 PM 0 File1.txt

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

d----- 4/14/2015 5:36 PM Depth0

-a---- 4/14/2015 1:19 PM 0 File1.txt

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0

Mode LastWriteTime Length Name

---- ------------- ------ ----

d----- 4/14/2015 5:33 PM Depth1

