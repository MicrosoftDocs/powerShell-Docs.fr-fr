---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSReadLine
ms.date: 06/30/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlineoption?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineOption
ms.openlocfilehash: ce5941787120988a3352153497c9a6df06ee9d89
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208810"
---
# Set-PSReadLineOption

## Synopsis
Personnalise le comportement de la modification de la ligne de commande dans **PSReadLine**.

## Syntaxe

```
Set-PSReadLineOption [-EditMode <EditMode>] [-ContinuationPrompt <String>] [-HistoryNoDuplicates]
 [-AddToHistoryHandler <System.Func[System.String,System.Object]>]
 [-CommandValidationHandler <System.Action[System.Management.Automation.Language.CommandAst]>]
 [-HistorySearchCursorMovesToEnd] [-MaximumHistoryCount <Int32>] [-MaximumKillRingCount <Int32>]
 [-ShowToolTips] [-ExtraPromptLineCount <Int32>] [-DingTone <Int32>] [-DingDuration <Int32>]
 [-BellStyle <BellStyle>] [-CompletionQueryItems <Int32>] [-WordDelimiters <String>]
 [-HistorySearchCaseSensitive] [-HistorySaveStyle <HistorySaveStyle>] [-HistorySavePath <String>]
 [-AnsiEscapeTimeout <Int32>] [-PromptText <String[]>] [-ViModeIndicator <ViModeStyle>]
 [-ViModeChangeHandler <ScriptBlock>] [-Colors <Hashtable>] [<CommonParameters>]
```

## Description

L' `Set-PSReadLineOption` applet de commande personnalise le comportement du module **PSReadLine** lors de la modification de la ligne de commande. Pour afficher les paramètres **PSReadLine** , utilisez `Get-PSReadLineOption` .

## Exemples

### Exemple 1 : définir les couleurs de premier plan et d’arrière-plan

Cet exemple définit **PSReadLine** pour afficher le jeton de **Commentaire** avec le texte de premier plan vert sur un arrière-plan gris. Dans la séquence d’échappement utilisée dans l’exemple, **32** représente la couleur de premier plan et **47** représente la couleur d’arrière-plan.

```powershell
Set-PSReadLineOption -Colors @{ "Comment"="`e[32;47m" }
```

Vous pouvez choisir de définir uniquement une couleur de texte de premier plan. Par exemple, une couleur de texte de premier plan vert clair pour le jeton de **Commentaire** : ``"Comment"="`e[92m"`` .

### Exemple 2 : définir le style de cloche

Dans cet exemple, **PSReadLine** répond aux erreurs ou conditions qui requièrent l’attention de l’utilisateur.
Le **BellStyle** est défini pour émettre un signal sonore à 1221 Hz pour 60 ms.

```powershell
Set-PSReadLineOption -BellStyle Audible -DingTone 1221 -DingDuration 60
```

> [!NOTE]
> Cette fonctionnalité peut ne pas fonctionner sur tous les ordinateurs hôtes sur les plateformes.

### Exemple 3 : définir plusieurs options

`Set-PSReadLineOption` peut définir plusieurs options avec une table de hachage.

```powershell
$PSReadLineOptions = @{
    EditMode = "Emacs"
    HistoryNoDuplicates = $true
    HistorySearchCursorMovesToEnd = $true
    Colors = @{
        "Command" = "#8181f7"
    }
}
Set-PSReadLineOption @PSReadLineOptions
```

La `$PSReadLineOptions` table de hachage définit les clés et les valeurs. `Set-PSReadLineOption` utilise les clés et les valeurs de `@PSReadLineOptions` pour mettre à jour les options **PSReadLine** .

Vous pouvez afficher les clés et les valeurs en entrant le nom de la table `$PSReadLineOptions` de hachage dans la ligne de commande PowerShell.

### Exemple 4 : définir plusieurs options de couleur

Cet exemple montre comment définir plusieurs valeurs de couleur dans une même commande.

```powershell
Set-PSReadLineOption -Colors @{
  Command            = 'Magenta'
  Number             = 'DarkGray'
  Member             = 'DarkGray'
  Operator           = 'DarkGray'
  Type               = 'DarkGray'
  Variable           = 'DarkGreen'
  Parameter          = 'DarkGreen'
  ContinuationPrompt = 'DarkGray'
  Default            = 'DarkGray'
}
```

### Exemple 5 : définir des valeurs de couleur pour plusieurs types

Cet exemple montre trois méthodes différentes pour définir la couleur des jetons affichés dans **PSReadLine**.

```powershell
Set-PSReadLineOption -Colors @{
 # Use a ConsoleColor enum
 "Error" = [ConsoleColor]::DarkRed

 # 24 bit color escape sequence
 "String" = "$([char]0x1b)[38;5;100m"

 # RGB value
 "Command" = "#8181f7"
}
```

### Exemple 6 : utilisation de ViModeChangeHandler pour afficher les modifications du mode VI

Cet exemple émet un changement de curseur à l’échappement VT en réponse à une modification du mode **VI** .

```powershell
function OnViModeChange {
    if ($args[0] -eq 'Command') {
        # Set the cursor to a blinking block.
        Write-Host -NoNewLine "`e[1 q"
    } else {
        # Set the cursor to a blinking line.
        Write-Host -NoNewLine "`e[5 q"
    }
}
Set-PSReadLineOption -ViModeIndicator Script -ViModeChangeHandler $Function:OnViModeChange
```

La fonction **OnViModeChange** définit les options de curseur pour les modes **VI** : Insert et Command.
**ViModeChangeHandler** utilise le `Function:` fournisseur pour faire référence à **OnViModeChange** en tant qu’objet de bloc de script.

Pour plus d'informations, consultez [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).

## Paramètres

### -AddToHistoryHandler

Spécifie un **scriptblock** qui contrôle les commandes qui sont ajoutées à l’historique **PSReadLine** .

Le **scriptblock** reçoit la ligne de commande comme entrée. Si le **scriptblock** retourne `$True` , la ligne de commande est ajoutée à l’historique.

```yaml
Type: System.Func`2[System.String,System.Object]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AnsiEscapeTimeout

Cette option est spécifique à Windows lorsque l’entrée est redirigée, par exemple, en cas d’exécution sous `tmux` ou `screen` .

Avec l’entrée redirigée sur Windows, de nombreuses clés sont envoyées sous la forme d’une séquence de caractères commençant par le caractère d’échappement. Il est impossible de faire la distinction entre un caractère d’échappement unique suivi d’un plus grand nombre de caractères et d’une séquence d’échappement valide.

L’hypothèse est que le terminal peut envoyer les caractères plus rapidement qu’un utilisateur. **PSReadLine** attend ce délai d’attente avant de conclure qu’il a reçu une séquence d’échappement complète.

Si vous voyez des caractères aléatoires ou inattendus lorsque vous tapez, vous pouvez ajuster ce délai d’attente.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### -BellStyle

Spécifie comment **PSReadLine** répond à différentes erreurs et conditions ambiguës.

Les valeurs valides sont les suivantes :

- **Audible** : un bref signal sonore.
- **Visuel** : le texte clignote brièvement.
- **Aucun** : aucun commentaire.

```yaml
Type: Microsoft.PowerShell.BellStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Audible
Accept pipeline input: False
Accept wildcard characters: False
```

### -Couleurs

Le paramètre **couleurs** spécifie différentes couleurs utilisées par **PSReadLine**.

L’argument est une table de hachage dans laquelle les clés spécifient l’élément et les valeurs spécifient la couleur.
Pour plus d’informations, consultez [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).

Les couleurs peuvent être une valeur de **ConsoleColor** , par exemple `[ConsoleColor]::Red` , ou une séquence d’échappement ANSI valide. Les séquences d’échappement valides dépendent de votre terminal. Dans PowerShell 5,0, un exemple de séquence d’échappement pour le texte en rouge est `$([char]0x1b)[91m` . Dans PowerShell 6 et versions ultérieures, la même séquence d’échappement est `` `e[91m`` . Vous pouvez spécifier d’autres séquences d’échappement, y compris les types suivants :

- 256 couleur
- couleur 24 bits
- Premier plan, arrière-plan ou les deux
- Inverse, gras

Pour plus d’informations sur les codes de couleur ANSI, consultez [Code ANSI Escape](https://wikipedia.org/wiki/ANSI_escape_code#Colors_) dans Wikipédia.

Les clés valides sont les suivantes :

- **ContinuationPrompt** : couleur de l’invite de continuation.
- **Accent** : couleur d’accentuation. Par exemple, le texte correspondant lors de la recherche de l’historique.
- **Erreur** : couleur de l’erreur. Par exemple, dans l’invite de commandes.
- **Sélection** : couleur pour mettre en surbrillance la sélection de menu ou le texte sélectionné.
- **Default** : couleur de jeton par défaut.
- **Comment** : couleur de jeton de commentaire.
- **Mot clé** : la couleur du jeton de mot clé.
- **Chaîne** : la couleur du jeton de chaîne.
- **Opérateur** : couleur de jeton de l’opérateur.
- **Variable** : couleur du jeton de la variable.
- **Commande** : couleur du jeton de commande.
- **Paramètre** : couleur du jeton du paramètre.
- **Type** : la couleur du jeton de type.
- **Number** : la couleur du jeton numérique.
- **Membre** : la couleur du jeton de nom de membre.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CommandValidationHandler

Spécifie un **scriptblock** qui est appelé à partir de **ValidateAndAcceptLine**. Si une exception est levée, la validation échoue et l’erreur est signalée.

Avant de lever une exception, le gestionnaire de validation peut placer le curseur au point de l’erreur pour faciliter la résolution. Un gestionnaire de validation peut également modifier la ligne de commande, par exemple pour corriger les erreurs typographiques courantes.

**ValidateAndAcceptLine** est utilisé pour éviter d’encombrer votre historique avec des commandes qui ne fonctionnent pas.

```yaml
Type: System.Action`1[System.Management.Automation.Language.CommandAst]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CompletionQueryItems

Spécifie le nombre maximal d’éléments de saisie semi-automatique affichés sans invite.

Si le nombre d’éléments à afficher est supérieur à cette valeur, **PSReadLine** invite **Oui/non** avant d’afficher les éléments de saisie semi-automatique.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### -ContinuationPrompt

Spécifie la chaîne affichée au début des lignes suivantes lorsque l’entrée multiligne est entrée. La valeur par défaut est double signe supérieur à ( `>>` ). Une chaîne vide est valide.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: >>
Accept pipeline input: False
Accept wildcard characters: False
```

### -DingDuration

Spécifie la durée du signal sonore quand **BellStyle** est défini sur **audible**.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 50ms
Accept pipeline input: False
Accept wildcard characters: False
```

### -DingTone

Spécifie le ton en Hertz (Hz) du bip quand **BellStyle** est défini sur **audible**.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1221
Accept pipeline input: False
Accept wildcard characters: False
```

### -EditMode

Spécifie le mode d’édition de la ligne de commande. L’utilisation de ce paramètre réinitialise toutes les combinaisons de touches définies par `Set-PSReadLineKeyHandler` .

Les valeurs valides sont les suivantes :

- **Windows** : les combinaisons de touches émulent PowerShell, cmd et Visual Studio.
- **Emacs** -les combinaisons de touches émulent bash ou Emacs.
- **VI** : les combinaisons de touches émulent VI.

Utilisez `Get-PSReadLineKeyHandler` pour afficher les combinaisons de touches pour le **EditMode** actuellement configuré.

```yaml
Type: Microsoft.PowerShell.EditMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Windows
Accept pipeline input: False
Accept wildcard characters: False
```

### -ExtraPromptLineCount

Spécifie le nombre de lignes supplémentaires.

Si votre invite s’étend sur plusieurs lignes, spécifiez une valeur pour ce paramètre. Utilisez cette option lorsque vous souhaitez que des lignes supplémentaires soient disponibles quand **PSReadLine** affiche l’invite après avoir affiché une sortie. Par exemple, **PSReadLine** retourne une liste des saisies semi-automatiques.

Cette option est requise moins que dans les versions précédentes de **PSReadLine** , mais elle est utile lorsque la `InvokePrompt` fonction est utilisée.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -HistoryNoDuplicates

Cette option contrôle le comportement de rappel. Les commandes dupliquées sont toujours ajoutées au fichier d’historique.
Lorsque cette option est définie, seul l’appel le plus récent s’affiche lorsque vous rappelez des commandes. Les commandes répétées sont ajoutées à l’historique pour préserver le classement pendant le rappel. Toutefois, vous ne souhaitez généralement pas voir la commande plusieurs fois lors du rappel ou de la recherche dans l’historique.

Par défaut, la propriété **HistoryNoDuplicates** de l’objet global **PSConsoleReadLineOptions** a la valeur `True` . L’utilisation de cet **Paramètre_Booléen** affecte la valeur à la propriété `True` . Pour modifier la valeur de la propriété, vous devez spécifier la valeur de **Paramètre_Booléen** comme suit : `-HistoryNoDuplicates:$False` .

À l’aide de la commande suivante, vous pouvez définir directement la valeur de la propriété :

`(Get-PSReadLineOption).HistoryNoDuplicates = $False`

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

### -HistorySavePath

Spécifie le chemin d’accès au fichier dans lequel l’historique est enregistré. Les ordinateurs exécutant des plates-formes Windows ou non Windows stockent le fichier à différents emplacements. Le nom de fichier est stocké dans une variable `$($host.Name)_history.txt` , par exemple `ConsoleHost_history.txt` .

Si vous n’utilisez pas ce paramètre, le chemin d’accès par défaut est le suivant :

**Windows**

`$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine\$($host.Name)_history.txt`

**non-Windows**

`$env:XDG_DATA_HOME/powershell/PSReadLine\$($host.Name)_history.txt`

`$env:HOME/.local/share/powershell/PSReadLine\$($host.Name)_history.txt`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: A file named $($host.Name)_history.txt in $env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine on Windows and $env:XDG_DATA_HOME/powershell/PSReadLine or $env:HOME/.local/share/powershell/PSReadLine on non-Windows platforms
Accept pipeline input: False
Accept wildcard characters: False
```

### -HistorySaveStyle

Spécifie la manière dont **PSReadLine** enregistre l’historique.

Les valeurs valides sont les suivantes :

- **SaveIncrementally** : enregistrer l’historique après l’exécution de chaque commande et le partage entre plusieurs instances de PowerShell.
- **SaveAtExit** : ajouter le fichier d’historique à la sortie de PowerShell.
- **SaveNothing** : n’utilisez pas de fichier d’historique.

```yaml
Type: Microsoft.PowerShell.HistorySaveStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: SaveIncrementally
Accept pipeline input: False
Accept wildcard characters: False
```

### -HistorySearchCaseSensitive

Spécifie que la recherche dans l’historique respecte la casse dans des fonctions telles que **ReverseSearchHistory** ou **HistorySearchBackward**.

Par défaut, la propriété **HistorySearchCaseSensitive** de l’objet global **PSConsoleReadLineOptions** a la valeur `False` . L’utilisation de cet **Paramètre_Booléen** affecte la valeur à la propriété `True` . Pour modifier la valeur de la propriété, vous devez spécifier la valeur de **Paramètre_Booléen** comme suit : `-HistorySearchCaseSensitive:$False` .

À l’aide de la commande suivante, vous pouvez définir directement la valeur de la propriété :

`(Get-PSReadLineOption).HistorySearchCaseSensitive = $False`

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

### -HistorySearchCursorMovesToEnd

Indique que le curseur se déplace vers la fin des commandes que vous chargez à partir de l’historique à l’aide d’une recherche.
Lorsque ce paramètre a la valeur `$False` , le curseur reste à la position où il se trouvait quand vous avez appuyé sur les flèches haut ou bas.

Par défaut, la propriété **HistorySearchCursorMovesToEnd** de l’objet global **PSConsoleReadLineOptions** a la valeur `False` . À l’aide de cet **Paramètre_Booléen** , affectez la valeur à la propriété `True` . Pour modifier la valeur de la propriété, vous devez spécifier la valeur de **Paramètre_Booléen** comme suit : `-HistorySearchCursorMovesToEnd:$False` .

À l’aide de la commande suivante, vous pouvez définir directement la valeur de la propriété :

`(Get-PSReadLineOption).HistorySearchCursorMovesToEnd = $False`

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

### -MaximumHistoryCount

Spécifie le nombre maximal de commandes à enregistrer dans l’historique **PSReadLine** .

L’historique de **PSReadLine** est séparé de l’historique PowerShell.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumKillRingCount

Spécifie le nombre maximal d’éléments stockés dans l’anneau Kill.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### -PromptText

En cas d’erreur d’analyse, **PSReadLine** modifie une partie de l’invite rouge. **PSReadLine** analyse votre fonction d’invite pour déterminer comment modifier uniquement la couleur d’une partie de votre invite. Cette analyse n’est pas 100% fiable.

Utilisez cette option si **PSReadLine** modifie votre invite de manière inattendue. Inclut tout espace blanc de fin.

Par exemple, si votre fonction d’invite ressemble à l’exemple suivant :

`function prompt { Write-Host -NoNewLine -ForegroundColor Yellow "$pwd"; return "# " }`

Ensuite, définissez :

`Set-PSReadLineOption -PromptText "# "`

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: >
Accept pipeline input: False
Accept wildcard characters: False
```

### -ShowToolTips

Lorsque vous affichez les saisies semi-automatiques possibles, les info-bulles sont affichées dans la liste des saisies semi-automatiques.

Cette option est activée par défaut. Cette option n’a pas été activée par défaut dans les versions antérieures de **PSReadLine**. Pour désactiver, définissez cette option sur `$False` .

Par défaut, la propriété **ShowToolTips** de l’objet global **PSConsoleReadLineOptions** a la valeur `True` . L’utilisation de cet **Paramètre_Booléen** affecte la valeur à la propriété `True` . Pour modifier la valeur de la propriété, vous devez spécifier la valeur de **Paramètre_Booléen** comme suit : `-ShowToolTips:$False` .

À l’aide de la commande suivante, vous pouvez définir directement la valeur de la propriété :

`(Get-PSReadLineOption).ShowToolTips = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### -ViModeChangeHandler

Lorsque **ViModeIndicator** a la valeur `Script` , le bloc de script fourni est appelé chaque fois que le mode change. Le bloc de script est fourni avec un argument de type `ViMode` .

Ce paramètre a été introduit dans PowerShell 7.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ViModeIndicator

Cette option définit l’indication visuelle pour le mode **VI** actuel. Mode insertion ou mode commande.

Les valeurs valides sont les suivantes :

- **None** : il n’existe aucune indication.
- **Prompt** : l’invite change de couleur.
- **Curseur** : le curseur change de taille.
- **Script** : le texte spécifié par l’utilisateur est imprimé.

```yaml
Type: Microsoft.PowerShell.ViModeStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WordDelimiters

Spécifie les caractères qui délimitent les mots pour des fonctions telles que **ForwardWord** ou **KillWord**.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: ;:,.[]{}()/\|^&*-=+'"–—―
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## Entrées

### None

Vous ne pouvez pas diriger d’objets vers `Set-PSReadLineOption.`

## Sorties

### Aucun

Cette applet de commande ne génère aucune sortie.

## Notes

## Liens connexes

[about_PSReadLine](./About/about_PSReadLine.md)

[PSReadLineKeyHandler](Get-PSReadLineKeyHandler.md)

[PSReadLineOption](Get-PSReadLineOption.md)

[Remove-PSReadLineKeyHandler](Remove-PSReadLineKeyHandler.md)

[Set-PSReadLineKeyHandler](Set-PSReadLineKeyHandler.md)
