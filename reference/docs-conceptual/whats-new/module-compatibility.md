---
title: Compatibilité des modules PowerShell 7
ms.date: 02/03/2020
description: Cet article liste l’état de PowerShell 7 avec les modules PowerShell publiés pour d’autres produits Microsoft.
ms.openlocfilehash: f845b33881c93fa076d97adf101f4f3e006df73b
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501624"
---
# <a name="powershell-7-module-compatibility"></a>Compatibilité des modules PowerShell 7

Cet article contient une liste de modules PowerShell publiés par Microsoft. Ils assurent la gestion et la prise en charge de différents produits et services Microsoft. Soit ils ont été mis à jour de façon à fonctionner nativement avec PowerShell 7, soit leur compatibilité avec PowerShell 7 a été testée. Cette liste sera actualisée avec de nouvelles informations au fur et à mesure que d’autres modules auront été identifiés et testés.

Si vous avez des informations à partager ou des problèmes avec certains modules, entrez un problème dans le [référentiel WindowsCompatibility](https://github.com/PowerShell/WindowsCompatibility).

## <a name="windows-management-modules"></a>Modules de gestion Windows

Les modules de gestion Windows sont installés de différentes façons en fonction de l’édition de Windows et de la façon dont le module a été packagé pour cette édition.

Sur Windows Server, utilisez le nom de la fonctionnalité avec la cmdlet [Install-WindowsFeature](/powershell/module/servermanager/install-windowsfeature) en tant qu’administrateur. Par exemple :

```powershell
Install-WindowsFeature -Name ActiveDirectory
```

Sur Windows 10, les modules de gestion Windows sont accessibles en tant que **fonctionnalités Windows facultatives** ou **fonctionnalités Windows** . Les commandes suivantes doivent être exécutées **en tant qu’administrateur** dans une session avec élévation de privilèges.

- Pour les fonctionnalités Windows facultatives

  Pour obtenir la liste des fonctionnalités facultatives, exécutez la commande suivante :

  ```powershell
  Get-WindowsOptionalFeature -Online
  ```

  Pour installer la fonctionnalité :

  ```powershell
  Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V-Management-PowerShell
  ```

  Pour plus d’informations, consultez les pages suivantes :

  - [Get-WindowsOptionalFeature](/powershell/module/dism/get-windowsoptionalfeature)
  - [Enable-WindowsOptionalFeature](/powershell/module/dism/enable-windowsoptionalfeature)

- Pour les fonctionnalités Windows

  Pour obtenir la liste des fonctionnalités Windows, exécutez la commande suivante :

  ```powershell
  Get-WindowsCapability -online
  ```

  Comme vous pouvez le constater, le nom du package de fonctionnalités se termine par `~~~~0.0.1.0`. Vous devez utiliser le nom complet pour pouvoir installer la fonctionnalité :

  ```powershell
  Add-WindowsCapability -Online -Name Rsat.ServerManager.Tools~~~~0.0.1.0
  ```

  Pour plus d’informations, consultez les pages suivantes :

  - [Get-WindowsCapability](/powershell/module/dism/get-windowscapability)
  - [Add-WindowsCapability](/powershell/module/dism/add-windowscapability)

### <a name="module-list"></a>Liste des modules

| Nom du module                        | Statut                               | Systèmes d’exploitation pris en charge                       |
| ---------------------------------- | ------------------------------------ | ---------------------------------- |
| Active Directory                    | Compatible nativement                  | Windows Server 1809 (et versions ultérieures) avec RSAT-AD-PowerShell<br>Windows 10 1809 (et versions ultérieures) avec Rsat.ActiveDirectory.DS-LDS.Tools |
| ADDSDeployment                     | Fonctionne avec la couche de compatibilité       |  Windows Server 2019 1809+         |
| ADFS                               | Non testé avec la couche de compatibilité    |                                    |
| AppBackgroundTask                  | Compatible nativement                  | Windows 10 1903 (et versions ultérieures)                   |
| AppLocker                          | Non testé avec la couche de compatibilité    |                                    |
| AppvClient                         | Non testé avec la couche de compatibilité    |                                    |
| Appx                               | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures) |
| AssignedAccess                     | Compatible nativement                  | Windows 10 1809 (et versions ultérieures)                   |
| BestPractices                      | Non pris en charge par la couche de compatibilité |                                    |
| BitLocker                          | Compatible nativement                  | Windows Server 1809 (et versions ultérieures) avec BitLocker<br>Windows 10 1809 (et versions ultérieures) |
| BitsTransfer                       | Compatible nativement                  | Windows Server 20H1<br>Windows 10 20H1 |
| BootEventCollector                 | Non testé avec la couche de compatibilité    |                                        |
| BranchCache                        | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures) |
| CimCmdlets                         | Compatible nativement                  | Intégré à PowerShell 7 |
| ClusterAwareUpdating               | Non testé avec la couche de compatibilité    |                         |
| ConfigCI                           | Non testé avec la couche de compatibilité    |                         |
| Defender                           | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)  |
| DeliveryOptimization               | Compatible nativement                  | Windows Server 1903 (et versions ultérieures)<br>Windows 10 1903 (et versions ultérieures)  |
| DFSN                               | Compatible nativement                  | Windows Server 1809 (et versions ultérieures) avec FS-DFS-Namespace<br>Windows 10 1809 (et versions ultérieures) avec Rsat.FailoverCluster.Management.Tools |
| DFSR                               | Non testé avec la couche de compatibilité    |                                   |
| DhcpServer                         | Non testé avec la couche de compatibilité    |                                   |
| DirectAccessClientComponents       | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)  |
| Dism                               | Compatible nativement                  | Windows Server 1903 (et versions ultérieures)<br>Windows 10 1903 (et versions ultérieures)  |
| DnsClient                          | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)  |
| DnsServer                          | Compatible nativement                  | Windows Server 1809 (et versions ultérieures) avec DNS ou RSAT-DNS-Server<br>Windows 10 1809 (et versions ultérieures) avec Rsat.Dns.Tools |
| EventTracingManagement             | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)  |
| FailoverClusters                   | Non testé avec la couche de compatibilité    |                                  |
| FailoverClusterSet                 | Non testé avec la couche de compatibilité    |                                  |
| FileServerResourceManager          | Compatible nativement                  | Windows Server 1809 (et versions ultérieures) avec FS-Resource-Manager |
| GroupPolicy                        | Non testé avec la couche de compatibilité    |                                               |
| HgsClient                          | Compatible nativement                  | Windows Server 1903 (et versions ultérieures) avec Hyper-V ou RSAT-Shielded-VM-Tools<br>Windows 10 1903 (et versions ultérieures) avec Rsat.Shielded.VM.Tools |
| HgsDiagnostics                     | Compatible nativement                  | Windows Server 1809 (et versions ultérieures) avec Hyper-V ou RSAT-Shielded-VM-Tools<br>Windows 10 1809 (et versions ultérieures) avec Rsat.Shielded.VM.Tools |
| Hyper-V                            | Compatible nativement                  | Windows Server 1809 (et versions ultérieures) avec Hyper-V-PowerShell<br>Windows 10 1809 (et versions ultérieures) avec Microsoft-Hyper-V-Management-PowerShell |
| IISAdministration                  | Non testé avec la couche de compatibilité    |                                               |
| International                      | Compatible nativement                  | Windows Server 1903 (et versions ultérieures)<br>Windows 10 1903 (et versions ultérieures)      |
| IpamServer                         | Non testé avec la couche de compatibilité    |                                               |
| iSCSI                              | Non testé avec la couche de compatibilité    |                                               |
| IscsiTarget                        | Non testé avec la couche de compatibilité    |                                               |
| ISE                                | Non testé avec la couche de compatibilité    |                                               |
| Kds                                | Compatible nativement                  | Windows Server 20H1<br>Windows 10 20H1        |
| Microsoft.PowerShell.Archive       | Compatible nativement                  | Intégré à PowerShell 7                       |
| Microsoft.PowerShell.Diagnostics   | Compatible nativement                  | Intégré à PowerShell 7                       |
| Microsoft.PowerShell.Host          | Compatible nativement                  | Intégré à PowerShell 7                       |
| Microsoft.PowerShell.LocalAccounts | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)      |
| Microsoft.PowerShell.Management    | Compatible nativement                  | Intégré à PowerShell 7                       |
| Microsoft.PowerShell.ODataUtils    | Non testé avec la couche de compatibilité    |                                               |
| Microsoft.PowerShell.Security      | Compatible nativement                  | Intégré à PowerShell 7                       |
| Microsoft.PowerShell.Utility       | Compatible nativement                  | Intégré à PowerShell 7                       |
| Microsoft.WSMan.Management         | Compatible nativement                  | Intégré à PowerShell 7                       |
| MMAgent                            | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)      |
| MPIO                               | Compatible nativement                  | Windows Server 1809 (et versions ultérieures) avec Multipath-IO        |
| MsDtc                              | Non testé avec la couche de compatibilité    |                                               |
| NetAdapter                         | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)      |
| NetConnection                      | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)      |
| NetEventPacketCapture              | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)      |
| NetLbfo                            | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)      |
| NetLldpAgent                       | Non testé avec la couche de compatibilité    |                                               |
| NetNat                             | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)      |
| NetQos                             | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)      |
| NetSecurity                        | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)      |
| NetSwitchTeam                      | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)      |
| NetTCPIP                           | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)      |
| NetWNV                             | Non testé avec la couche de compatibilité    |                                               |
| NetworkConnectivityStatus          | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)      |
| NetworkController                  | Non testé avec la couche de compatibilité    |                                               |
| NetworkControllerDiagnostics       | Non testé avec la couche de compatibilité    |                                               |
| NetworkLoadBalancingClusters       | Non testé avec la couche de compatibilité    |                                               |
| NetworkSwitchManager               | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)      |
| NetworkTransition                  | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)      |
| NFS                                | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures) avec Rsat.ServerManager.Tools |
| PackageManagement                  | Compatible nativement                  | Intégré à PowerShell 7                       |
| PcsvDevice                         | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)      |
| PersistentMemory                   | Non testé avec la couche de compatibilité    |                                               |
| PKI                                | Non testé avec la couche de compatibilité    |                                               |
| PnpDevice                          | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)      |
| PowerShellGet                      | Compatible nativement                  | Intégré à PowerShell 7                       |
| PrintManagement                    | Compatible nativement                  | Windows Server 1903 (et versions ultérieures) avec Print-Services<br>Windows 10 1903 (et versions ultérieures)  |
| ProcessMitigations                 | Compatible nativement                  | Windows Server 1903 (et versions ultérieures)<br>Windows 10 1903 (et versions ultérieures)      |
| Approvisionnement                       | Non testé avec la couche de compatibilité    |                                               |
| PSDesiredStateConfiguration        | Partiellement                            | Intégré à PowerShell 7                       |
| PSDiagnostics                      | Compatible nativement                  | Intégré à PowerShell 7                       |
| PSScheduledJob                     | Non pris en charge par la couche de compatibilité | Intégré à PowerShell 5.1                     |
| PSWorkflow                         | Non testé avec la couche de compatibilité    |                                               |
| PSWorkflowUtility                  | Non testé avec la couche de compatibilité    |                                               |
| RemoteAccess                       | Non testé avec la couche de compatibilité    |                                               |
| RemoteDesktop                      | Non testé avec la couche de compatibilité    |                                               |
| ScheduledTasks                     | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)      |
| SecureBoot                         | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)      |
| ServerCore                         | Non testé avec la couche de compatibilité    |                                               |
| ServerManager                      | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures) avec Rsat.ServerManager.Tools<br>_Voir les remarques ci-dessous_ |
| ServerManagerTasks                 | Non testé avec la couche de compatibilité    |                                               |
| ShieldedVMDataFile                 | Compatible nativement                  | Windows Server 1903 (et versions ultérieures) avec RSAT-Shielded-VM-Tools<br>Windows 10 1903 (et versions ultérieures) avec Rsat.Shielded.VM.Tools |
| ShieldedVMProvisioning             | Compatible nativement                  | Windows Server 1809 (et versions ultérieures) avec HostGuardian<br>Windows 10 1809 (et versions ultérieures) avec HostGuardian  |
| ShieldedVMTemplate                 | Compatible nativement                  | Windows Server 1809 (et versions ultérieures) avec RSAT-Shielded-VM-Tools<br>Windows 10 1809 (et versions ultérieures) avec Rsat.Shielded.VM.Tools |
| SmbShare                           | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)      |
| SmbWitness                         | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)      |
| SMISConfig                         | Compatible nativement                  | Windows Server 1903 (et versions ultérieures) avec WindowsStorageManagementService |
| SMS                                | Non testé avec la couche de compatibilité    |                                               |
| SoftwareInventoryLogging           | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)                          |
| StartLayout                        | Compatible nativement                  | Windows Server 1809 (et versions ultérieures) avec Desktop Experience<br>Windows 10 1809 (et versions ultérieures) |
| Stockage                            | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)      |
| StorageBusCache                    | Non testé avec la couche de compatibilité    |                                               |
| StorageMigrationService            | Non testé avec la couche de compatibilité    |                                               |
| StorageQOS                         | Compatible nativement                  | Windows Server 1809 (et versions ultérieures) avec RSAT-Clustering-PowerShell<br>Windows 10 1809 (et versions ultérieures) avec Rsat.FailoverCluster.Management.Tools |
| StorageReplica                     | Non testé avec la couche de compatibilité    |                                               |
| SyncShare                          | Compatible nativement                  | Windows Server 1809 (et versions ultérieures) avec FS-SyncShareService |
| SystemInsights                     | Non testé avec la couche de compatibilité    |                                               |
| TLS                                | Non testé avec la couche de compatibilité    |                                               |
| TroubleshootingPack                | Compatible nativement                  | Windows 10 1903 (et versions ultérieures)                              |
| TrustedPlatformModule              | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)      |
| UEV                                | Compatible nativement                  | Windows Server ? Version future de Server avec Expérience utilisateur ?<br>Windows 10 1903 (et versions ultérieures) |
| UpdateServices                     | Non pris en charge par la couche de compatibilité |                                               |
| VpnClient                          | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)      |
| Wdac                               | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)      |
| WebAdministration                  | Non testé avec la couche de compatibilité    |                                               |
| WHEA                               | Compatible nativement                  | Windows Server 1903 (et versions ultérieures)<br>Windows 10 1903 (et versions ultérieures)      |
| WindowsDeveloperLicense            | Compatible nativement                  | Windows Server 1809 (et versions ultérieures) avec Desktop Experience<br>Windows 10 1809 (et versions ultérieures) |
| WindowsErrorReporting              | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)      |
| WindowsSearch                      | Compatible nativement                  | Windows 10 1903 (et versions ultérieures)                              |
| WindowsServerBackup                | Compatible nativement                  | Windows Server 19H2 avec Windows-Server-Backup |
| WindowsUpdate                      | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)       |
| WindowsUpdateProvider              | Compatible nativement                  | Windows Server 1809 (et versions ultérieures)<br>Windows 10 1809 (et versions ultérieures)       |

## <a name="notes"></a>Notes

### <a name="servermanager-module"></a>Module ServerManager

Le module présente des problèmes de compatibilité mineurs avec la sortie mise en forme de PowerShell 7. Par exemple, l’applet de commande `Get-WindowsFeature` retourne l’objet approprié avec toutes les propriétés, mais la mise en forme par défaut fait que certaines propriétés paraissent vides. Vous pouvez accéder aux valeurs dans les propriétés de l’objet à l’aide de `Select-Object` ou par un accès membre direct.

