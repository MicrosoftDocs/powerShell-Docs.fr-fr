---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: db9c630bcb8e9e0da423c779976739f1ae76f13e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057422"
---
# <a name="archive-cmdlets"></a>Applets de commande d’archive

Deux nouvelles applets de commande, **compression-Archive** et **Expand-Archive**, permettent de compresser et de décompresser des fichiers ZIP.

## <a name="compress-archive"></a>Compress-Archive
L’applet de commande **Compress-Archive** crée un fichier d’archive à partir de fichiers spécifiés. Un fichier d’archive permet d’empaqueter, et éventuellement de compresser, plusieurs fichiers dans un fichier unique pour faciliter la gestion et le stockage. Un fichier d’archive peut être compressé à l’aide d’un algorithme de compression spécifié par le paramètre **-CompressionLevel**.
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a>Expand-Archive
L’applet de commande **Expand-Archive** extrait les fichiers à partir d’un fichier d’archive spécifié. Un fichier d’archive permet d’empaqueter, et éventuellement de compresser, plusieurs fichiers dans un fichier unique pour faciliter la gestion et le stockage.
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```
