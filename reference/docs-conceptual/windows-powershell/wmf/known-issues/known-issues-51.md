---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,configuration
title: Problèmes connus dans WMF 5.1
ms.openlocfilehash: 4f4c85e1f4984d9e91ea74ba65fdbf7188c5c7ab
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808705"
---
# <a name="known-issues-in-wmf-51"></a>Problèmes connus dans WMF 5.1

## <a name="starting-powershell-shortcut-as-administrator"></a>Démarrage de raccourci PowerShell en tant qu’administrateur

Lors de l’installation de WMF, si vous essayez de démarrer PowerShell en tant qu’administrateur à partir du raccourci, vous pouvez obtenir un message « Erreur non spécifiée ». Rouvrez le raccourci comme non-administrateur. Le raccourci fonctionne désormais même comme administrateur.

## <a name="pester"></a>Pester

Dans cette version, vous devez savoir qu’il existe deux problèmes quand vous utilisez Pester sur Nano Server :

- L’exécution des tests directement sur Pester peut entraîner des échecs en raison des différences entre la version CLR complète et la version CLR de base. En particulier, la méthode **Validate** n’est pas disponible sur le type **XmlDocument**. Six tests qui tentent de valider le schéma des journaux de sortie NUnit échouent systématiquement.
- Un test de couverture du code échoue, car la ressource DSC **WindowsFeature** n’existe pas dans Nano Server. Toutefois, ces échecs sont généralement sans conséquence et peuvent être ignorés.

## <a name="operation-validation"></a>Validation de l’opération

- `Update-Help` échoue pour le module Microsoft.PowerShell.Operation.Validation en raison d’un URI d’aide qui ne fonctionne pas

## <a name="dsc-after-uninstall-wmf"></a>DSC après la désinstallation de WMF

- La désinstallation de WMF ne supprime pas les documents MOF DSC du dossier de configuration. DSC ne fonctionne pas correctement si les documents MOF contiennent des propriétés récentes qui ne sont pas disponibles sur les anciens systèmes. Dans ce cas, exécutez le script suivant à partir de la console PowerShell avec élévation de privilèges pour nettoyer les états DSC.

  ```powershell
  $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
    "$env:windir\system32\configuration\*.mof.checksum",
    "$env:windir\system32\configuration\PartialConfiguration\*.mof",
    "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
  )
  $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
  ```

## <a name="jea-virtual-accounts"></a>Comptes virtuels JEA

Si des configurations de session et des points de terminaison JEA sont configurés pour utiliser des comptes virtuels dans WMF 5.0, il n’en est pas de même après la mise à niveau vers WMF 5.1. Les commandes exécutées dans des sessions JEA s’exécutent alors sous l’identité de l’utilisateur connecté et non sous un compte d’administrateur temporaire, ce qui peut empêcher l’utilisateur d’exécuter des commandes nécessitant des privilèges élevés. Pour restaurer les comptes virtuels, vous devez désinscrire et réinscrire toute configuration de session utilisant des comptes virtuels.

```powershell
# Find the JEA endpoint by its name
$jea = Get-PSSessionConfiguration -Name MyJeaEndpoint

# Copy the cached PSSC file so it can be re-registered
$pssc = Copy-Item $jea.ConfigFilePath $env:temp -PassThru

# Unregister the current PSSC
Unregister-PSSessionConfiguration -Name $jea.Name

# Re-register the PSSC
Register-PSSessionConfiguration -Name $jea.Name -Path $pssc.FullName -Force

# Ensure the access policies remain the same
Set-PSSessionConfiguration -Name $newjea.Name -SecurityDescriptorSddl $jea.SecurityDescriptorSddl
```
