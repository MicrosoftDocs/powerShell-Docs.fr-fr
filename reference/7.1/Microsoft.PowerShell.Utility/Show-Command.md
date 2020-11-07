---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/29/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/show-command?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-Command
ms.openlocfilehash: b5758fdb9fc3e8f604b24fb9c64cad3f95047ec3
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347769"
---
# Show-Command

## SYNOPSIS
Affiche des informations de commande PowerShell dans une fenêtre graphique.

## SYNTAXE

```
Show-Command [[-Name] <String>] [-Height <Double>] [-Width <Double>] [-NoCommonParameter]
 [-ErrorPopup] [-PassThru] [<CommonParameters>]
```

## DESCRIPTION

L' `Show-Command` applet de commande vous permet de créer une commande PowerShell dans une fenêtre de commande. Vous pouvez utiliser les fonctionnalités de la fenêtre de commandes pour qu'elle exécute la commande, ou pour qu'elle vous la retourne.

`Show-Command` est un outil d’apprentissage et d’apprentissage très utile. `Show-Command` fonctionne sur tous les types de commandes, y compris les applets de commande, les fonctions, les flux de travail et les commandes CIM.

Sans paramètres, `Show-Command` affiche une fenêtre de commande qui répertorie toutes les commandes disponibles dans tous les modules installés. Pour trouver les commandes d'un module, sélectionnez le module dans la liste déroulante Modules. Pour sélectionner une commande, cliquez sur son nom.

Pour utiliser la fenêtre commande, sélectionnez une commande, en utilisant le nom ou en cliquant sur le nom de la commande dans la liste **commandes** . Chaque jeu de paramètres s’affiche sous un onglet distinct. Les astérisques indiquent les paramètres obligatoires. Pour entrer des valeurs pour un paramètre, tapez la valeur dans la zone de texte ou sélectionnez la valeur dans la zone de liste déroulante. Pour ajouter un paramètre de commutateur, cliquez et cochez la case du paramètre.

Quand vous êtes prêt, cliquez sur **Copy** pour copier la commande que vous avez créée dans le Presse-papiers, ou cliquez sur **Run** pour exécuter la commande. Vous pouvez également utiliser le paramètre **PassThru** pour retourner la commande au programme hôte, tel que la console PowerShell. Pour annuler la sélection de la commande et revenir à la vue qui affiche toutes les commandes, appuyez sur Ctrl et cliquez sur la commande sélectionnée.

Dans l’environnement d’écriture de scripts intégré (ISE) de PowerShell, une variante de la `Show-Command` fenêtre s’affiche par défaut. Pour plus d’informations sur l’utilisation de cette fenêtre de commande, consultez les rubriques d’aide de PowerShell ISE.

Cette applet de commande a été réintroduite dans PowerShell 7.

Étant donné que cette applet de commande nécessite une interface utilisateur, elle ne fonctionne pas sur Windows Server Core ou Windows nano Server. Cette applet de commande est uniquement disponible sur les systèmes Windows qui prennent en charge le bureau Windows.

## EXEMPLES

### Exemple 1 : ouvrir la fenêtre commandes

Cet exemple affiche la vue par défaut de la `Show-Command` fenêtre. La fenêtre **commandes** affiche une liste de toutes les commandes de tous les modules installés sur l’ordinateur.

```powershell
Show-Command
```

### Exemple 2 : ouvrir une applet de commande dans la fenêtre commandes

Cet exemple affiche l' `Invoke-Command` applet de commande dans la fenêtre **commande** . Vous pouvez utiliser cet affichage pour exécuter des `Invoke-Command` commandes.

```powershell
Show-Command -Name "Invoke-Command"
```

### Exemple 3 : ouvrir une applet de commande avec les paramètres spécifiés

Cette commande ouvre une `Show-Command` fenêtre pour l' `Connect-PSSession` applet de commande.

```powershell
Show-Command -Name "Connect-PSSession" -Height 700 -Width 1000 -ErrorPopup
```

Les paramètres de **hauteur** et de **largeur** spécifient la dimension de la fenêtre de commande. Le paramètre **ErrorPopup** affiche la fenêtre d’erreur de la commande.

Lorsque vous cliquez sur **exécuter** , la `Connect-PSSession` commande s’exécute, comme si vous tapiiez la `Connect-PSSession` commande sur la ligne de commande.

### Exemple 4 : spécifier les nouvelles valeurs de paramètre par défaut pour une applet de commande

Cet exemple utilise la `$PSDefaultParameterValues` variable Automatic pour définir de nouvelles valeurs par défaut pour les paramètres de **hauteur** , de **largeur** et de **ErrorPopup** de l’applet de commande `Show-Command` .

```powershell
$PSDefaultParameterValues = @{
    "Show-Command:Height" = 700
    "Show-Command:Width" = 1000
    "Show-Command:ErrorPopup" = $True
}
```

Désormais, lorsque vous exécutez une `Show-Command` commande, les nouvelles valeurs par défaut sont appliquées automatiquement. Pour utiliser ces valeurs par défaut dans chaque session PowerShell, ajoutez la `$PSDefaultParameterValues` variable à votre profil PowerShell. Pour plus d’informations, consultez [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md) et [about_Parameters_Default_Values](../Microsoft.PowerShell.Core/About/about_Parameters_Default_Values.md).

### Exemple 5 : envoyer une sortie vers une vue grille

Cette commande montre comment utiliser les `Show-Command` `Out-GridView` cmdlets et ensemble.

```powershell
Show-Command Get-ChildItem | Out-GridView
```

La commande utilise l' `Show-Command` applet de commande pour ouvrir une fenêtre de commande pour l’applet de commande `Get-ChildItem` .
Lorsque vous cliquez sur le bouton **exécuter** , la `Get-ChildItem` commande s’exécute et génère une sortie. L’opérateur de pipeline (|) envoie la sortie de la `Get-ChildItem` commande à l’applet de commande `Out-GridView` , qui affiche la `Get-ChildItem` sortie dans une fenêtre interactive.

### Exemple 6 : afficher une commande que vous créez dans la fenêtre commandes

Cet exemple montre la commande que vous avez créée dans la `Show-Command` fenêtre. La commande utilise le paramètre **PassThru** , qui retourne les `Show-Command` résultats dans une chaîne.

```powershell
Show-Command -PassThru
```

```Output
Get-EventLog -LogName "Windows PowerShell" -Newest 5
```

Par exemple, si vous utilisez la `Show-Command` fenêtre pour créer une `Get-EventLog` commande qui obtient les cinq événements les plus récents dans le journal des événements Windows PowerShell, puis cliquez sur **OK** , la commande renvoie la sortie indiquée ci-dessus. L’affichage de la chaîne de commande vous aide à découvrir PowerShell.

### Exemple 7 : enregistrer une commande dans une variable

Cet exemple montre comment exécuter la chaîne de commande que vous recevez quand vous utilisez le paramètre **PassThru** de l' `Show-Command` applet de commande. Cette stratégie vous permet de voir la commande et de l'utiliser.

```powershell
$C = Show-Command -PassThru
$C
Invoke-Expression $C
```

```Output
Get-EventLog -LogName "PowerShell" -Newest 5

Index Time          EntryType   Source                 InstanceID Message
----- ----          ---------   ------                 ---------- -------
11520 Dec 16 16:37  Information Windows PowerShell            400 Engine state is changed from None to Available...
11519 Dec 16 16:37  Information Windows PowerShell            600 Provider "Variable" is Started. ...
11518 Dec 16 16:37  Information Windows PowerShell            600 Provider "Registry" is Started. ...
11517 Dec 16 16:37  Information Windows PowerShell            600 Provider "Function" is Started. ...
11516 Dec 16 16:37  Information Windows PowerShell            600 Provider "FileSystem" is Started. ...
```

La première commande utilise le paramètre **PassThru** de l' `Show-Command` applet de commande et enregistre les résultats de la commande dans la `$C` variable. Dans ce cas, nous utilisons la `Show-Command` fenêtre pour créer une `Get-EventLog` commande qui obtient les cinq événements les plus récents dans le journal des événements Windows PowerShell. Lorsque vous cliquez sur **OK** , `Show-Command` retourne la chaîne de commande, qui est enregistrée dans la `$C` variable.

### Exemple 8 : enregistrer la sortie d’une commande dans une variable

Cet exemple utilise le paramètre **ErrorPopup** pour enregistrer la sortie d’une commande dans une variable.

```powershell
$P = Show-Command Get-Process -ErrorPopup
$P
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    473      33    94096     112532   709     2.06   4492 powershell
```

Outre l'affichage des erreurs dans une fenêtre, **ErrorPopup** retourne la sortie de commande dans la commande actuelle, au lieu de créer une commande. Lorsque vous exécutez cette commande, la `Show-Command` fenêtre s’ouvre. Vous pouvez utiliser les fonctionnalités de la fenêtre pour définir les valeurs de paramètre. Pour exécuter la commande, cliquez sur le bouton **exécuter** dans la `Show-Command` fenêtre.

## PARAMÈTRES

### -ErrorPopup

Indique que l’applet de commande affiche les erreurs dans une fenêtre indépendante, en plus de les afficher sur la ligne de commande. Par défaut, lorsqu’une commande exécutée dans une `Show-Command` fenêtre génère une erreur, l’erreur s’affiche uniquement sur la ligne de commande.

En outre, lorsque vous exécutez la commande (à l’aide du bouton **exécuter** dans la `Show-Command` fenêtre), le paramètre **ErrorPopup** retourne les résultats de la commande à la commande actuelle, au lieu d’exécuter la commande et de retourner sa sortie à une nouvelle commande. Vous pouvez utiliser cette fonctionnalité pour enregistrer les résultats de la commande dans une variable.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Hauteur

Spécifie la hauteur de la `Show-Command` fenêtre en pixels. Entrez une valeur comprise entre 300 et le nombre de pixels de la résolution d'écran. Si la valeur est trop grande pour afficher la fenêtre commande à l’écran, `Show-Command` génère une erreur. La hauteur par défaut est de 600 pixels. Pour une `Show-Command` commande qui comprend le paramètre **Name** , la hauteur par défaut est de 300 pixels.

```yaml
Type: System.Double
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Affiche une fenêtre de commandes pour la commande spécifiée. Entrez le nom d’une commande, par exemple le nom d’une applet de commande, d’une fonction ou d’une commande CIM. Si vous omettez ce paramètre, `Show-Command` affiche une fenêtre de commande qui répertorie toutes les commandes PowerShell de tous les modules installés sur l’ordinateur.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CommandName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoCommonParameter

Indique que cette applet de commande omet la section paramètres communs de l’affichage de la commande. Par défaut, les paramètres communs apparaissent dans une section extensible en bas de la fenêtre de commandes.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

Retourne un objet représentant l’élément que vous utilisez. Par défaut, cette applet de commande ne génère aucun résultat. Pour exécuter la chaîne de commande, copiez et collez-la à l’invite de commandes, ou enregistrez-la dans une variable et utilisez l' `Invoke-Expression` applet de commande pour exécuter la chaîne dans la variable.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Largeur

Spécifie la largeur de la `Show-Command` fenêtre en pixels. Entrez une valeur comprise entre 300 et le nombre de pixels de la résolution d'écran. Si la valeur est trop grande pour afficher la fenêtre commande à l’écran, `Show-Command` génère une erreur. La largeur par défaut est de 300 pixels.

```yaml
Type: System.Double
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d’entrée vers `Show-Command` .

## SORTIES

### None, System. String, System. Object

Quand vous utilisez le paramètre **PassThru** , `Show-Command` retourne une chaîne de commande. Quand vous utilisez le paramètre **ErrorPopup** , `Show-Command` retourne la sortie de commande (n’importe quel objet). Dans le cas contraire, `Show-Command` ne génère pas de sortie.

## REMARQUES

Cette applet de commande est disponible uniquement sur les plateformes Windows.

`Show-Command` ne fonctionne pas dans les sessions à distance.

## LIENS CONNEXES
