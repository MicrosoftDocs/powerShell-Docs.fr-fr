---
ms.date: 02/03/2020
keywords: powershell,core
title: Historique des versions des modules et des cmdlets
ms.openlocfilehash: e421201d74da2cc74b1bd57529fb3c3e5245ecae
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995435"
---
# <a name="release-history-of-modules-and-cmdlets"></a>Historique des versions des modules et des cmdlets

Cet article répertorie les modules et les cmdlets fournis avec différentes versions de PowerShell. C’est un résumé des informations contenues dans les notes de publication. Vous trouverez des informations plus détaillées dans les notes de publication :

- [Nouveautés de PowerShell Core 6.2](what-s-new-in-powershell-core-62.md)
- [Nouveautés de PowerShell Core 6.1](what-s-new-in-powershell-core-61.md)
- [Nouveautés de PowerShell Core 6.0](what-s-new-in-powershell-core-60.md)
- [Modifications avec rupture dans PowerShell Core 6.0](breaking-changes-ps6.md)
- [Problèmes connus dans PowerShell Core 6.0](known-issues-ps6.md)

Il s’agit d’un travail en cours. Aidez-nous à conserver ces informations à jour.

## <a name="module-release-history"></a>Historique des versions des modules

|         Nom du module/version PS          |   5,1   |   6.x   |   7.0   |   7.1   |     Remarque     |
| ----------------------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| CimCmdlets                                | &check; | &check; | &check; | &check; | Windows uniquement |
| ISE (introduit dans 2.0)                   | &check; |         |         |         | Windows uniquement |
| Microsoft.PowerShell.Archive              | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Core                 | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Diagnostics          | &check; | &check; | &check; | &check; | Windows uniquement |
| Microsoft.PowerShell.Host                 | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.LocalAccounts        | &check; |         |         |         | Windows uniquement |
| Microsoft.PowerShell.Management           | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.ODataUtils           | &check; |         |         |         | Windows uniquement |
| Microsoft.PowerShell.Operation.Validation | &check; |         |         |         | Windows uniquement |
| Microsoft.PowerShell.Security             | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Utility              | &check; | &check; | &check; | &check; |              |
| Microsoft.WsMan.Management                | &check; | &check; | &check; | &check; | Windows uniquement |
| PackageManagement                         | &check; | &check; | &check; | &check; |              |
| PowershellGet                             | &check; | &check; | &check; | &check; |              |
| PSDesiredStateConfiguration               | &check; | &check; | &check; | &check; |              |
| PSDiagnostics                             | &check; | &check; | &check; | &check; | Windows uniquement |
| PSReadline 1.x                            | &check; |         |         |         | Windows uniquement |
| PSReadline 2.x                            |         | &check; | &check; | &check; |              |
| PSScheduledJob                            | &check; |         |         |         | Windows uniquement |
| PSWorkflow                                | &check; |         |         |         | Windows uniquement |
| PSWorkflowUtility                         | &check; |         |         |         | Windows uniquement |
| ThreadJob                                 |         | &check; | &check; | &check; |              |

## <a name="cmdlet-release-history"></a>Historique des versions des cmdlets

### <a name="cimcmdlets"></a>CimCmdlets

|         Nom de l’applet de commande         |   5,1   |   6.x   |   7.0   |   7.1   |     Remarque     |
| --------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Export-BinaryMiLog          | &check; | &check; | &check; | &check; | Windows uniquement |
| Get-CimAssociatedInstance   | &check; | &check; | &check; | &check; | Windows uniquement |
| Get-CimClass                | &check; | &check; | &check; | &check; | Windows uniquement |
| Get-CimInstance             | &check; | &check; | &check; | &check; | Windows uniquement |
| Get-CimSession              | &check; | &check; | &check; | &check; | Windows uniquement |
| Import-BinaryMiLog          | &check; | &check; | &check; | &check; | Windows uniquement |
| Invoke-CimMethod            | &check; | &check; | &check; | &check; | Windows uniquement |
| New-CimInstance             | &check; | &check; | &check; | &check; | Windows uniquement |
| New-CimSession              | &check; | &check; | &check; | &check; | Windows uniquement |
| New-CimSessionOption        | &check; | &check; | &check; | &check; | Windows uniquement |
| Register-CimIndicationEvent | &check; | &check; | &check; | &check; | Windows uniquement |
| Remove-CimInstance          | &check; | &check; | &check; | &check; | Windows uniquement |
| Remove-CimSession           | &check; | &check; | &check; | &check; | Windows uniquement |
| Set-CimInstance             | &check; | &check; | &check; | &check; | Windows uniquement |

### <a name="ise-introduced-in-20"></a>ISE (introduit dans 2.0)

|    Nom de l’applet de commande    |   5,1   | 6.x  |  7.0  |  7.1  |     Remarque     |
| ----------------- | :-----: | :--- | :---: | :---: | ------------ |
| Get-IseSnippet    | &check; |      |       |       | Windows uniquement |
| Import-IseSnippet | &check; |      |       |       | Windows uniquement |
| New-IseSnippet    | &check; |      |       |       | Windows uniquement |


### <a name="microsoftpowershellarchive"></a>Microsoft.PowerShell.Archive

|   Nom de l’applet de commande    |   5,1   |   6.x   |   7.0   |   7.1   | Remarque |
| ---------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Compress-Archive | &check; | &check; | &check; | &check; |      |
| Expand-Archive   | &check; | &check; | &check; | &check; |      |

### <a name="microsoftpowershellcore"></a>Microsoft.PowerShell.Core

|            Nom de l’applet de commande            |   5,1   |   6.x   |   7.0   |   7.1   |            Remarque            |
| --------------------------------- | :-----: | :-----: | :-----: | :-----: | -------------------------- |
| Add-History                       | &check; | &check; | &check; | &check; |                            |
| Add-PSSnapin                      | &check; |         |         |         | Windows uniquement               |
| Clear-History                     | &check; | &check; | &check; | &check; |                            |
| Clear-Host                        | &check; | &check; | &check; | &check; |                            |
| Connect-PSSession                 | &check; | &check; | &check; | &check; | Windows uniquement               |
| Debug-Job                         | &check; | &check; | &check; | &check; |                            |
| Disable-ExperimentalFeature       |         |   6.2   | &check; | &check; |                            |
| Disable-PSRemoting                | &check; | &check; | &check; | &check; | Windows uniquement               |
| Disable-PSSessionConfiguration    | &check; | &check; | &check; | &check; | Windows uniquement               |
| Disconnect-PSSession              | &check; | &check; | &check; | &check; | Windows uniquement               |
| Enable-ExperimentalFeature        |         |   6.2   | &check; | &check; |                            |
| Enable-PSRemoting                 | &check; | &check; | &check; | &check; | Windows uniquement               |
| Enable-PSSessionConfiguration     | &check; | &check; | &check; | &check; | Windows uniquement               |
| Enter-PSHostProcess               | &check; | &check; | &check; | &check; | Ajout de la prise en charge de Linux dans 6.2 |
| Enter-PSSession                   | &check; | &check; | &check; | &check; |                            |
| Exit-PSHostProcess                | &check; | &check; | &check; | &check; | Ajout de la prise en charge de Linux dans 6.2 |
| Exit-PSSession                    | &check; | &check; | &check; | &check; |                            |
| Export-Console                    | &check; |         |         |         | Windows uniquement               |
| Export-ModuleMember               | &check; | &check; | &check; | &check; |                            |
| ForEach-Object                    | &check; | &check; | &check; | &check; |                            |
| Get-Command                       | &check; | &check; | &check; | &check; |                            |
| Get-ExperimentalFeature           |         |   6.2   | &check; | &check; |                            |
| Get-Help                          | &check; | &check; | &check; | &check; |                            |
| Get-History                       | &check; | &check; | &check; | &check; |                            |
| Get-Job                           | &check; | &check; | &check; | &check; |                            |
| Get-Module                        | &check; | &check; | &check; | &check; |                            |
| Get-PSHostProcessInfo             | &check; | &check; | &check; | &check; | Ajout de la prise en charge de Linux dans 6.2 |
| Get-PSSession                     | &check; | &check; | &check; | &check; |                            |
| Get-PSSessionCapability           | &check; | &check; | &check; | &check; |                            |
| Get-PSSessionConfiguration        | &check; | &check; | &check; | &check; |                            |
| Get-PSSnapin                      | &check; |         |         |         | Windows uniquement               |
| Get-Verb                          | &check; |         |         |         | Windows uniquement               |
| Module d’importation                     | &check; | &check; | &check; | &check; |                            |
| Invoke-Command                    | &check; | &check; | &check; | &check; |                            |
| Invoke-History                    | &check; | &check; | &check; | &check; |                            |
| New-Module                        | &check; | &check; | &check; | &check; |                            |
| New-ModuleManifest                | &check; | &check; | &check; | &check; |                            |
| New-PSRoleCapabilityFile          | &check; | &check; | &check; | &check; |                            |
| New-PSSession                     | &check; | &check; | &check; | &check; |                            |
| New-PSSessionConfigurationFile    | &check; | &check; | &check; | &check; | Windows uniquement               |
| New-PSSessionOption               | &check; | &check; | &check; | &check; |                            |
| New-PSTransportOption             | &check; | &check; | &check; | &check; |                            |
| Out-Default                       | &check; | &check; | &check; | &check; |                            |
| Out-Host                          | &check; | &check; | &check; | &check; |                            |
| Out-Null                          | &check; | &check; | &check; | &check; |                            |
| Receive-Job                       | &check; | &check; | &check; | &check; |                            |
| Receive-PSSession                 | &check; | &check; | &check; | &check; | Windows uniquement               |
| Register-ArgumentCompleter        | &check; | &check; | &check; | &check; |                            |
| Register-PSSessionConfiguration   | &check; | &check; | &check; | &check; | Windows uniquement               |
| Remove-Job                        | &check; | &check; | &check; | &check; |                            |
| Remove-Module                     | &check; | &check; | &check; | &check; |                            |
| Remove-PSSession                  | &check; | &check; | &check; | &check; |                            |
| Remove-PSSnapin                   | &check; |         |         |         | Windows uniquement               |
| Resume-Job                        | &check; |         |         |         |                            |
| Save-Help                         | &check; | &check; | &check; | &check; |                            |
| Set-PSDebug                       | &check; | &check; | &check; | &check; |                            |
| Set-PSSessionConfiguration        | &check; | &check; | &check; | &check; | Windows uniquement               |
| Set-StrictMode                    | &check; | &check; | &check; | &check; |                            |
| Start-Job                         | &check; | &check; | &check; | &check; |                            |
| Stop-Job                          | &check; | &check; | &check; | &check; |                            |
| Suspend-Job                       | &check; |         |         |         | Windows uniquement               |
| Test-ModuleManifest               | &check; | &check; | &check; | &check; |                            |
| Test-PSSessionConfigurationFile   | &check; | &check; | &check; | &check; | Windows uniquement               |
| Unregister-PSSessionConfiguration | &check; | &check; | &check; | &check; | Windows uniquement               |
| Update-Help                       | &check; | &check; | &check; | &check; |                            |
| Wait-Job                          | &check; | &check; | &check; | &check; |                            |
| Where-Object                      | &check; | &check; | &check; | &check; |                            |

### <a name="microsoftpowershelldiagnostics"></a>Microsoft.PowerShell.Diagnostics

|  Nom de l’applet de commande   |   5,1   |   6.x   |   7.0   |   7.1   |     Remarque     |
| -------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Export-Counter | &check; |         |         |         | Windows uniquement |
| Get-Counter    | &check; |         | &check; | &check; | Windows uniquement |
| Get-WinEvent   | &check; | &check; | &check; | &check; | Windows uniquement |
| Import-Counter | &check; |         |         |         | Windows uniquement |
| New-WinEvent   | &check; | &check; | &check; | &check; | Windows uniquement |

### <a name="microsoftpowershellhost"></a>Microsoft.PowerShell.Host

|   Nom de l’applet de commande    |   5,1   |   6.x   |   7.0   |   7.1   | Remarque |
| ---------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Start-Transcript | &check; | &check; | &check; | &check; |      |
| Stop-Transcript  | &check; | &check; | &check; | &check; |      |

### <a name="microsoftpowershelllocalaccounts"></a>Microsoft.PowerShell.LocalAccounts

|       Nom de l’applet de commande       |   5,1   | 6.x  |  7.0  |  7.1  |     Remarque     |
| ----------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Add-LocalGroupMember    | &check; |      |       |       | Windows uniquement |
| Disable-LocalUser       | &check; |      |       |       | Windows uniquement |
| Enable-LocalUser        | &check; |      |       |       | Windows uniquement |
| Get-LocalGroup          | &check; |      |       |       | Windows uniquement |
| Get-LocalGroupMember    | &check; |      |       |       | Windows uniquement |
| Get-LocalUser           | &check; |      |       |       | Windows uniquement |
| New-LocalGroup          | &check; |      |       |       | Windows uniquement |
| New-LocalUser           | &check; |      |       |       | Windows uniquement |
| Remove-LocalGroup       | &check; |      |       |       | Windows uniquement |
| Remove-LocalGroupMember | &check; |      |       |       | Windows uniquement |
| Remove-LocalUser        | &check; |      |       |       | Windows uniquement |
| Rename-LocalGroup       | &check; |      |       |       | Windows uniquement |
| Rename-LocalUser        | &check; |      |       |       | Windows uniquement |
| Set-LocalGroup          | &check; |      |       |       | Windows uniquement |
| Set-LocalUser           | &check; |      |       |       | Windows uniquement |

### <a name="microsoftpowershellmanagement"></a>Microsoft.PowerShell.Management

|          Nom de l’applet de commande          |   5,1   |   6.x   |   7.0   |   7.1   |               Remarque               |
| ----------------------------- | :-----: | :-----: | :-----: | :-----: | -------------------------------- |
| Add-Computer                  | &check; |         |         |         | Windows uniquement                     |
| Add-Content                   | &check; | &check; | &check; | &check; |                                  |
| Checkpoint-Computer           | &check; |         |         |         | Windows uniquement                     |
| Clear-Content                 | &check; | &check; | &check; | &check; |                                  |
| Clear-EventLog                | &check; |         |         |         | Windows uniquement                     |
| Clear-Item                    | &check; | &check; | &check; | &check; |                                  |
| Clear-ItemProperty            | &check; | &check; | &check; | &check; |                                  |
| Clear-RecycleBin              | &check; |         | &check; | &check; | Windows uniquement                     |
| Complete-Transaction          | &check; |         |         |         | Windows uniquement                     |
| Convert-Path                  | &check; | &check; | &check; | &check; |                                  |
| Copy-Item                     | &check; | &check; | &check; | &check; |                                  |
| Copy-ItemProperty             | &check; | &check; | &check; | &check; |                                  |
| Debug-Process                 | &check; | &check; | &check; | &check; |                                  |
| Disable-ComputerRestore       | &check; |         |         |         | Windows uniquement                     |
| Enable-ComputerRestore        | &check; |         |         |         | Windows uniquement                     |
| Get-ChildItem                 | &check; | &check; | &check; | &check; |                                  |
| Get-Clipboard                 | &check; |         | &check; | &check; | Pas de prise en charge sur macOS           |
| Get-ComputerInfo              | &check; | &check; | &check; | &check; |                                  |
| Get-ComputerRestorePoint      | &check; |         |         |         | Windows uniquement                     |
| Get-Content                   | &check; | &check; | &check; | &check; |                                  |
| Get-ControlPanelItem          | &check; |         |         |         | Windows uniquement                     |
| Get-EventLog                  | &check; |         |         |         | Windows uniquement                     |
| Get-HotFix                    | &check; |         | &check; | &check; | Windows uniquement                     |
| Get-Item                      | &check; | &check; | &check; | &check; |                                  |
| Get-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| Get-ItemPropertyValue         | &check; | &check; | &check; | &check; |                                  |
| Get-Location                  | &check; | &check; | &check; | &check; |                                  |
| Get-Process                   | &check; | &check; | &check; | &check; |                                  |
| Get-PSDrive                   | &check; | &check; | &check; | &check; |                                  |
| Get-PSProvider                | &check; | &check; | &check; | &check; |                                  |
| Get-Service                   | &check; | &check; | &check; | &check; | Windows uniquement                     |
| Get-TimeZone                  | &check; | &check; | &check; | &check; |                                  |
| Get-Transaction               | &check; |         |         |         | Windows uniquement                     |
| Get-WmiObject                 | &check; |         |         |         | Windows uniquement                     |
| Invoke-Item                   | &check; | &check; | &check; | &check; |                                  |
| Invoke-WmiMethod              | &check; |         |         |         | Windows uniquement                     |
| Join-Path                     | &check; | &check; | &check; | &check; |                                  |
| Limit-EventLog                | &check; |         |         |         | Windows uniquement                     |
| Move-Item                     | &check; | &check; | &check; | &check; |                                  |
| Move-ItemProperty             | &check; | &check; | &check; | &check; |                                  |
| New-EventLog                  | &check; |         |         |         | Windows uniquement                     |
| New-Item                      | &check; | &check; | &check; | &check; |                                  |
| New-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| New-PSDrive                   | &check; | &check; | &check; | &check; |                                  |
| New-Service                   | &check; | &check; | &check; | &check; | Windows uniquement                     |
| New-WebServiceProxy           | &check; |         |         |         | Windows uniquement                     |
| Pop-Location                  | &check; | &check; | &check; | &check; |                                  |
| Push-Location                 | &check; | &check; | &check; | &check; |                                  |
| Register-WmiEvent             | &check; |         |         |         | Windows uniquement                     |
| Remove-Computer               | &check; |         |         |         | Windows uniquement                     |
| Remove-EventLog               | &check; |         |         |         | Windows uniquement                     |
| Remove-Item                   | &check; | &check; | &check; | &check; |                                  |
| Remove-ItemProperty           | &check; | &check; | &check; | &check; |                                  |
| Remove-PSDrive                | &check; | &check; | &check; | &check; |                                  |
| Remove-Service                |         | &check; | &check; | &check; | Windows uniquement                     |
| Remove-WmiObject              | &check; |         |         |         | Windows uniquement                     |
| Rename-Computer               | &check; | &check; | &check; | &check; |                                  |
| Rename-Item                   | &check; | &check; | &check; | &check; |                                  |
| Rename-ItemProperty           | &check; | &check; | &check; | &check; |                                  |
| Reset-ComputerMachinePassword | &check; |         |         |         | Windows uniquement                     |
| Resolve-Path                  | &check; | &check; | &check; | &check; |                                  |
| Restart-Computer              | &check; | &check; | &check; | &check; |                                  |
| Restart-Service               | &check; | &check; | &check; | &check; | Windows uniquement                     |
| Restore-Computer              | &check; |         |         |         | Windows uniquement                     |
| Resume-Service                | &check; | &check; | &check; | &check; | Windows uniquement                     |
| Set-Clipboard                 | &check; |         | &check; | &check; |                                  |
| Set-Content                   | &check; | &check; | &check; | &check; |                                  |
| Set-Item                      | &check; | &check; | &check; | &check; |                                  |
| Set-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| Set-Location                  | &check; | &check; | &check; | &check; |                                  |
| Set-Service                   | &check; | &check; | &check; | &check; | Windows uniquement                     |
| Set-TimeZone                  | &check; | &check; | &check; | &check; |                                  |
| Set-WmiInstance               | &check; |         |         |         | Windows uniquement                     |
| Show-ControlPanelItem         | &check; |         |         |         | Windows uniquement                     |
| Show-EventLog                 | &check; |         |         |         | Windows uniquement                     |
| Split-Path                    | &check; | &check; | &check; | &check; |                                  |
| Start-Process                 | &check; | &check; | &check; | &check; |                                  |
| Start-Service                 | &check; | &check; | &check; | &check; | Windows uniquement                     |
| Start-Transaction             | &check; |         |         |         | Windows uniquement                     |
| Stop-Computer                 | &check; | &check; | &check; | &check; | Ajout de la prise en charge de Linux/macOS dans 7.0 |
| Stop-Process                  | &check; | &check; | &check; | &check; |                                  |
| Stop-Service                  | &check; | &check; | &check; | &check; | Windows uniquement                     |
| Suspend-Service               | &check; | &check; | &check; | &check; | Windows uniquement                     |
| Test-ComputerSecureChannel    | &check; |         |         |         | Windows uniquement                     |
| Test-Connection               | &check; | &check; | &check; | &check; |                                  |
| Test-Path                     | &check; | &check; | &check; | &check; |                                  |
| Undo-Transaction              | &check; |         |         |         | Windows uniquement                     |
| Use-Transaction               | &check; |         |         |         | Windows uniquement                     |
| Wait-Process                  | &check; | &check; | &check; | &check; | Ne fonctionne pas sur Linux/macOS     |
| Write-EventLog                | &check; |         |         |         | Windows uniquement                     |

### <a name="microsoftpowershellodatautils"></a>Microsoft.PowerShell.ODataUtils

|        Nom de l’applet de commande        |   5,1   | 6.x  |  7.0  |  7.1  |     Remarque     |
| ------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Export-ODataEndpointProxy | &check; |      |       |       | Windows uniquement |

### <a name="microsoftpowershelloperationvalidation"></a>Microsoft.PowerShell.Operation.Validation

|        Nom de l’applet de commande         |   5,1   | 6.x  |  7.0  |  7.1  |     Remarque     |
| -------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Get-OperationValidation    | &check; |      |       |       | Windows uniquement |
| Invoke-OperationValidation | &check; |      |       |       | Windows uniquement |

### <a name="microsoftpowershellsecurity"></a>Microsoft.PowerShell.Security

|        Nom de l’applet de commande        |   5,1   |   6.x   |   7.0   |   7.1   |                  Remarque                   |
| ------------------------- | :-----: | :-----: | :-----: | :-----: | --------------------------------------- |
| ConvertFrom-SecureString  | &check; | &check; | &check; | &check; |                                         |
| ConvertTo-SecureString    | &check; | &check; | &check; | &check; |                                         |
| Get-Acl                   | &check; | &check; | &check; | &check; | Windows uniquement                            |
| Get-AuthenticodeSignature | &check; | &check; | &check; | &check; | Windows uniquement                            |
| Get-CmsMessage            | &check; | &check; | &check; | &check; | Windows uniquement                            |
| Get-Credential            | &check; | &check; | &check; | &check; |                                         |
| Get-ExecutionPolicy       | &check; | &check; | &check; | &check; | Retourne **Unrestricted** (sans restriction) sur Linux/macOS |
| Get-PfxCertificate        | &check; | &check; | &check; | &check; |                                         |
| New-FileCatalog           | &check; | &check; | &check; | &check; | Windows uniquement                            |
| Protect-CmsMessage        | &check; | &check; | &check; | &check; | Windows uniquement                            |
| Set-Acl                   | &check; | &check; | &check; | &check; | Windows uniquement                            |
| Set-AuthenticodeSignature | &check; | &check; | &check; | &check; | Windows uniquement                            |
| Set-ExecutionPolicy       | &check; | &check; | &check; | &check; | Ne fait rien sur Linux/macOS             |
| Test-FileCatalog          | &check; | &check; | &check; | &check; | Windows uniquement                            |
| Unprotect-CmsMessage      | &check; | &check; | &check; | &check; | Windows uniquement                            |

### <a name="microsoftpowershellutility"></a>Microsoft.PowerShell.Utility

|        Nom de l’applet de commande        |   5,1   |   6.x   |   7.0   |   7.1   |                   Remarque                    |
| ------------------------- | :-----: | :-----: | :-----: | :-----: | ----------------------------------------- |
| Add-Member                | &check; | &check; | &check; | &check; |                                           |
| Add-Type                  | &check; | &check; | &check; | &check; |                                           |
| Clear-Variable            | &check; | &check; | &check; | &check; |                                           |
| Compare-Object            | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-Csv           | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-Json          | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-Markdown      |         |   6.1   | &check; | &check; |                                           |
| ConvertFrom-SddlString    | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-String        | &check; |         |         |         |                                           |
| ConvertFrom-StringData    | &check; | &check; | &check; | &check; |                                           |
| Convert-String            | &check; |         |         |         |                                           |
| ConvertTo-Csv             | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Html            | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Json            | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Xml             | &check; | &check; | &check; | &check; |                                           |
| Debug-Runspace            | &check; | &check; | &check; | &check; |                                           |
| Disable-PSBreakpoint      | &check; | &check; | &check; | &check; |                                           |
| Disable-RunspaceDebug     | &check; | &check; | &check; | &check; |                                           |
| Enable-PSBreakpoint       | &check; | &check; | &check; | &check; |                                           |
| Enable-RunspaceDebug      | &check; | &check; | &check; | &check; |                                           |
| Export-Alias              | &check; | &check; | &check; | &check; |                                           |
| Export-Clixml             | &check; | &check; | &check; | &check; |                                           |
| Export-Csv                | &check; | &check; | &check; | &check; |                                           |
| Export-FormatData         | &check; | &check; | &check; | &check; |                                           |
| Export-PSSession          | &check; | &check; | &check; | &check; |                                           |
| Format-Custom             | &check; | &check; | &check; | &check; |                                           |
| Format-Hex                | &check; | &check; | &check; | &check; |                                           |
| Format-List               | &check; | &check; | &check; | &check; |                                           |
| Format-Table              | &check; | &check; | &check; | &check; |                                           |
| Format-Wide               | &check; | &check; | &check; | &check; |                                           |
| Get-Alias                 | &check; | &check; | &check; | &check; |                                           |
| Get-Culture               | &check; | &check; | &check; | &check; |                                           |
| Get-Date                  | &check; | &check; | &check; | &check; |                                           |
| Get-Error                 |         |         | &check; | &check; |                                           |
| Get-Event                 | &check; | &check; | &check; | &check; | Aucune source d’événements disponible sur Linux/macOS |
| Get-EventSubscriber       | &check; | &check; | &check; | &check; |                                           |
| Get-FileHash              | &check; | &check; | &check; | &check; |                                           |
| Get-FormatData            | &check; | &check; | &check; | &check; |                                           |
| Get-Host                  | &check; | &check; | &check; | &check; |                                           |
| Get-MarkdownOption        |         |   6.1   | &check; | &check; |                                           |
| Get-Member                | &check; | &check; | &check; | &check; |                                           |
| Get-PSBreakpoint          | &check; | &check; | &check; | &check; |                                           |
| Get-PSCallStack           | &check; | &check; | &check; | &check; |                                           |
| Get-Random                | &check; | &check; | &check; | &check; |                                           |
| Get-Runspace              | &check; | &check; | &check; | &check; |                                           |
| Get-RunspaceDebug         | &check; | &check; | &check; | &check; |                                           |
| Get-TraceSource           | &check; | &check; | &check; | &check; |                                           |
| Get-TypeData              | &check; | &check; | &check; | &check; |                                           |
| Get-UICulture             | &check; | &check; | &check; | &check; |                                           |
| Get-Unique                | &check; | &check; | &check; | &check; |                                           |
| Get-Uptime                |         | &check; | &check; | &check; |                                           |
| Get-Variable              | &check; | &check; | &check; | &check; |                                           |
| Get-Verb                  |         | &check; | &check; | &check; |                                           |
| Group-Object              | &check; | &check; | &check; | &check; |                                           |
| Import-Alias              | &check; | &check; | &check; | &check; |                                           |
| Import-Clixml             | &check; | &check; | &check; | &check; |                                           |
| Import-Csv                | &check; | &check; | &check; | &check; |                                           |
| Import-LocalizedData      | &check; | &check; | &check; | &check; |                                           |
| Import-PowerShellDataFile | &check; | &check; | &check; | &check; |                                           |
| Import-PSSession          | &check; | &check; | &check; | &check; |                                           |
| Invoke-Expression         | &check; | &check; | &check; | &check; |                                           |
| Invoke-RestMethod         | &check; | &check; | &check; | &check; |                                           |
| Invoke-WebRequest         | &check; | &check; | &check; | &check; |                                           |
| Join-String               |         | &check; | &check; | &check; |                                           |
| Measure-Command           | &check; | &check; | &check; | &check; |                                           |
| Measure-Object            | &check; | &check; | &check; | &check; |                                           |
| New-Alias                 | &check; | &check; | &check; | &check; |                                           |
| New-Event                 | &check; | &check; | &check; | &check; | Aucune source d’événements disponible sur Linux/macOS |
| New-Guid                  | &check; | &check; | &check; | &check; |                                           |
| New-Object                | &check; | &check; | &check; | &check; |                                           |
| New-TemporaryFile         | &check; | &check; | &check; | &check; |                                           |
| New-TimeSpan              | &check; | &check; | &check; | &check; |                                           |
| New-Variable              | &check; | &check; | &check; | &check; |                                           |
| Out-File                  | &check; | &check; | &check; | &check; |                                           |
| Out-GridView              | &check; |         | &check; | &check; |                                           |
| Out-Printer               | &check; |         | &check; | &check; |                                           |
| Out-String                | &check; | &check; | &check; | &check; |                                           |
| Read-Host                 | &check; | &check; | &check; | &check; |                                           |
| Register-EngineEvent      | &check; | &check; | &check; | &check; | Aucune source d’événements disponible sur Linux/macOS |
| Register-ObjectEvent      | &check; | &check; | &check; | &check; |                                           |
| Remove-Alias              |         | &check; | &check; | &check; |                                           |
| Remove-Event              | &check; | &check; | &check; | &check; | Aucune source d’événements disponible sur Linux/macOS |
| Remove-PSBreakpoint       | &check; | &check; | &check; | &check; |                                           |
| Remove-TypeData           | &check; | &check; | &check; | &check; |                                           |
| Remove-Variable           | &check; | &check; | &check; | &check; |                                           |
| Select-Object             | &check; | &check; | &check; | &check; |                                           |
| Select-String             | &check; | &check; | &check; | &check; |                                           |
| Select-Xml                | &check; | &check; | &check; | &check; |                                           |
| Send-MailMessage          | &check; | &check; | &check; | &check; |                                           |
| Set-Alias                 | &check; | &check; | &check; | &check; |                                           |
| Set-Date                  | &check; | &check; | &check; | &check; |                                           |
| Set-MarkdownOption        |         |   6.1   | &check; | &check; |                                           |
| Set-PSBreakpoint          | &check; | &check; | &check; | &check; |                                           |
| Set-TraceSource           | &check; | &check; | &check; | &check; |                                           |
| Set-Variable              | &check; | &check; | &check; | &check; |                                           |
| Show-Command              | &check; |         | &check; | &check; |                                           |
| Show-Markdown             |         |   6.1   | &check; | &check; |                                           |
| Sort-Object               | &check; | &check; | &check; | &check; |                                           |
| Start-Sleep               | &check; | &check; | &check; | &check; |                                           |
| Tee-Object                | &check; | &check; | &check; | &check; |                                           |
| Test-Json                 |         | &check; | &check; | &check; |                                           |
| Trace-Command             | &check; | &check; | &check; | &check; |                                           |
| Unblock-File              | &check; | &check; | &check; | &check; | Ajout de la prise en charge pour macOS dans 7.0            |
| Unregister-Event          | &check; | &check; | &check; | &check; | Aucune source d’événements disponible sur Linux/macOS |
| Update-FormatData         | &check; | &check; | &check; | &check; |                                           |
| Update-List               | &check; |         | &check; | &check; |                                           |
| Update-TypeData           | &check; | &check; | &check; | &check; |                                           |
| Wait-Debugger             | &check; | &check; | &check; | &check; |                                           |
| Wait-Event                | &check; | &check; | &check; | &check; |                                           |
| Write-Debug               | &check; | &check; | &check; | &check; |                                           |
| Write-Error               | &check; | &check; | &check; | &check; |                                           |
| Write-Host                | &check; | &check; | &check; | &check; |                                           |
| Write-Information         | &check; | &check; | &check; | &check; |                                           |
| Write-Output              | &check; | &check; | &check; | &check; |                                           |
| Write-Progress            | &check; | &check; | &check; | &check; |                                           |
| Write-Verbose             | &check; | &check; | &check; | &check; |                                           |
| Write-Warning             | &check; | &check; | &check; | &check; |                                           |

### <a name="microsoftwsmanmanagement"></a>Microsoft.WsMan.Management

|      Nom de l’applet de commande       |   5,1   |   6.x   |   7.0   |   7.1   |     Remarque     |
| ---------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Connect-WSMan          | &check; | &check; | &check; | &check; | Windows uniquement |
| Disable-WSManCredSSP   | &check; | &check; | &check; | &check; | Windows uniquement |
| Disconnect-WSMan       | &check; | &check; | &check; | &check; | Windows uniquement |
| Enable-WSManCredSSP    | &check; | &check; | &check; | &check; | Windows uniquement |
| Get-WSManCredSSP       | &check; | &check; | &check; | &check; | Windows uniquement |
| Get-WSManInstance      | &check; | &check; | &check; | &check; | Windows uniquement |
| Invoke-WSManAction     | &check; | &check; | &check; | &check; | Windows uniquement |
| New-WSManInstance      | &check; | &check; | &check; | &check; | Windows uniquement |
| New-WSManSessionOption | &check; | &check; | &check; | &check; | Windows uniquement |
| Remove-WSManInstance   | &check; | &check; | &check; | &check; | Windows uniquement |
| Set-WSManInstance      | &check; | &check; | &check; | &check; | Windows uniquement |
| Set-WSManQuickConfig   | &check; | &check; | &check; | &check; | Windows uniquement |
| Test-WSMan             | &check; | &check; | &check; | &check; | Windows uniquement |

### <a name="packagemanagement"></a>PackageManagement

|       Nom de l’applet de commande        |   5,1   |   6.x   |   7.0   |   7.1   | Remarque |
| ------------------------ | :-----: | :-----: | :-----: | :-----: | ---- |
| Find-Package             | &check; | &check; | &check; | &check; |      |
| Find-PackageProvider     | &check; | &check; | &check; | &check; |      |
| Get-Package              | &check; | &check; | &check; | &check; |      |
| Get-PackageProvider      | &check; | &check; | &check; | &check; |      |
| Get-PackageSource        | &check; | &check; | &check; | &check; |      |
| Import-PackageProvider   | &check; | &check; | &check; | &check; |      |
| Install-Package          | &check; | &check; | &check; | &check; |      |
| Install-PackageProvider  | &check; | &check; | &check; | &check; |      |
| Register-PackageSource   | &check; | &check; | &check; | &check; |      |
| Save-Package             | &check; | &check; | &check; | &check; |      |
| Set-PackageSource        | &check; | &check; | &check; | &check; |      |
| Uninstall-Package        | &check; | &check; | &check; | &check; |      |
| Unregister-PackageSource | &check; | &check; | &check; | &check; |      |

### <a name="powershellget"></a>PowershellGet

|           Nom de l’applet de commande           |   5,1   |   6.x   |   7.0   |   7.1   | Remarque |
| ------------------------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Find-Command                    | &check; | &check; | &check; | &check; |      |
| Find-DscResource                | &check; | &check; | &check; | &check; |      |
| Find-Module                     | &check; | &check; | &check; | &check; |      |
| Find-RoleCapability             | &check; | &check; | &check; | &check; |      |
| Find-Script                     | &check; | &check; | &check; | &check; |      |
| Get-CredsFromCredentialProvider |         | &check; | &check; | &check; |      |
| Get-InstalledModule             | &check; | &check; | &check; | &check; |      |
| Get-InstalledScript             | &check; | &check; | &check; | &check; |      |
| Get-PSRepository                | &check; | &check; | &check; | &check; |      |
| Install-Module                  | &check; | &check; | &check; | &check; |      |
| Install-Script                  | &check; | &check; | &check; | &check; |      |
| New-ScriptFileInfo              | &check; | &check; | &check; | &check; |      |
| Publish-Module                  | &check; | &check; | &check; | &check; |      |
| Publish-Script                  | &check; | &check; | &check; | &check; |      |
| Register-PSRepository           | &check; | &check; | &check; | &check; |      |
| Save-Module                     | &check; | &check; | &check; | &check; |      |
| Save-Script                     | &check; | &check; | &check; | &check; |      |
| Set-PSRepository                | &check; | &check; | &check; | &check; |      |
| Test-ScriptFileInfo             | &check; | &check; | &check; | &check; |      |
| Uninstall-Module                | &check; | &check; | &check; | &check; |      |
| Uninstall-Script                | &check; | &check; | &check; | &check; |      |
| Unregister-PSRepository         | &check; | &check; | &check; | &check; |      |
| Update-Module                   | &check; | &check; | &check; | &check; |      |
| Update-ModuleManifest           | &check; | &check; | &check; | &check; |      |
| Update-Script                   | &check; | &check; | &check; | &check; |      |
| Update-ScriptFileInfo           | &check; | &check; | &check; | &check; |      |

### <a name="psdesiredstateconfiguration"></a>PSDesiredStateConfiguration

|                Nom de l’applet de commande                 |   5,1   |   6.x   |   7.0   |   7.1   |     Remarque     |
| ------------------------------------------ | :-----: | :-----: | :-----: | :-----: | ------------ |
| Add-NodeKeys                               |         | &check; |         |         |              |
| ConvertTo-MOFInstance                      |         | &check; |         |         |              |
| Disable-DscDebug                           | &check; |         |         |         | Windows uniquement |
| Enable-DscDebug                            | &check; |         |         |         | Windows uniquement |
| Generate-VersionInfo                       |         | &check; |         |         |              |
| Get-CompatibleVersionAddtionaPropertiesStr |         | &check; |         |         |              |
| Get-ComplexResourceQualifier               |         | &check; |         |         |              |
| Get-ConfigurationErrorCount                |         | &check; |         |         |              |
| Get-DscConfiguration                       | &check; |         |         |         | Windows uniquement |
| Get-DscConfigurationStatus                 | &check; |         |         |         | Windows uniquement |
| Get-DscLocalConfigurationManager           | &check; |         |         |         | Windows uniquement |
| Get-DscResource                            | &check; | &check; | &check; | &check; |              |
| Get-DSCResourceModules                     |         | &check; |         |         |              |
| Get-EncryptedPassword                      |         | &check; |         |         |              |
| Get-InnerMostErrorRecord                   |         | &check; |         |         |              |
| Get-MofInstanceName                        |         | &check; |         |         |              |
| Get-MofInstanceText                        |         | &check; |         |         |              |
| Get-PositionInfo                           |         | &check; |         |         |              |
| Get-PSCurrentConfigurationNode             |         | &check; |         |         |              |
| Get-PSDefaultConfigurationDocument         |         | &check; |         |         |              |
| Get-PSMetaConfigDocumentInstVersionInfo    |         | &check; |         |         |              |
| Get-PSMetaConfigurationProcessed           |         | &check; |         |         |              |
| Get-PSTopConfigurationName                 |         | &check; |         |         |              |
| Get-PublicKeyFromFile                      |         | &check; |         |         |              |
| Get-PublicKeyFromStore                     |         | &check; |         |         |              |
| Initialize-ConfigurationRuntimeState       |         | &check; |         |         |              |
| Invoke-DscResource                         | &check; |         | &check; | &check; |              |
| New-DSCCheckSum                            | &check; | &check; | &check; | &check; |              |
| Publish-DscConfiguration                   | &check; |         |         |         | Windows uniquement |
| Remove-DscConfigurationDocument            | &check; |         |         |         | Windows uniquement |
| Restore-DscConfiguration                   | &check; |         |         |         | Windows uniquement |
| Set-DscLocalConfigurationManager           | &check; |         |         |         | Windows uniquement |
| Set-NodeExclusiveResources                 |         | &check; |         |         |              |
| Set-NodeManager                            |         | &check; |         |         |              |
| Set-NodeResources                          |         | &check; |         |         |              |
| Set-NodeResourceSource                     |         | &check; |         |         |              |
| Set-PSCurrentConfigurationNode             |         | &check; |         |         |              |
| Set-PSDefaultConfigurationDocument         |         | &check; |         |         |              |
| Set-PSMetaConfigDocInsProcessedBeforeMeta  |         | &check; |         |         |              |
| Set-PSMetaConfigVersionInfoV2              |         | &check; |         |         |              |
| Set-PSTopConfigurationName                 |         | &check; |         |         |              |
| Start-DscConfiguration                     | &check; |         |         |         | Windows uniquement |
| Stop-DscConfiguration                      | &check; |         |         |         | Windows uniquement |
| Test-ConflictingResources                  |         | &check; |         |         |              |
| Test-DscConfiguration                      | &check; |         |         |         | Windows uniquement |
| Test-ModuleReloadRequired                  |         | &check; |         |         |              |
| Test-MofInstanceText                       |         | &check; |         |         |              |
| Test-NodeManager                           |         | &check; |         |         |              |
| Test-NodeResources                         |         | &check; |         |         |              |
| Test-NodeResourceSource                    |         | &check; |         |         |              |
| Update-ConfigurationDocumentRef            |         | &check; |         |         |              |
| Update-ConfigurationErrorCount             |         | &check; |         |         |              |
| Update-DependsOn                           |         | &check; |         |         |              |
| Update-DscConfiguration                    | &check; |         |         |         | Windows uniquement |
| Update-LocalConfigManager                  |         | &check; |         |         |              |
| Update-ModuleVersion                       |         | &check; |         |         |              |
| ValidateUpdate-ConfigurationData           |         | &check; |         |         |              |
| Write-Log                                  |         | &check; |         |         |              |
| Write-MetaConfigFile                       |         | &check; |         |         |              |
| Write-NodeMOFFile                          |         | &check; |         |         |              |

### <a name="psdiagnostics"></a>PSDiagnostics

|         Nom de l’applet de commande          |   5,1   |   6.x   |   7.0   |   7.1   |     Remarque     |
| ---------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Disable-PSTrace              | &check; |   6.2   | &check; | &check; | Windows uniquement |
| Disable-PSWSManCombinedTrace | &check; |   6.2   | &check; | &check; | Windows uniquement |
| Disable-WSManTrace           | &check; | &check; | &check; | &check; | Windows uniquement |
| Enable-PSTrace               | &check; | &check; | &check; | &check; | Windows uniquement |
| Enable-PSWSManCombinedTrace  | &check; | &check; | &check; | &check; | Windows uniquement |
| Enable-WSManTrace            | &check; |   6.2   | &check; | &check; | Windows uniquement |
| Get-LogProperties            | &check; |   6.2   | &check; | &check; | Windows uniquement |
| Set-LogProperties            | &check; |   6.2   | &check; | &check; | Windows uniquement |
| Start-Trace                  | &check; |   6.2   | &check; | &check; | Windows uniquement |
| Stop-Trace                   | &check; |   6.2   | &check; | &check; | Windows uniquement |

### <a name="psreadline"></a>PSReadline

|         Nom de l’applet de commande         |   5,1   |   6.x   |   7.0   |   7.1   | Remarque |
| --------------------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Get-PSReadlineKeyHandler    | &check; | &check; | &check; | &check; |      |
| Get-PSReadlineOption        | &check; | &check; | &check; | &check; |      |
| PSConsoleHostReadline       | &check; | &check; | &check; | &check; |      |
| Remove-PSReadlineKeyHandler | &check; | &check; | &check; | &check; |      |
| Set-PSReadlineKeyHandler    | &check; | &check; | &check; | &check; |      |
| Set-PSReadlineOption        | &check; | &check; | &check; | &check; |      |

### <a name="psscheduledjob"></a>PSScheduledJob

|       Nom de l’applet de commande       |   5,1   | 6.x  |  7.0  |  7.1  |     Remarque     |
| ----------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Add-JobTrigger          | &check; |      |       |       | Windows uniquement |
| Disable-JobTrigger      | &check; |      |       |       | Windows uniquement |
| Disable-ScheduledJob    | &check; |      |       |       | Windows uniquement |
| Enable-JobTrigger       | &check; |      |       |       | Windows uniquement |
| Enable-ScheduledJob     | &check; |      |       |       | Windows uniquement |
| Get-JobTrigger          | &check; |      |       |       | Windows uniquement |
| Get-ScheduledJob        | &check; |      |       |       | Windows uniquement |
| Get-ScheduledJobOption  | &check; |      |       |       | Windows uniquement |
| New-JobTrigger          | &check; |      |       |       | Windows uniquement |
| New-ScheduledJobOption  | &check; |      |       |       | Windows uniquement |
| Register-ScheduledJob   | &check; |      |       |       | Windows uniquement |
| Remove-JobTrigger       | &check; |      |       |       | Windows uniquement |
| Set-JobTrigger          | &check; |      |       |       | Windows uniquement |
| Set-ScheduledJob        | &check; |      |       |       | Windows uniquement |
| Set-ScheduledJobOption  | &check; |      |       |       | Windows uniquement |
| Unregister-ScheduledJob | &check; |      |       |       | Windows uniquement |

### <a name="psworkflow--psworkflowutility"></a>PSWorkflow & PSWorkflowUtility

|          Nom de l’applet de commande          |   5,1   | 6.x  |  7.0  |  7.1  |     Remarque     |
| ----------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| New-PSWorkflowExecutionOption | &check; |      |       |       | Windows uniquement |
| New-PSWorkflowSession         | &check; |      |       |       | Windows uniquement |
| Invoke-AsWorkflow             | &check; |      |       |       | Windows uniquement |

### <a name="threadjob"></a>ThreadJob

|   Nom de l’applet de commande   |  5,1  |   6.x   |   7.0   |   7.1   | Remarque |
| --------------- | :---: | :-----: | :-----: | :-----: | ---- |
| Start-ThreadJob |       | &check; | &check; | &check; |      |
