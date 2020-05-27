---
ms.date: 08/14/2018
keywords: powershell,applet de commande
title: Présentation de Windows PowerShell ISE
ms.openlocfilehash: 3e4471d0982ba4d7ef1a9d59906a9ff297f6f7cb
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808715"
---
# <a name="the-windows-powershell-ise"></a>Windows PowerShell ISE

Windows PowerShell Integrated Scripting Environment (ISE) est une application hôte pour Windows PowerShell. Dans ISE, vous pouvez exécuter des commandes et écrire, tester et déboguer des scripts dans une seule interface utilisateur graphique Windows. ISE fournit l’édition multiligne, la saisie semi-automatique par tabulation, la coloration syntaxique, l’exécution sélective, l’aide contextuelle et la prise en charge pour les langues s’écrivant de droite à gauche. Les éléments de menu et les raccourcis clavier sont mappés une grande partie des tâches accessibles à partir de la console Windows PowerShell. Par exemple, lorsque vous déboguez un script dans ISE, vous pouvez cliquer avec le bouton droit sur une ligne de code dans le panneau de modification pour définir un point d’arrêt.

## <a name="support"></a>Support

ISE a été inauguré avec Windows PowerShell V2 et a été remodelé avec PowerShell V3. ISE est pris en charge dans toutes les versions prises en charge de PowerShell Windows jusqu’à et y compris Windows PowerShell V5.1.

> [!NOTE]
> L’environnement ISE PowerShell ne fait plus partie du développement de fonctionnalités actif. En tant que composant d’expédition de Windows, il continue d’être officiellement pris en charge pour la sécurité et les correctifs de maintenance de haute priorité.
> Nous n’avons actuellement aucun projet de supprimer l’environnement ISE de Windows.
>
> Il n’existe aucune prise en charge pour l’environnement ISE dans PowerShell v6 et versions ultérieures. Les utilisateurs cherchant à remplacer l’environnement ISE doivent utiliser [Visual Studio Code](https://code.visualstudio.com/) avec [l’extension PowerShell](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell).

## <a name="key-features"></a>Principales fonctionnalités

Les fonctionnalités clés dans Windows PowerShell ISE incluent :

- Édition multiligne : pour insérer une ligne vide sous la ligne actuelle dans le volet de commandes, appuyez sur <kbd>Maj</kbd>+<kbd>Entrée</kbd>.
- Exécution sélective : Pour exécuter une partie d’un script, sélectionnez le texte à exécuter, puis cliquez sur le bouton **Exécuter le script**. Ou bien, appuyez sur <kbd>F5</kbd>.
- Aide contextuelle : Tapez `Invoke-Item` puis appuyez sur <kbd>F1</kbd>. Le fichier d’aide s’ouvre à l’article de la cmdlet `Invoke-Item`.

Windows PowerShell ISE permet de personnaliser certains aspects de son apparence. Il possède également son propre script de profil Windows PowerShell.

## <a name="to-start-the-windows-powershell-ise"></a>Pour démarrer Windows PowerShell ISE

Cliquez sur **Démarrer**, sélectionnez **Windows PowerShell**, puis cliquez sur **Windows PowerShell ISE**.
Vous pouvez aussi taper `powershell_ise.exe` dans n’importe quel interpréteur de commandes ou dans la zone Exécuter.

## <a name="to-get-help-in-the-windows-powershell-ise"></a>Pour obtenir de l'aide dans Windows PowerShell ISE

Dans le menu **Aide**, cliquez sur **Aide Windows PowerShell**. Ou appuyez sur <kbd>F1</kbd>. Le fichier qui s’ouvre décrit Windows PowerShell ISE et Windows PowerShell. Il comprend aussi l’intégralité de l’aide disponible à partir de la cmdlet `Get-Help`.
