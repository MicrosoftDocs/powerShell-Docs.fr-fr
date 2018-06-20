---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 9ca12ad3f0729a2e9595d7ca5ccf9041e47658a3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218091"
---
# <a name="archive-cmdlets"></a><span data-ttu-id="ef741-102">Applets de commande d’archive</span><span class="sxs-lookup"><span data-stu-id="ef741-102">Archive cmdlets</span></span>

<span data-ttu-id="ef741-103">Deux nouvelles applets de commande, **compression-Archive** et **Expand-Archive**, permettent de compresser et de décompresser des fichiers ZIP.</span><span class="sxs-lookup"><span data-stu-id="ef741-103">Two new cmdlets, **Compress-Archive** and **Expand-Archive**, let you compress and expand ZIP files.</span></span>

## <a name="compress-archive"></a><span data-ttu-id="ef741-104">Compress-Archive</span><span class="sxs-lookup"><span data-stu-id="ef741-104">Compress-Archive</span></span>
<span data-ttu-id="ef741-105">L’applet de commande **Compress-Archive** crée un fichier d’archive à partir de fichiers spécifiés.</span><span class="sxs-lookup"><span data-stu-id="ef741-105">The **Compress-Archive** cmdlet creates a new archive file from specified files.</span></span> <span data-ttu-id="ef741-106">Un fichier d’archive permet d’empaqueter, et éventuellement de compresser, plusieurs fichiers dans un fichier unique pour faciliter la gestion et le stockage.</span><span class="sxs-lookup"><span data-stu-id="ef741-106">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span> <span data-ttu-id="ef741-107">Un fichier d’archive peut être compressé à l’aide d’un algorithme de compression spécifié par le paramètre **-CompressionLevel**.</span><span class="sxs-lookup"><span data-stu-id="ef741-107">An archive file can be compressed by using a compression algorithm specified in the **-CompressionLevel** parameter.</span></span>
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a><span data-ttu-id="ef741-108">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="ef741-108">Expand-Archive</span></span>
<span data-ttu-id="ef741-109">L’applet de commande **Expand-Archive** extrait les fichiers à partir d’un fichier d’archive spécifié.</span><span class="sxs-lookup"><span data-stu-id="ef741-109">The **Expand-Archive** cmdlet extracts files from a specified archive file.</span></span> <span data-ttu-id="ef741-110">Un fichier d’archive permet d’empaqueter, et éventuellement de compresser, plusieurs fichiers dans un fichier unique pour faciliter la gestion et le stockage.</span><span class="sxs-lookup"><span data-stu-id="ef741-110">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span>
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```
