---
ms.date: 08/14/2018
keywords: powershell,applet de commande
title: Présentation de Windows PowerShell ISE
ms.openlocfilehash: 729c8535dbcfcd2c51070b8beac5d328375f36ae
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057414"
---
# <a name="the-windows-powershell-ise"></a>Windows PowerShell ISE

Windows PowerShell Integrated Scripting Environment (ISE) est une application hôte pour Windows PowerShell. Dans ISE, vous pouvez exécuter des commandes et écrire, tester et déboguer des scripts dans une seule interface utilisateur graphique Windows. ISE fournit l’édition multiligne, la saisie semi-automatique par tabulation, la coloration syntaxique, l’exécution sélective, l’aide contextuelle et la prise en charge pour les langues s’écrivant de droite à gauche. Les éléments de menu et les raccourcis clavier sont mappés une grande partie des tâches accessibles à partir de la console Windows PowerShell. Par exemple, lorsque vous déboguez un script dans ISE, vous pouvez cliquer avec le bouton droit sur une ligne de code dans le panneau de modification pour définir un point d’arrêt.

## <a name="support"></a>Assistance

ISE a été inauguré avec Windows PowerShell V2 et a été remodelé avec PowerShell V3. ISE est pris en charge dans toutes les versions prises en charge de PowerShell Windows jusqu’à et y compris Windows PowerShell V5.1. Cependant, ISE est en mode maintenance et aucune nouvelle fonctionnalité ne devrait y être ajoutée.
En outre, il n’existe aucune prise en charge pour ISE avec PowerShell v6 et versions ultérieures. Les utilisateurs qui recherchent un outil graphique permettant de gérer des scripts PowerShell, entre autres, devraient se tourner vers [Visual Studio Code](https://code.visualstudio.com/).

## <a name="key-features"></a>Principales fonctionnalités

Les fonctionnalités clés dans Windows PowerShell ISE incluent :

- Édition multiligne : pour insérer une ligne vide sous la ligne actuelle dans le volet de commandes, appuyez sur Maj+Entrée.
- Exécution sélective : Pour exécuter une partie d’un script, sélectionnez le texte à exécuter, puis cliquez sur le bouton **Exécuter le script**. Ou bien, appuyez sur F5.
- Aide contextuelle : Saisissez **Invoke-Item**, puis appuyez sur F1. Le fichier d’aide s’ouvre à l’article de la cmdlet **Invoke-Item**.

Windows PowerShell ISE permet de personnaliser certains aspects de son apparence. Il possède également son propre script de profil Windows PowerShell.

## <a name="to-start-the-windows-powershell-ise"></a>Pour démarrer Windows PowerShell ISE

Cliquez sur **Démarrer**, sélectionnez **Windows PowerShell**, puis cliquez sur **Windows PowerShell ISE**.
Vous pouvez aussi taper `powershell_ise.exe` dans n’importe quel interpréteur de commandes ou dans la zone Exécuter.

## <a name="to-get-help-in-the-windows-powershell-ise"></a>Pour obtenir de l'aide dans Windows PowerShell ISE

Dans le menu **Aide**, cliquez sur **Aide Windows PowerShell**. Ou bien, appuyez sur F1. Le fichier qui s'ouvre décrit Windows PowerShell ISE et Windows PowerShell. Il comprend aussi l'intégralité de l'aide disponible à partir de l'applet de commande Get-Help.
