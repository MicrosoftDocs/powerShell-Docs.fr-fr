---
title: Accès distant à WS-Management (WSMan) dans PowerShell Core
description: Accès distant dans PowerShell Core à l’aide de WSMan
ms.date: 08/06/2018
ms.openlocfilehash: fdc4159279db28b8ee60bc0853e19512a1f9ec14
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501301"
---
# <a name="ws-management-wsman-remoting-in-powershell-core"></a>Accès distant à WS-Management (WSMan) dans PowerShell Core

## <a name="instructions-to-create-a-remoting-endpoint"></a>Instructions pour créer un point de terminaison de communication à distance

Le package PowerShell Core pour Windows inclut un plug-in WinRM (`pwrshplugin.dll`) et un script d’installation (`Install-PowerShellRemoting.ps1`) dans `$PSHome`. Ces fichiers permettent à PowerShell d’accepter les connexions à distance PowerShell entrantes quand son point de terminaison est spécifié.

### <a name="motivation"></a>Motivation

Une installation de PowerShell peut établir des sessions PowerShell sur des ordinateurs distants avec `New-PSSession` et `Enter-PSSession`. Pour lui permettre d’accepter les connexions à distance PowerShell, l’utilisateur doit créer un point de terminaison d’accès distant WinRM. Il s’agit d’un scénario à choisir explicitement là où l’utilisateur exécute Install-PowerShellRemoting.ps1 pour créer le point de terminaison WinRM. Le script d’installation est une solution à court terme jusqu’à ce que nous ajoutions une fonctionnalité supplémentaire à `Enable-PSRemoting` pour effectuer la même action. Pour plus d’informations, reportez-vous au problème [#1193](https://github.com/PowerShell/PowerShell/issues/1193).

### <a name="script-actions"></a>Actions de script

Le script

1. Crée un répertoire pour le plug-in dans `$env:windir\System32\PowerShell`
1. Copie pwrshplugin.dll à cet emplacement
1. Génère un fichier de configuration
1. Inscrit ce plug-in auprès de WinRM

### <a name="registration"></a>Inscription

Le script doit être exécuté dans une session PowerShell de niveau administrateur et il s’exécute dans deux modes.

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a>Exécuté par l’instance de PowerShell qu’il inscrira

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a>Exécuté par une autre instance de PowerShell pour le compte de l’instance qu’il inscrira

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

Par exemple :

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

> [!NOTE]
> Le script d’inscription de l’accès distant redémarre WinRM. Toutes les sessions PSRP existantes sont arrêtées immédiatement après l’exécution du script. S’il est exécuté pendant une session à distance, le script mettra fin à la connexion.

## <a name="how-to-connect-to-the-new-endpoint"></a>Comment se connecter à un nouveau point de terminaison

Créez une session PowerShell sur le nouveau point de terminaison PowerShell en spécifiant `-ConfigurationName "some endpoint name"`. Pour vous connecter à l’instance PowerShell de l’exemple ci-dessus, utilisez :

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

Notez que les appels de `New-PSSession` et de `Enter-PSSession` qui ne spécifient pas `-ConfigurationName` ciblent le point de terminaison PowerShell par défaut, `microsoft.powershell`.
