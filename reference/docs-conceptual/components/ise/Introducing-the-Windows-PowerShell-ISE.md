---
ms.date: 08/14/2018
keywords: powershell,applet de commande
title: Présentation de Windows PowerShell ISE
ms.openlocfilehash: 09a28b295855fd2a3c62bba8a681399dae3454f8
ms.sourcegitcommit: 3402a478cf118c11a5642038eb117bc76553e3ab
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53411580"
---
# <a name="the-windows-powershell-ise"></a>Windows PowerShell ISE

Windows PowerShell Integrated Scripting Environment (ISE) est une application hôte pour Windows PowerShell. Dans l’environnement ISE, vous pouvez exécuter des commandes et écrire, tester et déboguer des scripts dans une interface utilisateur graphique Windows unique. L’environnement ISE fournit édition multiligne, saisie semi-automatique par tabulation, la coloration syntaxique, l’exécution sélective, l’aide contextuelle et prise en charge pour les langues de droite à gauche. Les éléments de menu et les raccourcis clavier sont mappés une grande partie des tâches accessibles à partir de la console Windows PowerShell. Par exemple, lorsque vous déboguez un script dans l’environnement ISE, vous pouvez avec le bouton droit sur une ligne de code dans le volet d’édition pour définir un point d’arrêt.

## <a name="support"></a>Assistance

L’environnement ISE a été introduite avec Windows PowerShell V2 et a été remodelée avec PowerShell V3. L’environnement ISE est pris en charge dans toutes les versions prises en charge de PowerShell Windows jusqu'à et y compris Windows PowerShell version 5.1. L’environnement ISE, cependant, est en mode de maintennce et aucuns nouvelles fonctionnalités ne sont susceptibles d’être ajouté.
En outre, il n’existe aucune prise en charge pour l’environnement ISE avec PowerShell v6 et au-delà. Tenez compte des utilisateurs souhaitant un outil graphique permettant de gérer scrips de PowerShell, etc., [Visual Studio Code](https://code.visualstudio.com/).

## <a name="key-features"></a>Principales fonctionnalités

Les fonctionnalités clées de Windows PowerShell ISE :

- Édition multiligne : Pour insérer une ligne vide sous la ligne actuelle dans le volet de commandes, appuyez sur Maj+Entrée.
- Exécution sélective : Pour exécuter une partie d’un script, sélectionnez le texte à exécuter, puis cliquez sur le bouton **Exécuter le script**. Ou bien, appuyez sur F5.
- Aide contextuelle : Saisissez **Invoke-Item**, puis appuyez sur F1. Le fichier d’aide s’ouvre à l’article de la cmdlet **Invoke-Item**.

Windows PowerShell ISE permet de personnaliser certains aspects de son apparence. Il possède également son propre script de profil Windows PowerShell.

## <a name="to-start-the-windows-powershell-ise"></a>Pour démarrer Windows PowerShell ISE

Cliquez sur **Démarrer**, sélectionnez **Windows PowerShell**, puis cliquez sur **Windows PowerShell ISE**.
Vous pouvez aussi taper `powershell_ise.exe` dans n’importe quel interpréteur de commandes ou dans la zone Exécuter.

## <a name="to-get-help-in-the-windows-powershell-ise"></a>Pour obtenir de l'aide dans Windows PowerShell ISE

Dans le menu **Aide**, cliquez sur **Aide Windows PowerShell**. Ou bien, appuyez sur F1. Le fichier qui s'ouvre décrit Windows PowerShell ISE et Windows PowerShell. Il comprend aussi l'intégralité de l'aide disponible à partir de l'applet de commande Get-Help.
