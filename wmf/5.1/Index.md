---
ms.date: 2017-08-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: Notes de publication de WMF 5.1
ms.openlocfilehash: 3a6b7fb84d679d9bbe7a89e30c8c769e26f7381a
ms.sourcegitcommit: 3f49bd2e0b786e69c71393c00ad85d05a8466753
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2017
---
# <a name="windows-management-framework-wmf-51"></a>Windows Management Framework (WMF) 5.1 #

WMF offre aux utilisateurs la possibilité de mettre à jour les systèmes Windows existants avec les versions des composants PowerShell, WMI, WinRM et SIL (Journalisation de l’inventaire logiciel) qui ont été publiées avec Windows Server 2016. 

WMF 5.1 peut être installé sur Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 et 2012 R2, et fournit plusieurs améliorations par rapport à WMF 5.0 RTM, notamment :

- Nouvelles applets de commande : groupes et utilisateurs locaux ; Get-ComputerInfo
- Améliorations de PowerShellGet avec l’utilisation imposée de modules signés et l’installation de modules JEA
- Ajout de la prise en charge de PackageManagement pour les conteneurs, l’installation de CBS, l’installation basée sur des fichiers .exe et les packages CAB
- Améliorations du débogage pour les classes DSC et PowerShell
- Améliorations de la sécurité, notamment l’utilisation imposée de modules signés par le catalogue provenant du serveur collecteur et lors de l’utilisation des applets de commande PowerShellGet
- Réponses à plusieurs demandes et problèmes des utilisateurs

Pour connaître les nouveautés de cette version, parcourez les rubriques listées sous [Nouveaux scénarios et fonctionnalités](https://docs.microsoft.com/en-us/powershell/wmf/5.1/scenarios-features). 

La rubrique [Installer et configurer](https://docs.microsoft.com/en-us/powershell/wmf/5.1/install-configure) décrit la configuration requise et fournit les instructions d’installation de WMF. 

La rubrique [Compatibilité](https://docs.microsoft.com/en-us/powershell/wmf/5.1/compatibility) liste quelles versions de WMF peuvent être installées sur quelles versions Windows. 

La rubrique [Compatibilité des produits](https://docs.microsoft.com/en-us/powershell/wmf/5.1/productincompat) liste les applications Microsoft qui n’ont pas approuvé WMF 5.1 pour l’instant. 

Les détails des composants de WMF se trouvent dans la documentation MSDN :

- [PowerShell 5.1](https://docs.microsoft.com/en-us/powershell/) 
- [WMI](https://msdn.microsoft.com/en-us/library/jj152383(v=vs.85).aspx)
- [WinRM](https://msdn.microsoft.com/en-us/library/aa384426(v=vs.85).aspx)
- [Journalisation de l’inventaire logiciel](https://technet.microsoft.com/en-us/library/dn383584(v=ws.11).aspx)

