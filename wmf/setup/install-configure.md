---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,configuration
contributor: keithb
title: Installer et configurer WMF 5.1
ms.openlocfilehash: cb223844c2a214846e7206bcb476fac9154fda4b
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855404"
---
# <a name="install-and-configure-wmf-51"></a>Installer et configurer WMF 5.1

> [!IMPORTANT]
> WMF 5.0 est remplacé par WMF 5.1. Les utilisateurs de WMF 5.0 doivent passer à WMF 5.1 pour profiter de la prise en charge.
> **WMF 5.1 nécessite le .NET Framework 4.5.2** (ou ultérieur). L’installation réussit, mais des fonctionnalités clés échouent si le .NET Framework 4.5.2 (ou ultérieur) n’est pas installé.

## <a name="download-and-install-the-wmf-51-package"></a>Télécharger et installer le package WMF 5.1

Téléchargez le package WMF 5.1 correspondant au système d’exploitation et à l’architecture sur lesquels vous souhaitez installer :

| Système d'exploitation       | Conditions préalables           | Liens de package                          |
|------------------------|-------------------------|----------------------------------------|
| Windows Server 2012 R2 |                         | [Win8.1AndW2K12R2-KB3191564-x64.msu][] |
| Windows Server 2012    |                         | [W2K12-KB3191565-x64.msu][]            |
| Windows Server 2008 R2 | [.NET Framework 4.5.2][]| [Win7AndW2K8R2-KB3191566-x64.ZIP][]    |
| Windows 8.1            |                         | **x64 :** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</br>**x86 :** [Win8.1-KB3191564-x86.msu][] |
| Windows 7 SP1          | [.NET Framework 4.5.2][]| **x64 :** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</br>**x86 :** [Win7-KB3191566-x86.ZIP][] |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

- La préversion de WMF 5.1 doit être désinstallée avant d’installer la version WMF 5.1 RTM.
- WMF 5.1 peut être installé directement sur WMF 5.0 ou WMF 4.0.
- Il n’est **pas nécessaire** d’installer WMF 4.0 avant d’installer WMF 5.1 sur Windows 7 et Windows Server 2008 R2.

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a>Installer WMF 5.1 pour Windows Server 2008 R2 et Windows 7

> [!NOTE]
> Les instructions d’installation pour Windows Server 2008 R2 et Windows 7 ont été modifiées et diffèrent désormais de celles des autres packages. Les instructions d’installation pour Windows Server 2012 R2, Windows Server 2012 et Windows 8.1 sont indiquées ci-dessous.

### <a name="installing-wmf-51-on-windows-server-2008-r2-and-windows-7"></a>Installer WMF 5.1 sur Windows Server 2008 R2 et Windows 7

1. Accédez au dossier dans lequel vous avez téléchargé le fichier ZIP.

2. Cliquez avec le bouton droit sur le fichier ZIP, puis sélectionnez « Extraire tout ». Le fichier ZIP contient 2 fichiers : un fichier MSU et le fichier de script Install-WMF5.1.PS1. Une fois le fichier ZIP décompressé, vous pouvez copier le contenu sur n’importe quel ordinateur exécutant Windows 7 ou Windows Server 2008 R2.

3. Après avoir extrait le contenu du fichier ZIP, ouvrez PowerShell en tant qu’administrateur, puis accédez au dossier dans lequel figure le contenu du fichier zip.

4. Exécutez le script Install-Wmf5.1.ps1 dans ce dossier et suivez les instructions. Ce script vérifie les prérequis sur l’ordinateur local et, s’ils sont respectés, installe WMF 5.1. Les prérequis sont répertoriés ci-dessous.

   Install-WMF5.1.ps1 accepte les paramètres suivants pour faciliter l’automatisation de l’installation sur Windows Server 2008 R2 et Windows 7 :

   - AcceptEula : quand ce paramètre est inclus, le CLUF est accepté automatiquement et n’est pas affiché.
   - AllowRestart : ce paramètre peut être utilisé uniquement si AcceptEula est spécifié. Si ce paramètre est inclus et qu’un redémarrage est nécessaire après l’installation de WMF 5.1, l’ordinateur redémarre sans invite dès l’installation terminée.

### <a name="wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1"></a>Prérequis de WMF 5.1 pour Windows Server 2008 R2 SP1 et Windows 7 SP1

L’installation de WMF 5.1 sur Windows Server 2008 R2 SP1 ou Windows 7 SP1 nécessite ce qui suit :

- Le dernier Service Pack doit est installé.
- WMF 3.0 **ne doit pas** être installé. L’installation de WMF 5.1 sur WMF 3.0 entraîne la perte de PSModulePath, ce qui peut provoquer l’échec d’autres applications. Avant d’installer WMF 5.1, vous devez soit désinstaller WMF 3.0, soit enregistrer PSModulePath et le restaurer manuellement au terme de l’installation de WMF 5.1.
- WMF 5.1 nécessite au moins [.NET Framework 4.5.2](https://www.microsoft.com/download/details.aspx?id=42642).
  Vous pouvez installer Microsoft .NET Framework 4.5.2 en suivant les instructions à l’emplacement du téléchargement.

## <a name="winrm-dependency"></a>Dépendance de WinRM

La Configuration de l’état souhaité (DSC) Windows PowerShell dépend de WinRM. WinRM n’est pas activé par défaut sur Windows Server 2008 R2 et Windows 7. Exécutez `Set-WSManQuickConfig` dans une session Windows PowerShell avec élévation des privilèges pour activer WinRM.

## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a>Installer WMF 5.1 pour Windows Server 2012 R2, Windows Server 2012 et Windows 8.1

### <a name="install-from-windows-file-explorer"></a>Avec l’Explorateur de fichiers Windows

1. Accédez au dossier dans lequel vous avez téléchargé le fichier MSU.
2. Double-cliquez sur le fichier MSU pour l’exécuter.

### <a name="installing-from-the-command-prompt"></a>Dans l’invite de commandes

1. Après avoir téléchargé le package correspondant à l’architecture de votre ordinateur, ouvrez une fenêtre d’invite de commandes avec des droits d’utilisateur élevés (Exécuter en tant qu’administrateur). Dans les options d’installation Server Core de Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1, une invite de commandes s’ouvre avec des droits d’utilisateur avec élévation de privilèges par défaut.
2. Accédez au dossier dans lequel vous avez téléchargé ou copié le package d’installation WMF 5.1.
3. Exécutez l’une des commandes suivantes :
   - Sur les ordinateurs qui exécutent Windows Server 2012 R2 ou Windows 8.1 x64, exécutez `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.
   - Sur les ordinateurs qui exécutent Windows Server 2012, exécutez `W2K12-KB3191565-x64.msu /quiet`.
   - Sur les ordinateurs qui exécutent Windows 8.1 x86, exécutez `Win8.1-KB3191564-x86.msu /quiet`.

> [!NOTE]
> L’installation de WMF 5.1 nécessite un redémarrage. L’option `/quiet` redémarre le système sans avertissement. Utilisez l’option `/norestart` pour éviter le redémarrage. Toutefois, WMF 5.1 ne sera pas installé tant que vous n’avez pas redémarré.
