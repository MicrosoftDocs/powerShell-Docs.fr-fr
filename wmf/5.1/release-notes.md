---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,configuration
title: Notes de publication de WMF 5.1
ms.openlocfilehash: 61ca854cf8f26a9e96c6c5b5c06f6b54d08fb4ea
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795009"
---
# <a name="windows-management-framework-wmf-51-release-notes"></a>Notes de publication de Windows Management Framework (WMF) 5.1

WMF 5.1 comprend les composants PowerShell, WMI, WinRM et SIL (Journalisation de l’inventaire logiciel) qui ont été publiés avec Windows Server 2016.
WMF 5.1 peut être installé sur Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 et 2012 R2, et fournit plusieurs améliorations par rapport à WMF 5.0 RTM, notamment :

- Nouvelles applets de commande : groupes et utilisateurs locaux ; Get-ComputerInfo
- Améliorations de PowerShellGet avec l’utilisation imposée de modules signés et l’installation de modules JEA
- Ajout de la prise en charge de PackageManagement pour les conteneurs, l’installation de CBS, l’installation basée sur des fichiers .exe et les packages CAB
- Améliorations du débogage pour les classes DSC et PowerShell
- Améliorations de la sécurité, notamment l’utilisation imposée de modules signés par le catalogue provenant du serveur collecteur et lors de l’utilisation des applets de commande PowerShellGet
- Réponses à plusieurs demandes et problèmes des utilisateurs

**Remarques importantes :**

- **WMF 5.1 nécessite le .NET Framework 4.5.2** (ou ultérieur). L’installation réussit, mais des fonctionnalités clés échouent si le .NET Framework 4.5.2 (ou ultérieur) n’est pas installé. Des instructions sont disponibles dans la rubrique [Installer et configurer WMF 5.1](https://msdn.microsoft.com/powershell/wmf/5.1/install-configure).
- La préversion de WMF 5.1 doit être désinstallée avant d’installer la version WMF 5.1 RTM.
- WMF 5.1 peut être installé directement sur WMF 5.0 ou WMF 4.0.
- Il n’est __pas nécessaire__ d’installer WMF 4.0 avant d’installer WMF 5.1 sur Windows 7 et Windows Server 2008 R2. C’était un problème lié à version 5.1 WMF qui a été résolu.
