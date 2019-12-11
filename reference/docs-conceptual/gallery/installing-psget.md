---
ms.date: 09/19/2019
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Installation de PowerShellGet
ms.openlocfilehash: 69dc851c54089b47fb19e5b32990d579d26effb9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328200"
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
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>Pour les systèmes avec PowerShell 5.0 (ou version ultérieure), vous pouvez installer la dernière version de PowerShellGet

Pour installer PowerShellGet sur Windows 10, Windows Server 2016, tout système équipé de WMF 5.0 ou 5.1, ou tout système équipé de PowerShell 6, exécutez les commandes suivantes à partir d’une session PowerShell avec élévation de privilèges.

```powershell
Install-Module -Name PowerShellGet -Force
Exit
```

Utilisez `Update-Module` pour obtenir des versions plus récentes.

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-computers-running-powershell-30-or-powershell-40"></a>Pour les ordinateurs exécutant PowerShell 3.0 ou PowerShell 4.0

Ces instructions s’appliquent aux ordinateurs sur lesquels **PackageManagement Preview** est installé ou qui ne disposent d’aucune version de **PowerShellGet**.

L’applet de commande `Save-Module` est utilisée dans les deux jeux d’instructions. `Save-Module` permet de télécharger un module et les dépendances éventuelles à partir d’un dépôt inscrit et de les y enregistrer. La version la plus récente du module est enregistrée sur un chemin spécifié sur l’ordinateur local, mais n’est pas installée. Pour plus d’informations, consultez [Save-Module](/powershell/module/PowershellGet/Save-Module).

#### <a name="computers-with-the-packagemanagement-preview-installed"></a>Ordinateurs sur lesquels la préversion de PackageManagement est installée

1. À partir d’une session PowerShell, utilisez `Save-Module` pour enregistrer les modules dans un répertoire local.

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. Vérifiez que les modules **PowerShellGet** et **PackageManagement** ne sont pas chargés dans d’autres processus.
1. Supprimez le contenu des dossiers : `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` et `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.
1. Ouvrez à nouveau la console PowerShell avec élévation de privilèges, puis exécutez les commandes suivantes.

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```

#### <a name="computers-without-powershellget"></a>Ordinateurs sans PowerShellGet

Les ordinateurs qui ne disposent d’aucune version de **PowerShellGet** ne peuvent pas télécharger les modules. Pour pouvoir le faire, **PowerShellGet** doit être installé sur ces ordinateurs.

1. À partir d’un ordinateur sur lequel **PowerShellGet** est installé, utilisez `Save-Module` pour télécharger la version actuelle de **PowerShellGet**. Deux dossiers sont téléchargés : **PowerShellGet** et **PackageManagement**. Chaque dossier contient un sous-dossier avec un numéro de version.

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. Copiez les dossiers **PowerShellGet** et **PackageManagement** sur l’ordinateur qui ne dispose pas de **PowerShellGet**.

   Le répertoire de destination est le suivant : `$env:ProgramFiles\WindowsPowerShell\Modules`
