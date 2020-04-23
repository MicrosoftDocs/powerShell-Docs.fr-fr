---
ms.date: 04/19/2019
keywords: wmf,powershell,configuration
title: Windows Management Framework (WMF)
ms.openlocfilehash: d581370fd602e03c86aa549eb8b273ff4d01b4e5
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71147909"
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) fournit une interface de gestion cohérente pour Windows. WMF offre un moyen fluide de gérer différentes versions du client Windows et de Windows Server. Les packages du programme d’installation de WMF contiennent les mises à jour des fonctionnalités de gestion qui sont disponibles pour les anciennes versions de Windows.

L’installation de WMF ajoute ou met à jour les fonctionnalités suivantes :

- Windows PowerShell
- Configuration de l’état souhaité de Windows PowerShell (DSC)
- Windows PowerShell Integrated Script Environment (ISE)
- Windows Remote Management (WinRM)
- Windows Management Instrumentation (WMI)
- Windows PowerShell Web Services (Extension ISS Management OData)
- Journalisation de l’inventaire logiciel
- Fournisseur CIM de Gestionnaire de serveur

## <a name="wmf-release-notes"></a>Notes de publication de WMF

Pour en savoir plus sur les diverses améliorations apportées à PowerShell et d’autres composants d’une version donnée de WMF, consultez les liens ci-dessous pour consulter les notes de publication :

- [WMF 5.1](whats-new/release-notes.md#wmf-51-changes)
- [WMF 5.0](whats-new/release-notes.md#wmf-50-changes)
- [WMF 4.0](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [WMF 3.0](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a>Disponibilité de WMF sur les systèmes d’exploitation Windows

|        Version du système d'exploitation         | [WMF 5.1][]  | WMF 5.0<br>*Hors support* | [WMF 4.0][]  | [WMF 3.0][]  | [WMF 2.0][]  |
| --------------------------------------- | ------------ | --------------------------- | ------------ | ------------ | ------------ |
| Windows Server 2019                     | Fourni par défaut |                             |              |              |              |
| Windows Server 2016                     | Fourni par défaut |                             |              |              |              |
| Windows 10                              | Fourni par défaut | Fourni par défaut                |              |              |              |
| Windows Server 2012 R2                  | Oui          | Oui                         | Fourni par défaut |              |              |
| Windows 8.1                             | Oui          | Oui                         | Fourni par défaut |              |              |
| Windows Server 2012                     | Oui          | Oui                         | Oui          | Fourni par défaut |              |
| Windows 8<br>*Hors support*           |              |                             |              | Fourni par défaut |              |
| Windows Server 2008 R2 SP1              | Oui          | Oui                         | Oui          | Oui          | Fourni par défaut |
| Windows 7 SP1                           | Oui          | Oui                         | Oui          | Oui          | Fourni par défaut |
| Windows Server 2008 SP2                 |              |                             |              | Oui          | Oui          |
| Windows Vista<br>*Hors support*       |              |                             |              |              | Oui          |
| Windows Server 2003<br>*Hors support* |              |                             |              |              | Oui          |
| Windows XP<br>*Hors support*          |              |                             |              | Oui          | Oui          |

- **Fourni par défaut** : les fonctionnalités de la version spécifiée de WMF ont été fournies dans la version indiquée du client Windows ou de Windows Server.
- **Hors support** : ces produits ne sont plus pris en charge par Microsoft. Vous devez effectuer une mise à niveau vers une nouvelle version prise en charge. Pour plus d’informations, consultez la page [Stratégie de cycle de vie Microsoft][].

> [!NOTE]
> Le programme d’installation de WMF 5.0 n’est plus disponible ou pris en charge. Il a été remplacé par WMF 5.1.

[Stratégie de cycle de vie Microsoft]: https://support.microsoft.com/lifecycle
[WMF 5.1]: https://aka.ms/wmf51download
[WMF 4.0]: https://aka.ms/wmf4download
[WMF 3.0]: https://aka.ms/wmf3download
[WMF 2.0]: https://aka.ms/wmf2download
