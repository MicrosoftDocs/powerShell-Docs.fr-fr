---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 64a29aa87507e65a182837df538c5e695c420cb3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="uninstallation-instructions"></a>Instructions de désinstallation

## <a name="using-command-prompt"></a>Utilisation de l’invite de commandes
1.  Ouvrez une **invite de commandes.**
2.  Exécutez le [Lanceur autonome Windows Update](https://support.microsoft.com/en-us/kb/934307) comme indiqué ci-dessous :

Sur Windows Server 2012 R2 et Windows 8.1 :
```powershell
wusa /uninstall /kb:3134758
```
Sur Windows Server 2012 :
```powershell
wusa /uninstall /kb:3134759
```
Sur Windows Server 2008 R2 SP1 et Windows 7 SP1 :
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a>Utilisation du Panneau de configuration
1.  Ouvrez le **Panneau de configuration.**
2.  Ouvrez **Programmes**, puis **Désinstaller un programme.**
3.  Cliquez sur **Afficher les mises à jour installées.**
4.  Sélectionnez **Windows Management Framework 5.0** dans la liste des mises à jour installées. Cela correspond à *KB3134758*, *KB3134759* ou *KB3134760*. Cliquez sur **Désinstaller.**
