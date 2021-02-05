---
title: Installation de PowerShell Core sur Arm
description: Installation de PowerShell Core sur les systèmes Arm
ms.date: 11/11/2020
ms.openlocfilehash: 1477b99767c19d24f8540714942f63c8347550e9
ms.sourcegitcommit: ef25c8bc95df12697725958c9814f0e187cfc683
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98130137"
---
# <a name="powershell-core-on-arm"></a>PowerShell Core sur Arm

La prise en charge de PowerShell sur Arm est basée sur les **stratégies de cycle de vie du système d’exploitation .NET Core pris en charge**.

PowerShell 7.0 repose sur la [politique de cycle de vie du système d’exploitation .NET Core 3.1 pris en charge](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) et gère les plateformes suivantes :

|         Système d''exploitation          |          Version           | Architectures |          Cycle de vie           |
| ------------------- | -------------------------- | ------------- | ---------------------------- |
| Windows Nano Server | Version 1803              | Arm32         | [Windows][Windows-lifecycle] |
| Alpine Linux        | 3.10+                      | Arm64         | [Alpine][Alpine-lifecycle]   |
| Debian              | 9+                         | Arm32, Arm64  | [Debian][Debian-lifecycle]   |
| Ubuntu              | 20.10, 20.04, 18.04, 16.04 | Arm32, Arm64  | [Ubuntu][Ubuntu-lifecycle]   |

PowerShell 7.1 repose sur la [politique de cycle de vie du système d’exploitation .NET 5.0 pris en charge](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md) et gère les plateformes suivantes :

|        Système d''exploitation         |          Version           | Architectures |          Cycle de vie           |
| ----------------- | -------------------------- | ------------- | ---------------------------- |
| Client Windows 10 | Version 1709+              | Arm64         | [Windows][Windows-lifecycle] |
| Alpine Linux      | 3.11+                      | Arm64         | [Alpine][Alpine-lifecycle]   |
| Debian            | 9+                         | Arm32, Arm64  | [Debian][Debian-lifecycle]   |
| Ubuntu            | 20.10, 20.04, 18.04, 16.04 | Arm32, Arm64  | [Ubuntu][Ubuntu-lifecycle]   |

[Windows-lifecycle]: https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet
[Alpine-lifecycle]: https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases
[Debian-lifecycle]: https://wiki.debian.org/DebianReleases
[Ubuntu-lifecycle]: https://wiki.ubuntu.com/Releases

Pour obtenir des instructions d’installation, consultez les articles suivants :

- [Windows 10 sur Arm](installing-powershell-core-on-windows.md#installing-the-zip-package)
- [Windows 10 IoT Entreprise](installing-powershell-core-on-windows.md#deploying-on-windows-10-iot-enterprise)
- [Windows 10 IoT Standard](installing-powershell-core-on-windows.md#deploying-on-windows-10-iot-core)
- [Raspbian](installing-powershell-core-on-linux.md#raspbian)
