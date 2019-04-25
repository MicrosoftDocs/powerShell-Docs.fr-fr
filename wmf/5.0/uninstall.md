---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 385bb7223b19c8ace8088ba469e543721a527b99
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057512"
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
