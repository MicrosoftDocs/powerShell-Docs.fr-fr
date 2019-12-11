---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Comment créer un onglet PowerShell dans Windows PowerShell ISE
ms.openlocfilehash: 7baf9a4051a196045d53eebf8ce5260bdc1bc55a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030587"
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a>Comment créer un onglet PowerShell dans Windows PowerShell ISE

Les onglets de l’environnement d’écriture de scripts intégré de Windows PowerShell permettent de créer et d’utiliser simultanément plusieurs environnements d’exécution au sein de la même application.
Chaque onglet PowerShell correspond à un environnement d’exécution ou à une session distincts.

> [!NOTE]
> Les variables, fonctions et alias que vous créez sous un onglet ne s’appliquent pas à un autre. Il s’agit de sessions Windows PowerShell différentes.

Pour ouvrir ou fermer un onglet dans Windows PowerShell, procédez comme suit.
Pour renommer un onglet, définissez la propriété [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) sur l’objet de script Onglet Windows PowerShell.

## <a name="to-create-and-use-a-new-powershell-tab"></a>Pour créer et utiliser un onglet PowerShell

Dans le menu **Fichier**, cliquez sur **Nouvel onglet PowerShell**. Le nouvel onglet PowerShell s’ouvre toujours comme la fenêtre active.
Les onglets PowerShell sont numérotés de façon incrémentielle dans l’ordre de leur ouverture.
Chaque onglet est associé à sa propre fenêtre de console Windows PowerShell.
Vous pouvez avoir jusqu’à 32 onglets PowerShell avec leur propre session ouverte simultanément (ce nombre est limité à 8 sur Windows PowerShell ISE 2.0.)

Notez qu’un clic sur l’icône **Nouveau** ou **Ouvrir** dans la barre d’outils ne crée pas d’onglet avec une session distincte.
Au lieu de cela, ces boutons ouvrent un fichier de script nouveau ou existant sur l’onglet actif avec une session.
Vous pouvez avoir plusieurs fichiers script ouverts avec chaque onglet et session.
Les onglets de script pour une session s’affichent sous les onglets de la session uniquement lorsque la session associée est active.

Pour activer un onglet PowerShell, cliquez dessus. Pour opérer une sélection parmi tous les onglets PowerShell ouverts, dans le menu **Affichage**, cliquez sur l’onglet PowerShell que vous souhaitez utiliser.

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a>Pour créer et utiliser un onglet PowerShell à distance

Dans le menu **Fichier**, cliquez sur **Nouvel onglet PowerShell à distance** pour établir une session sur un ordinateur distant.
Une boîte de dialogue s’affiche et vous invite à entrer les détails requis pour établir la connexion à distance.
L’onglet à distance fonctionne exactement comme un onglet PowerShell local, mais les commandes et les scripts sont exécutés sur l’ordinateur distant.

## <a name="to-close-a-powershell-tab"></a>Pour fermer un onglet PowerShell

Pour fermer un onglet, vous pouvez utiliser l’une des techniques suivantes :

- Cliquez sur l’onglet que vous souhaitez fermer.

- Dans le menu **Fichier**, cliquez sur **Fermer l’onglet PowerShell** ou sur le bouton Fermer (**X**) d’un onglet actif pour fermer celui-ci.

Si des fichiers non enregistrés sont ouverts dans l’onglet PowerShell que vous fermez, vous êtes invité à les enregistrer ou les ignorer.
Pour plus d’informations sur l’enregistrement d’un script, voir [Comment enregistrer un script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).

## <a name="see-also"></a>Voir aussi

- [Présentation de Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
- [Comment utiliser le volet Console dans Windows PowerShell ISE](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)
