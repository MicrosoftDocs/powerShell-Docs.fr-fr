---
description: Explique comment utiliser l’outil en ligne de commande PowerShell_Ise.exe.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_ise_exe?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Ise_exe
ms.openlocfilehash: c7500eb6d8586b9dca568edc4e805c577e94bec4
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207957"
---
# <a name="about-powershell-iseexe"></a>À propos des Ise.exe PowerShell

## <a name="short-description"></a>DESCRIPTION COURTE

Explique comment utiliser l’outil en ligne de commande PowerShell_Ise.exe.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

PowerShell_Ise.exe démarre une session Environnement d’écriture de scripts intégré de Windows PowerShell (ISE). Vous pouvez l’exécuter dans Cmd.exe et dans Windows PowerShell.

Pour exécuter PowerShell_ISE.exe, tapez PowerShell_ISE.exe, PowerShell_ISE ou ISE.

## <a name="syntax"></a>SYNTAX

```
PowerShell_Ise[.exe]
PowerShell_ISE[.exe]
ISE[.exe]
[-File]<FilePath[]> [-NoProfile] [-MTA]
-Help | ? | -? | /? Displays the syntax and describes the command-line switches.
```

## <a name="parameters"></a>PARAMETERS

### <a name="-file"></a>-File

Ouvre les fichiers spécifiés dans Windows PowerShell ISE. Le nom du paramètre (« -file ») est facultatif. Pour répertorier plusieurs fichiers, entrez une chaîne de texte entre guillemets. Utilisez des virgules pour séparer les noms de fichiers dans la chaîne.

Par exemple :

PowerShell_ISE-file « File1.ps1, File2.ps1, File3.xml ».

Les espaces entre les noms de fichiers sont autorisés dans Windows PowerShell, mais ils peuvent ne pas être interprétés correctement par d’autres programmes, tels que Cmd.exe.

Vous pouvez utiliser ce paramètre pour ouvrir n’importe quel fichier texte, y compris les fichiers de script Windows PowerShell et les fichiers XML.

### <a name="-mta"></a>-Mta

Démarre Windows PowerShell ISE à l’aide d’un cloisonnement multithread. Ce paramètre est introduit dans Windows PowerShell 3.0. Le cloisonnement (STA, Single-Threaded Apartment) est la valeur par défaut.

### <a name="-noprofile"></a>-NoProfile

N’exécute pas les profils Windows PowerShell. Par défaut, les profils Windows PowerShell sont exécutés dans chaque session.

Ce paramètre est recommandé lorsque vous écrivez du contenu partagé, comme des fonctions et des scripts qui seront exécutés sur des systèmes avec des profils différents.
Pour plus d’informations, consultez [about_Profiles](about_Profiles.md).

### <a name="-help---"></a>-Help- ?,/ ?

Affiche l’aide pour PowerShell_ISE.exe.

## <a name="examples"></a>EXEMPLES

Ces commandes démarrent Windows PowerShell ISE. Les commandes sont équivalentes et peuvent être utilisées indifféremment.

```
PS C:> PowerShell_ISE.exe
PS C:> PowerShell_ISE
PS C:> ISE
```

Ces commandes ouvrent le script Get-Profile.ps1 dans Windows PowerShell ISE.
Les commandes sont équivalentes et peuvent être utilisées indifféremment.

```
PS C:> PowerShell_ISE.exe -File .\Get-Profile.ps1
PS C:> ISE -File .\Get-Profile.ps1
PS C:> ISE .\Get-Profile.ps1
```

Cette commande ouvre les scripts Get-Backups.ps1 et Get-BackupInstance.ps1 dans Windows PowerShell ISE. Pour ouvrir plusieurs fichiers, utilisez une virgule pour séparer les noms de fichiers et placez la valeur de nom de fichier complète entre guillemets.

```
PS C:> ISE -File ".\Get-Backups.ps1,Get-BackupInstance.ps1"
```

Cette commande démarre Windows PowerShell ISE sans profil.

```
PS C:> ISE -NoProfile
```

Cette commande obtient de l’aide pour PowerShell_ISE.exe.

```
PS C:> ISE -help
```

## <a name="see-also"></a>VOIR AUSSI

[about_PowerShell.exe](about_PowerShell_exe.md)

[about_Windows_PowerShell_ISE](about_Windows_PowerShell_ISE.md)

[Environnement d’écriture de scripts intégré de Windows PowerShell (ISE)](/powershell/scripting/windows-powershell/ise/introducing-the-windows-powershell-ise)
