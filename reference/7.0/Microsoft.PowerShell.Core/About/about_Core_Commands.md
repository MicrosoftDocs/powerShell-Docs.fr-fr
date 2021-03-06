---
description: Répertorie les applets de commande conçues pour être utilisées avec les fournisseurs PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_core_commands?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Core_Commands
ms.openlocfilehash: 5c784518ae30108813d32497f654198e7d10b379
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206653"
---
# <a name="about-core-commands"></a>À propos des commandes principales

## <a name="short-description"></a>DESCRIPTION COURTE
Répertorie les applets de commande conçues pour être utilisées avec les fournisseurs PowerShell.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

PowerShell comprend un ensemble d’applets de commande spécialement conçues pour gérer les éléments des magasins de données exposés par les fournisseurs PowerShell.
Vous pouvez utiliser ces applets de commande de la même manière pour gérer tous les différents types de données que les fournisseurs mettent à votre disposition. Pour plus d’informations sur les fournisseurs, tapez « obtenir-aide about_providers ».

Par exemple, vous pouvez utiliser l’applet de commande Get-ChildItem pour répertorier les fichiers dans un répertoire du système de fichiers, les clés sous une clé de registre ou les éléments qui sont exposés par un fournisseur que vous écrivez ou téléchargez.

La liste suivante répertorie les applets de commande PowerShell conçues pour être utilisées avec les fournisseurs :

Applets de commande ChildItem

- Get-ChildItem

Applets de commande de contenu

- Add-Content
- Clear-Content
- Get-Content
- Set-Content

Applets de commande Item

- Clear-Item
- Copy-Item
- Get-Item
- Invoke-Item
- Move-Item
- New-Item
- Remove-Item
- Rename-Item
- Set-Item

Applets de commande ItemProperty

- Clear-ItemProperty
- Copy-ItemProperty
- Get-ItemProperty
- Move-ItemProperty
- New-ItemProperty
- Remove-ItemProperty
- Rename-ItemProperty
- Set-ItemProperty

Applets de commande Location

- Get-Location
- Pop-Location
- Push-Location
- Set-Location

Applets de commande Path

- Join-Path
- Convert-Path
- Split-Path
- Resolve-Path
- Test-Path

PSDrive, applets de commande

- Get-PSDrive
- New-PSDrive
- Remove-PSDrive

Applets de commande PSProvider

- Get-PSProvider

Pour plus d’informations sur une applet de commande, tapez `get-help <cmdlet-name>` .

## <a name="see-also"></a>VOIR AUSSI

[about_Providers](about_Providers.md)
