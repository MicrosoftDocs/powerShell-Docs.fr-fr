---
description: Décrit la fonctionnalité de compatibilité de Windows PowerShell pour PowerShell 7.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_powershell_compatibility?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_PowerShell_Compatibility
ms.openlocfilehash: 777dab1cce4329958337a7c0857b0d712b4387a9
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207477"
---
# <a name="about-windows-powershell-compatibility"></a>À propos de la compatibilité Windows PowerShell

## <a name="short-description"></a>DESCRIPTION COURTE

Décrit la fonctionnalité de compatibilité de Windows PowerShell pour PowerShell 7.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

À moins que le manifeste de module indique que le module est compatible avec PowerShell Core, les modules du `%windir%\system32\WindowsPowerShell\v1.0\Modules` dossier sont chargés dans un processus Windows powershell 5,1 en arrière-plan par la fonctionnalité de compatibilité Windows PowerShell.

### <a name="using-the-compatibility-feature"></a>Utilisation de la fonctionnalité de compatibilité

Lorsque le premier module est importé à l’aide de la fonctionnalité de compatibilité Windows PowerShell, PowerShell crée une session à distance nommée `WinPSCompatSession` qui s’exécute dans un processus Windows powershell 5,1 en arrière-plan. Ce processus est créé lorsque la fonctionnalité de compatibilité importe le premier module. Le processus est fermé lorsque le dernier module de ce type est supprimé (à l’aide de `Remove-Module` ) ou lorsque le processus PowerShell s’arrête.

Les modules chargés dans la `WinPSCompatSession` session sont utilisés via la communication à distance implicite et sont reflétés dans la session PowerShell active. Il s’agit de la même méthode de transport que celle utilisée pour les travaux PowerShell.

Lorsqu’un module est importé dans la `WinPSCompatSession` session, la communication à distance implicite génère un module proxy dans le répertoire de l’utilisateur `$env:Temp` et importe ce module proxy dans la session PowerShell active. PowerShell peut ainsi détecter que le module a été chargé à l’aide de la fonctionnalité de compatibilité Windows PowerShell.

Une fois la session créée, elle peut être utilisée pour les opérations qui ne fonctionnent pas correctement sur les objets désérialisés. L’intégralité du pipeline est exécutée dans Windows PowerShell et seul le résultat final est retourné. Par exemple :

```powershell
$s = Get-PSSession -Name WinPSCompatSession
Invoke-Command -Session $s -ScriptBlock {
  "Running in Windows PowerShell version $($PSVersionTable.PSVersion)"
}
```

La fonctionnalité de compatibilité peut être appelée de deux manières :

- Explicitement en important un module à l’aide du paramètre **UseWindowsPowerShell**

   ```powershell
   Import-Module -Name ScheduledTasks -UseWindowsPowerShell
   ```

- Implicitement en important un module Windows PowerShell par nom de module, chemin d’accès ou chargement automatique via la découverte de commande.

   ```powershell
   Import-Module -Name ServerManager
   Get-AppLockerPolicy -Local
   ```

   S’il n’est pas déjà chargé, le module AppLocker est chargé lors de l’exécution de  `Get-AppLockerPolicy` .

La compatibilité Windows PowerShell bloque le chargement des modules répertoriés dans le `WindowsPowerShellCompatibilityModuleDenyList` paramètre du fichier de configuration PowerShell.

La valeur par défaut de ce paramètre est :

```json
"WindowsPowerShellCompatibilityModuleDenyList":  [
   "PSScheduledJob","BestPractices","UpdateServices"
]
```

### <a name="managing-implicit-module-loading"></a>Gestion du chargement de modules implicites

Pour désactiver le comportement d’importation implicite de la fonctionnalité de compatibilité Windows PowerShell, utilisez le `DisableImplicitWinCompat` paramètre dans un fichier de configuration PowerShell. Ce paramètre peut être ajouté au `powershell.config.json` fichier. Pour plus d’informations, consultez [about_powershell_config](about_powershell_config.md).

Cet exemple montre comment créer un fichier de configuration qui désactive la fonctionnalité de chargement de module implicite de compatibilité Windows PowerShell.

```powershell
$ConfigPath = "$PSHOME\DisableWinCompat.powershell.config.json"
$ConfigJSON = ConvertTo-Json -InputObject @{
  "DisableImplicitWinCompat" = $true
  "Microsoft.PowerShell:ExecutionPolicy" = "RemoteSigned"
}
$ConfigJSON | Out-File -Force $ConfigPath
pwsh -settingsFile $ConfigPath
```

Pour plus d’informations sur la compatibilité des modules, consultez la liste de [compatibilité des modules PowerShell 7](https://aka.ms/PSModuleCompat) .

### <a name="managing-cmdlet-clobbering"></a>Gestion des applets de commande effacer

La fonctionnalité de compatibilité Windows PowerShell utilise la communication à distance implicite pour charger les modules en mode de compatibilité. En conséquence, les commandes exportées par le module sont prioritaires sur les commandes du même nom dans la session PowerShell 7 actuelle. Dans PowerShell 7.0.0, cela comprenait les modules principaux fournis avec PowerShell.

Dans PowerShell 7,1, le comportement a été modifié, de sorte que les modules PowerShell de base suivants ne sont pas écrasé :

- Microsoft. PowerShell. ConsoleHost
- Microsoft.PowerShell.Diagnostics
- Microsoft.PowerShell.Host
- Microsoft.PowerShell.Management
- Microsoft.PowerShell.Security
- Microsoft.PowerShell.Utility
- Microsoft.WSMan.Management

PowerShell 7,1 a également ajouté la possibilité de répertorier des modules supplémentaires qui ne doivent pas être écrasé par le mode de compatibilité.

Vous pouvez ajouter le `WindowsPowerShellCompatibilityNoClobberModuleList` paramètre au fichier de configuration PowerShell. La valeur de ce paramètre est une liste de noms de module séparés par des virgules. La valeur par défaut de ce paramètre est :

```json
"WindowsPowerShellCompatibilityNoClobberModuleList": [ ]
```

## <a name="limitations"></a>Limites

La fonctionnalité de compatibilité de Windows PowerShell :

1. Fonctionne uniquement localement sur les ordinateurs Windows
1. Requiert Windows PowerShell 5,1
1. Fonctionne sur les paramètres et les valeurs de retour de l’applet de commande sérialisés, et non sur les objets actifs
1. Tous les modules importés dans la session de communication à distance Windows PowerShell partagent la même instance d’exécution.

## <a name="keywords"></a>Mots clés

about_Windows_PowerShell_Compatibility

## <a name="see-also"></a>Voir aussi

[about_Modules](about_Modules.md)

[Module d’importation](xref:Microsoft.PowerShell.Core.Import-Module)
