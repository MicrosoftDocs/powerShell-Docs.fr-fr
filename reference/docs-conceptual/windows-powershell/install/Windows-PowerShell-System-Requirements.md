---
ms.date: 12/06/2019
keywords: powershell,applet de commande
title: Configuration requise pour Windows PowerShell
ms.openlocfilehash: 883da2f91c4a0b46e4bccbacd9933a52f8f476f6
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89236082"
---
# <a name="windows-powershell-system-requirements"></a>Configuration requise pour Windows PowerShell

Cet article répertorie la configuration requise pour Windows PowerShell 3.0, Windows PowerShell 4.0, Windows PowerShell 5.0 et Windows PowerShell 5.1, ainsi que des fonctionnalités spéciales, telles que l’Environnement d’écriture de scripts intégré (ISE) de Windows PowerShell, les commandes Common Information Model (CIM) et les flux de travail.

Windows® 8.1 et Windows Server® 2012 R2 incluent tous les programmes obligatoires. Cet article est conçu pour les utilisateurs de versions antérieures de Windows.

## <a name="operating-system-requirements"></a>Système d'exploitation requis

### <a name="windows-powershell-51"></a>Windows PowerShell 5.1

Windows PowerShell 5.1 s’exécute sur les versions suivantes de Windows. Pour exécuter Windows PowerShell 5.1, installez Windows Management Framework 5.1. Pour plus d’informations, voir [Installer et configurer WMF 5.1](../wmf/setup/install-configure.md).

|              Version de Windows               |                           Configuration requise                            |
| ------------------------------------------ | ----------------------------------------------------------------------- |
| Windows Server 2019                        | Installé par défaut                                                    |
| Windows Server 2016                        | Installé par défaut                                                    |
| Windows Server 2012 R2                     | Installer [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows Server 2012                        | Installer [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows Server 2008 R2 avec Service Pack 1 | Installer [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows 10 version 1607 et supérieure             | Installé par défaut                                                    |
| Windows 10 version 1507, 1511              | Installer [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows 8.1                                | Installer [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows 7 avec Service Pack 1              | Installer [Windows Management Framework 5.1](https://aka.ms/wmf5download) |

### <a name="windows-powershell-50"></a>Windows PowerShell 5.0

Windows PowerShell 5.0 s’exécute sur les versions suivantes de Windows. Pour exécuter Windows PowerShell 5.0, installez Windows Management Framework 5.1. Pour plus d’informations, voir [Installer et configurer WMF 5.1](../wmf/setup/install-configure.md). Windows Management Framework 5.1 remplace Windows Management Framework 5.0.

|              Version de Windows               |                           Configuration requise                            |
| ------------------------------------------ | ----------------------------------------------------------------------- |
| Windows Server 2019                        | Version ultérieure installée par défaut                                     |
| Windows Server 2016                        | Version ultérieure installée par défaut                                     |
| Windows Server 2012 R2                     | Installer [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows Server 2012                        | Installer [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows Server 2008 R2 avec Service Pack 1 | Installer [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows 10 version 1607 et supérieure             | Version ultérieure installée par défaut                                     |
| Windows 10 version 1507, 1511              | Installé par défaut                                                    |
| Windows 8.1                                | Installer [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows 7 avec Service Pack 1              | Installer [Windows Management Framework 5.1](https://aka.ms/wmf5download) |

### <a name="windows-powershell-40"></a>Windows PowerShell 4.0

Windows PowerShell 4.0 s’exécute sur les versions suivantes de Windows. Pour exécuter Windows PowerShell 4.0, installez la version spécifiée de Windows Management Framework pour votre système d’exploitation.

|               Version de Windows               |                                             Configuration requise                                             |
| ------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| Windows 8.1                                 | Installé par défaut                                                                                       |
| Windows Server 2012 R2                      | Installé par défaut                                                                                       |
| Windows® 7 avec Service Pack 1              | Installer [Windows Management Framework 4.0](https://www.microsoft.com/download/details.aspx?id=40855) |
| Windows Server® 2008 R2 avec Service Pack 1 | Installer [Windows Management Framework 4.0](https://www.microsoft.com/download/details.aspx?id=40855) |

### <a name="windows-powershell-30"></a>Windows PowerShell 3.0

Windows PowerShell 3.0 s’exécute sur les versions suivantes de Windows. Pour exécuter Windows PowerShell 3.0, installez la version spécifiée de Windows Management Framework pour votre système d’exploitation.

|               Version de Windows               |                                             Configuration requise                                             |
| ------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| Windows 8                                   | Installé par défaut                                                                                       |
| Windows Server 2012                         | Installé par défaut                                                                                       |
| Windows® 7 avec Service Pack 1              | Installer [Windows Management Framework 3.0](https://www.microsoft.com/download/details.aspx?id=34595) |
| Windows Server® 2008 R2 avec Service Pack 1 | Installer [Windows Management Framework 3.0](https://www.microsoft.com/download/details.aspx?id=34595) |
| Windows Server 2008 avec Service Pack 2     | Installer [Windows Management Framework 3.0](https://www.microsoft.com/download/details.aspx?id=34595) |

## <a name="microsoft-net-framework-requirements"></a>Configuration requise pour Microsoft .NET Framework

Le tableau suivant indique la configuration requise de .NET Framework pour Windows PowerShell.

|        Version         |                                                                                 Configuration requise pour .NET                                                                                  |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Windows PowerShell 5.1 | Requiert l’installation complète de Microsoft .NET Framework 4.5. Windows 8.1 et Windows Server 2012 R2 incluent le Microsoft .NET Framework 4.5 par défaut.                           |
| Windows PowerShell 5.0 | Requiert l’installation complète de Microsoft .NET Framework 4.5. Windows 8.1 et Windows Server 2012 R2 incluent le Microsoft .NET Framework 4.5 par défaut.                           |
| Windows PowerShell 4.0 | Requiert l’installation complète de Microsoft .NET Framework 4.5. Windows 8.1 et Windows Server 2012 R2 incluent le Microsoft .NET Framework 4.5 par défaut.                           |
| Windows PowerShell 3.0 | Requiert l’installation complète de Microsoft .NET Framework 4. Windows 8 et Windows Server 2012 incluent le Microsoft .NET Framework 4.5 par défaut, ce qui répond à cette exigence. |

Utilisez les liens suivants pour télécharger Microsoft .NET Framework à partir du Centre de téléchargement Microsoft.

|                     Version                      |                                                     Lien                                                     |
| ------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ |
| .NET Framework 4.5 (`dotNetFx45_Full_setup.exe`) | [Microsoft .NET Framework 4.5](https://go.microsoft.com/fwlink/?LinkID=242919)                               |
| .NET Framework 4 (`dotNetFx40_Full_setup.exe`)   | [Microsoft .NET Framework 4 (programme d’installation web)](https://www.microsoft.com/download/details.aspx?id=17851) |

## <a name="windows-management-framework-40"></a>Windows Management Framework 4.0

Windows PowerShell 5.0 nécessite la préinstallation de Windows Management Framework 4.0 sur Windows Server 2008 R2 SP1 et Windows 7 SP1.

## <a name="ws-management-30"></a>WS-Management 3.0

Windows PowerShell 3.0 et Windows PowerShell 4.0 nécessitent WS-Management 3.0, qui prend en charge le service WinRM et le protocole WSMan. Ce programme est inclus dans Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 et Windows Management Framework 3.0.

## <a name="windows-management-instrumentation-30"></a>WMI (Windows Management Instrumentation) 3.0

Windows PowerShell 3.0 et Windows PowerShell 4.0 nécessitent WMI (Windows Management Instrumentation) 3.0. Ce programme est inclus dans Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 et Windows Management Framework 3.0. Si ce programme n’est pas installé sur l’ordinateur, les fonctionnalités qui requièrent WMI, telles que les commandes CIM, ne fonctionnent pas.

## <a name="common-language-runtime-40"></a>Common Language Runtime (CLR) 4.0

Windows PowerShell 3.0, Windows PowerShell 4.0 et Windows PowerShell 5.0 sont compilés pour le Common Language Runtime (CLR) 4.0.

## <a name="graphical-user-interface-requirements"></a>Configuration requise de l’interface graphique utilisateur

Windows PowerShell est une application de console qui ne nécessite pas d’interface graphique utilisateur.
Elle est particulièrement adaptée aux ordinateurs qui n’ont pas d’écran, de moniteur ou d’interface utilisateur, notamment avec les options d’installation minimale de Windows Server 2012 R2 ou Windows Server 2012.

Certains éléments requièrent une interface graphique utilisateur. Pour plus d’informations, consultez l’article d’aide sur chaque élément.

- Environnement d’écriture de scripts intégré (ISE) de Windows PowerShell. Pour plus d'informations, consultez [Présentation de Windows PowerShell ISE](/powershell/scripting/components/ise/introducing-the-windows-powershell-ise).
- Applets de commande
  - [Out-GridView](/powershell/module/microsoft.powershell.utility/out-gridview)
  - [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command)
  - [Show-ControlPanelItem](/powershell/module/Microsoft.PowerShell.Management/Show-ControlPanelItem)
  - [Show-EventLog](/powershell/module/Microsoft.PowerShell.Management/Show-EventLog)
- Paramètres
  - Paramètre **ShowWindow** de l’applet de commande [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help).
  - Paramètre **ShowSecurityDescriptorUI** des applets de commande [Register-PSSessionConfiguration](/powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration) et [Set-PSSessionConfiguration](/powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration).

## <a name="windows-powershell-engine-requirements"></a>Configuration requise pour le moteur Windows PowerShell

Windows PowerShell 4.0 est conçu pour offrir une compatibilité descendante avec Windows PowerShell 3.0 et Windows PowerShell 2.0. Les applets de commande, fournisseurs, composants logiciels enfichables, modules et scripts écrits pour Windows PowerShell 2.0 et Windows PowerShell 3.0 s’exécutent sans modification dans Windows PowerShell 4.0.

Toutefois, en raison d’une modification de la stratégie d’activation du runtime dans Microsoft .NET Framework 4, les programmes hôtes de Windows PowerShell écrits pour Windows PowerShell 2.0 et compilés avec le Common Language Runtime (CLR) 2.0 ne peuvent pas s’exécuter sans modification dans Windows PowerShell 3.0, qui est compilé avec le CLR 4.0.

La configuration minimale requise pour le moteur Windows PowerShell 2.0 est Microsoft .NET Framework 2.0.50727. Cette condition est remplie par Microsoft .NET Framework 3.5 Service Pack 1. Cette exigence n’est pas remplie par Microsoft .NET Framework 4 ni par les versions ultérieures de Microsoft .NET Framework.

Pour plus d’informations sur l’ajout ou l’installation du moteur Windows PowerShell 2.0, et l’ajout ou l’installation des versions requises du Microsoft .NET Framework, consultez [Installation du moteur Windows PowerShell 2.0](Installing-the-Windows-PowerShell-2.0-Engine.md). Pour plus d’informations sur le démarrage du moteur Windows PowerShell 2.0, consultez [Démarrage du moteur Windows PowerShell 2.0](../Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="windows-preinstallation-environment"></a>Environnement de préinstallation Windows

Windows PowerShell 2.0, Windows PowerShell 3.0 et Windows PowerShell 4.0 s’exécutent dans l’environnement de préinstallation Windows (Windows PE). Toutefois, les applets de commande suivantes ne sont pas prises en charge.

- Applets de commande du service de transfert intelligent en arrière-plan (BITS). Pour plus d’informations, consultez [BitsTransfer](/powershell/module/bitstransfer/?view=win10-ps).
- [Get-EventLog](/powershell/module/Microsoft.PowerShell.Management/Get-EventLog)
- [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent)
- [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help)
- [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)

Le service **WinRM** n’est pas présent sur Windows PE.

## <a name="see-also"></a>Voir aussi

[Installation de Windows PowerShell](Installing-Windows-PowerShell.md)

[Démarrage de Windows PowerShell](../Starting-Windows-PowerShell.md)

[Windows Management Framework](../wmf/overview.md)
