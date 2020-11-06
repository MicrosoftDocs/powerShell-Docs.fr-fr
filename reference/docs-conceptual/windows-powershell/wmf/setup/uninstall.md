---
ms.date: 06/12/2017
title: Désinstaller WMF 5.0
description: Cet article explique comment désinstaller WMF des versions antérieures de Windows.
ms.openlocfilehash: d8078ea918db2c1cf9a7ddd6ea8d1413b593c0ff
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660811"
---
# <a name="uninstallation-instructions"></a>Instructions de désinstallation

## <a name="using-command-prompt"></a>Utilisation de l’invite de commandes

1. Ouvrez une **invite de commandes.**
2. Exécutez le [Lanceur autonome Windows Update](https://support.microsoft.com/kb/934307) comme indiqué ci-dessous :

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

1. Ouvrez le **Panneau de configuration.**
2. Ouvrez **Programmes** , puis **Désinstaller un programme.**
3. Cliquez sur **Afficher les mises à jour installées.**
4. Sélectionnez **Windows Management Framework 5.0** dans la liste des mises à jour installées. Cela correspond à *KB3134758* , *KB3134759* ou *KB3134760*. Cliquez sur **Désinstaller.**
