---
title: PowerShell de Windows mise en forme de fichiers | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d4c8f84-ebd2-4405-bb10-cfc5400d4ad6
caps.latest.revision: 6
ms.openlocfilehash: 49344d32dfcef36a904772b4a7237646a63cb12a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065374"
---
# <a name="windows-powershell-formatting-files"></a>Fichiers de mise en forme Windows PowerShell

Windows PowerShell fournit plusieurs fichiers de mise en forme (. format.ps1xml) qui se trouvent dans le répertoire d’installation (`$pshome`). Chacun de ces fichiers définit l’affichage par défaut pour un ensemble spécifique d’objets .NET. Ces fichiers ne doivent jamais être modifiées. Toutefois, vous pouvez les utiliser comme référence pour la création de vos propres fichiers de mise en forme personnalisées.

Certificate.Format.ps1xml définit l’affichage des objets dans le magasin de certificats tels que les certificats x.509 et les magasins de certificats.

DotNetTypes.Format.ps1xml définit l’affichage des divers objets .NET tels que les objets CultureInfo et FileVersionInfo EventLogEntry.

FileSystem.Format.ps1xml définit l’affichage des objets de système de fichiers tels que les objets fichier et répertoire.

Définit Help.Format.ps1xml les différentes vues utilisées par le [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) applet de commande, tels que les vues exemple intégral et paramètres détaillés.

PowerShellCore.Format.ps1xml définit l’affichage des objets générés par Windows PowerShell core applets de commande tels que les objets retournés par le [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) et [Get-History](/powershell/module/Microsoft.PowerShell.Core/Get-History) applets de commande.

PowerShellTrace.Format.ps1xml définit l’affichage des objets de trace telles que celles générées par le [Trace-Command](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) applet de commande.

Registry.Format.ps1xml définit l’affichage des objets de Registre tels que les objets de clé et d’entrée.

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md)
