---
ms.date: 09/19/2019
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Installation de PowerShellGet
ms.openlocfilehash: 4a10699be9ff2b64e5848c6749bdd3dedf55e3c7
ms.sourcegitcommit: f05f18154913d346012527c23020d48d87ccac74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2020
ms.locfileid: "88162509"
---
# <a name="installing-powershellget"></a>Installation de PowerShellGet

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet est un module inclus par défaut dans les versions suivantes

- [Windows 10](https://www.microsoft.com/windows) ou version ultérieure
- [Windows Server 2016](/windows-server/windows-server) ou version ultérieure
- [Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) ou version ultérieure
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a>Obtenir la dernière version de PowerShell Gallery

Avant d’effectuer la mise à jour de **PowerShellGet**, vous devez toujours installer le dernier fournisseur **NuGet**. À partir d’une session PowerShell avec élévation de privilèges, exécutez la commande suivante.

```powershell
Install-PackageProvider -Name NuGet -Force
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>Pour les systèmes avec PowerShell 5.0 (ou version ultérieure), vous pouvez installer la dernière version de PowerShellGet

Pour installer PowerShellGet sur Windows 10, Windows Server 2016, tout système équipé de WMF 5.0 ou 5.1, ou tout système équipé de PowerShell 6, exécutez les commandes suivantes à partir d’une session PowerShell avec élévation de privilèges.

```powershell
Install-Module -Name PowerShellGet -Force
```

Utilisez `Update-Module` pour obtenir des versions plus récentes.

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-computers-running-powershell-30-or-powershell-40"></a>Pour les ordinateurs exécutant PowerShell 3.0 ou PowerShell 4.0

Ces instructions s’appliquent aux ordinateurs sur lesquels **PackageManagement Preview** est installé ou qui ne disposent d’aucune version de **PowerShellGet**.

L’applet de commande `Save-Module` est utilisée dans les deux jeux d’instructions. `Save-Module` permet de télécharger un module et les dépendances éventuelles à partir d’un dépôt inscrit et de les y enregistrer. La version la plus récente du module est enregistrée sur un chemin spécifié sur l’ordinateur local, mais n’est pas installée. Pour installer les modules dans PowerShell 3.0 ou 4.0, copiez les dossiers enregistrés du module dans `$env:ProgramFiles\WindowsPowerShell\Modules`.

Pour plus d’informations, consultez [Save-Module](/powershell/module/PowershellGet/Save-Module).

> [!NOTE]
> PowerShell 3.0 et PowerShell 4.0 ne prenaient en charge qu’une seule version d’un module. À compter de PowerShell 5.0, les modules sont installés dans `<modulename>\<version>`. Cela vous permet d’installer plusieurs versions côte à côte. Après avoir téléchargé le module à l’aide de `Save-Module`, vous devez copier les fichiers du dossier `<modulename>\<version>` dans le dossier `<modulename>` sur l’ordinateur de destination, comme indiqué dans les instructions ci-dessous.

#### <a name="preparatory-step-on-computers-running-powershell-30"></a>Étape préparatoire sur les ordinateurs exécutant PowerShell 3.0

Les instructions fournies dans les sections ci-dessous permettent d’installer les modules dans le répertoire `$env:ProgramFiles\WindowsPowerShell\Modules`.
Dans PowerShell 3.0, ce répertoire n’est pas listé dans `$env:PSModulePath` par défaut. Vous devez donc l’ajouter pour que les modules se chargent automatiquement. 

Ouvrez une session PowerShell avec élévation de privilèges et exécutez la commande suivante (qui prendra effet dans les sessions ultérieures) :

```powershell
[Environment]::SetEnvironmentVariable(
  'PSModulePath',
  ((([Environment]::GetEnvironmentVariable('PSModulePath', 'Machine') -split ';') + "$env:ProgramFiles\WindowsPowerShell\Modules") -join ';'),
  'Machine'
)
```

#### <a name="computers-with-the-packagemanagement-preview-installed"></a>Ordinateurs sur lesquels la préversion de PackageManagement est installée

> [!NOTE] 
> La préversion de PackageManagement était un composant téléchargeable qui rendait PowerShellGet disponible pour les versions 3 et 4 de PowerShell, mais ce composant n’est plus disponible.
> Pour déterminer s’il a été installé sur un ordinateur donné, exécutez `Get-Module -ListAvailable PowerShellGet`.

1. À partir d’une session PowerShell, utilisez `Save-Module` pour télécharger la version actuelle de **PowerShellGet**. Deux dossiers sont téléchargés : **PowerShellGet** et **PackageManagement**. Chaque dossier contient un sous-dossier avec un numéro de version.

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. Vérifiez que les modules **PowerShellGet** et **PackageManagement** ne sont pas chargés dans d’autres processus.

1. Rouvrez la console PowerShell avec élévation de privilèges, puis exécutez les commandes suivantes.

   ```powershell
   'PowerShellGet', 'PackageManagement' | % { 
     $targetDir = "$env:ProgramFiles\WindowsPowerShell\Modules\$_"
     Remove-Item $targetDir\* -Recurse -Force
     Copy-Item C:\LocalFolder\$_\*\* $targetDir\ -Recurse -Force
   }
   ```

#### <a name="computers-without-powershellget"></a>Ordinateurs sans PowerShellGet

Les ordinateurs qui ne disposent d’aucune version de **PowerShellGet** (utilisez `Get-Module -ListAvailable PowerShellGet` pour le déterminer) ne peuvent pas télécharger les modules. Pour pouvoir le faire, **PowerShellGet** doit être installé sur ces ordinateurs.

1. À partir d’un ordinateur sur lequel **PowerShellGet** est installé, utilisez `Save-Module` pour télécharger la version actuelle de **PowerShellGet**. Deux dossiers sont téléchargés : **PowerShellGet** et **PackageManagement**. Chaque dossier contient un sous-dossier avec un numéro de version.

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. Copiez le sous-dossier `<version>` respectif dans les dossiers **PowerShellGet** et **PackageManagement** sur l’ordinateur sur lequel **PowerShellGet** n’est pas installé, dans les dossiers `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` et `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` respectivement, ce qui nécessite une session avec élévation de privilèges.
   
1. Par exemple, si vous pouvez accéder au dossier de téléchargement sur l’autre ordinateur, par exemple `ws1`, à partir de l’ordinateur cible par le biais d’un chemin UNC, par exemple `\\ws1\C$\LocalFolder`, ouvrez une console PowerShell avec des autorisations élevées et exécutez la commande suivante :

   ```powershell
   'PowerShellGet', 'PackageManagement' | % {
     $targetDir = "$env:ProgramFiles\WindowsPowerShell\Modules\$_"
     $null = New-Item -Type Directory -Force $targetDir
     $fromComputer = 'ws1'  # Specify the name of the other computer here.
     Copy-Item \\$fromComputer\C$\LocalFolder\$_\*\* $targetDir -Recurse -Force
     if (-not (Get-ChildItem $targetDir)) { Throw "Copying failed." }
   }
   ```
