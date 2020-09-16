---
ms.date: 08/09/2017
keywords: powershell, applet de commande, télécharger, installer, installation, programme d’installation, windows 10, windows 8.1, windows 8.0, windows 7
title: Installation de Windows PowerShell
ms.openlocfilehash: 26675eb0b213818eaa72e148f0814545ee9f960e
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89236218"
---
# <a name="installing-windows-powershell"></a>Installation de Windows PowerShell

Windows PowerShell est installé par défaut avec chaque copie de Windows, à compter de Windows 7 SP1 et de Windows Server 2008 R2 SP1.

Si vous envisagez d’utiliser PowerShell 6 et versions ultérieures, vous devez installer PowerShell Core plutôt que Windows PowerShell. Pour cela, consultez [Installation de PowerShell Core sous Windows](../../install/Installing-PowerShell-Core-on-Windows.md).

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a>Recherche de PowerShell dans Windows 10, 8.1, 8.0 et 7

Il est parfois difficile de localiser la console ou l’environnement d’écriture de scripts intégré (ISE) de PowerShell dans Windows, car ils ne se trouvent pas au même emplacement d’une version de Windows à l’autre.

Les tableaux suivants devraient vous aider à trouver PowerShell dans votre version de Windows. Toutes les versions listées ici sont les versions d’origine telles qu’elles ont été publiées, sans aucune mise à jour.

### <a name="for-console"></a>Pour la console

|     Version      |                                                            Location                                                            |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Windows 10       | Cliquez sur l’icône Windows en bas à gauche et commencez à taper PowerShell                                                                  |
| Windows 8.1, 8.0 | Sur l’écran d’accueil, commencez à taper PowerShell.<br/>Sur un poste de travail, cliquez sur l’icône Windows en bas à gauche et commencez à taper PowerShell |
| Windows 7 SP1    | Cliquez sur l’icône Windows en bas à gauche et commencez à taper PowerShell dans la zone de recherche                                                |

### <a name="for-ise"></a>Pour l’ISE

|     Version      |                                                            Location                                                            |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Windows 10       | Cliquez sur l’icône Windows en bas à gauche et commencez à taper ISE                                                                         |
| Windows 8.1, 8.0 | Sur l’écran d’accueil, tapez **PowerShell ISE**.<br/>Sur un poste de travail, cliquez sur l’icône Windows en bas à gauche et tapez **PowerShell ISE** |
| Windows 7 SP1    | Cliquez sur l’icône Windows en bas à gauche et commencez à taper PowerShell dans la zone de recherche                                                |

## <a name="finding-powershell-in-windows-server-versions"></a>Recherche de PowerShell dans les versions de Windows Server

À compter de Windows Server 2008 R2, le système d’exploitation Windows peut être installé sans l’interface graphique utilisateur (GUI). Les éditions de Windows Server sans GUI sont appelées **Core**, tandis que les éditions avec GUI sont appelées **Desktop**.

### <a name="windows-server-core-editions"></a>Éditions Windows Server Core

Dans toutes les éditions Core, quand vous vous connectez au serveur, vous obtenez une fenêtre d’invite de commandes Windows.

Tapez `powershell` et appuyez sur **Entrée** pour démarrer PowerShell dans la session d’invite de commandes. Tapez `exit` pour mettre fin à la session PowerShell et revenir à l’invite de commandes.

### <a name="windows-server-desktop-editions"></a>Éditions Windows Server Desktop

Dans toutes les éditions Desktop, cliquez sur l’icône Windows en bas à gauche et commencez à taper PowerShell. Vous obtenez à la fois les options de la console et de l’ISE.

La seule exception à cette règle est l’ISE dans Windows Server 2008 R2 SP1 ; dans cette édition, cliquez sur l’icône Windows en bas à gauche et tapez PowerShell ISE.

## <a name="how-to-check-the-version-of-powershell"></a>Comment vérifier la version de PowerShell

Pour trouver la version de PowerShell que vous avez installée, démarrez une console PowerShell (ou l’ISE), puis tapez `$PSVersionTable` et appuyez sur **Entrée**. Recherchez la valeur `PSVersion`.

## <a name="upgrading-existing-windows-powershell"></a>Mise à niveau des instances Windows PowerShell existantes

Le package d’installation de PowerShell se trouve dans un programme d’installation WMF. La version du programme d’installation WMF correspond à la version de PowerShell ; il n’existe aucun programme d’installation autonome de Windows PowerShell.

Si vous devez mettre à jour votre version existante de PowerShell dans Windows, utilisez le tableau suivant pour trouver le programme d’installation de la version de PowerShell que vous souhaitez mettre à jour.

|                    Windows                     |                                  PS 3.0                                   |                                  PS 4.0                                   |                                  PS 5.0                                   |                                  PS 5.1                                   |
| ---------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| Windows 10 (voir Note1)<br/>Windows Server 2016 | -                                                                         | -                                                                         | -                                                                         | installé                                                                 |
| Windows 8.1<br/>Windows Server 2012 R2         | -                                                                         | installé                                                                 | [WMF 5.0](https://www.microsoft.com/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/download/details.aspx?id=54616) |
| Windows 8<br/>Windows Server 2012              | installé                                                                 | [WMF 4.0](https://www.microsoft.com/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/download/details.aspx?id=54616) |
| Windows 7 SP1<br/>Windows Server 2008 R2 SP1   | [WMF 3.0](https://www.microsoft.com/download/details.aspx?id=34595) | [WMF 4.0](https://www.microsoft.com/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/download/details.aspx?id=54616) |

> [!NOTE]
> Dans la version initiale de Windows 10, avec les mises à jour automatiques activées, PowerShell est mis à jour de la version 5.0 à la version 5.1. Si la version originale de Windows 10 n’est pas mise à jour par le biais de Windows Updates, la version de PowerShell est 5.0.

## <a name="need-azure-powershell"></a>Pour Azure PowerShell

Si vous recherchez **Azure PowerShell**, vous pouvez commencer par [Vue d’ensemble d’Azure PowerShell](/powershell/azure/overview).

Sinon, vous voudrez peut-être [Installer et configurer Azure PowerShell](/powershell/azure/install-az-ps)

## <a name="see-also"></a>Voir aussi

[Configuration nécessaire pour Windows PowerShell](Windows-PowerShell-System-Requirements.md)

[Démarrage de Windows PowerShell](../Starting-Windows-PowerShell.md)
