---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 61a914cc05c4ca9592196c925e232224d193f9d8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="format-hex"></a><span data-ttu-id="3f069-102">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="3f069-102">Format-Hex</span></span>
<span data-ttu-id="3f069-103">**Format-Hex** permet d’afficher du texte ou des données binaires au format hexadécimal ; voir [Format-Hex](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/format-hex)</span><span class="sxs-lookup"><span data-stu-id="3f069-103">**Format-Hex** lets you view text or binary data in hexadecimal format; see [Format-Hex](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/format-hex)</span></span>

## <a name="example-1"></a><span data-ttu-id="3f069-104">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="3f069-104">Example 1</span></span>
<span data-ttu-id="3f069-105">Afficher le contenu d’une chaîne au format hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="3f069-105">View the contents of a string in hexadecimal format.</span></span>

```powershell
"This is a very long line to force the line folding in Format-Hex cmdlet" | Format-Hex
```

<span data-ttu-id="3f069-106">Sorties</span><span class="sxs-lookup"><span data-stu-id="3f069-106">Outputs</span></span>
```
PS C:\> This is a very long line to force the line folding in Format-Hex cmdlet" | Format-Hex


           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   54 68 69 73 20 69 73 20 61 20 76 65 72 79 20 6C  This is a very l
00000010   6F 6E 67 20 6C 69 6E 65 20 74 6F 20 66 6F 72 63  ong line to forc
00000020   65 20 74 68 65 20 6C 69 6E 65 20 66 6F 6C 64 69  e the line foldi
00000030   6E 67 20 69 6E 20 46 6F 72 6D 61 74 2D 48 65 78  ng in Format-Hex
00000040   20 63 6D 64 6C 65 74                              cmdlet


PS C:\>
```
