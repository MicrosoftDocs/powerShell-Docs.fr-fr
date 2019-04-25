---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: aa2e9540af8b3d4c5de5e00377a84e0e5edd6e4a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057846"
---
# <a name="new-temporaryfile"></a>New-TemporaryFile
Parfois, dans vos scripts, vous devez créer un fichier temporaire. Avec l’applet de commande **New-TemporaryFile**, cette opération est très simple :

PS C:\\&gt; $tempFile = New-TemporaryFile

PS C:\\&gt; $tempFile.FullName

C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp
