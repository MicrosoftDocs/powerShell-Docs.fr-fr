---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: e6b54519d878ab572662075709beb4cf4454b0c6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="clipboard-cmdlets"></a><span data-ttu-id="34385-102">Applets de commande de Presse-papiers</span><span class="sxs-lookup"><span data-stu-id="34385-102">Clipboard cmdlets</span></span>
<span data-ttu-id="34385-103">**Get-Clipboard** et **Set-Clipboard** simplifient le transfert de contenu vers et à partir d’une session Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="34385-103">**Get-Clipboard** and **Set-Clipboard** make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="34385-104">Par exemple, si vous utilisez l’Explorateur Windows pour copier trois fichiers dans le Presse-papiers (en les sélectionnant et en appuyant sur `ctrl-c`, par exemple), vous pouvez ensuite accéder facilement au contenu du Presse-papiers sous forme d’une liste de fichiers :</span><span class="sxs-lookup"><span data-stu-id="34385-104">For example, if you use Windows Explorer to copy three files to the clipboard (by selecting them and pressing `ctrl-c`, for example), you can then easily access the contents of the clipboard as a list of files:</span></span>

```powershell
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


<span data-ttu-id="34385-105">Les applets de commande du Presse-papiers prennent en charge les images, les fichiers audio, les listes de fichiers et le texte.</span><span class="sxs-lookup"><span data-stu-id="34385-105">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>
