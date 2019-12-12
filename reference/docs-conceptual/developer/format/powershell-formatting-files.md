---
title: Fichiers de mise en forme Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d4c8f84-ebd2-4405-bb10-cfc5400d4ad6
caps.latest.revision: 6
ms.openlocfilehash: 3ec127d5ff60754de5d7f1ac73f2965524228b9c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365008"
---
# <a name="windows-powershell-formatting-files"></a>Fichiers de mise en forme Windows PowerShell

Windows PowerShell fournit plusieurs fichiers de mise en forme (. format. ps1xml) qui se trouvent dans le répertoire d’installation (`$pshome`). Chacun de ces fichiers définit l’affichage par défaut pour un ensemble spécifique d’objets .NET. Ces fichiers ne doivent jamais être modifiés. Toutefois, vous pouvez les utiliser comme référence pour créer vos propres fichiers de mise en forme personnalisés.

`Certificate.Format.ps1xml` définit l’affichage des objets dans le magasin de certificats, tels que les certificats x. 509 et les magasins de certificats.

`DotNetTypes.Format.ps1xml` définit l’affichage des divers objets .NET tels que les objets CultureInfo, FileVersionInfo et EventLogEntry.

`FileSystem.Format.ps1xml` définit l’affichage des objets de système de fichiers tels que les objets de fichiers et de répertoires.

`Help.Format.ps1xml` définit les différents affichages utilisés par l’applet de commande [« obtenir-Help »](/powershell/module/Microsoft.PowerShell.Core/Get-Help) , tels que les affichages détaillés, complets, des paramètres et des exemples.

`PowerShellCore.Format.ps1xml` définit l’affichage des objets générés par les applets de commande Windows PowerShell Core, telles que les objets retournés par les applets de commande [obtenir-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) et [obtenir-History](/powershell/module/Microsoft.PowerShell.Core/Get-History) .

`PowerShellTrace.Format.ps1xml` définit l’affichage des objets de trace tels que ceux générés par l’applet [de commande trace-Command](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) .

`Registry.Format.ps1xml` définit l’affichage des objets de Registre tels que les objets de clé et d’entrée.

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md)
