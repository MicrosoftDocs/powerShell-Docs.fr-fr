---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/export-modulemember?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-ModuleMember
ms.openlocfilehash: a8f059a5f7ae36415054dd94f87a1224d64c2cbf
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202318"
---
# Export-ModuleMember

## SYNOPSIS
Spécifie les membres de module exportés.

## SYNTAX

```
Export-ModuleMember [[-Function] <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>]
 [<CommonParameters>]
```

## Description

L’applet de commande **Export-ModuleMember** spécifie les membres de module exportés à partir d’un fichier de module de script (. psm1), ou à partir d’un module dynamique créé à l’aide de l’applet de commande New-Module.
Les membres de module incluent des applets de commande, des fonctions, des variables et des alias.
Cette applet de commande peut être utilisée uniquement dans un fichier de module de script ou un module dynamique.

Si un module de script n’inclut pas de commande **Export-ModuleMember** , les fonctions et les alias dans le module de script sont exportés, mais les variables ne le sont pas.
Quand un module de script comprend des commandes **Export-ModuleMember** , seuls les membres spécifiés dans les commandes **Export-ModuleMember** sont exportés.
Vous pouvez également utiliser **Export-ModuleMember** pour supprimer ou exporter des membres que le module de script importe à partir d’autres modules.

Une commande **Export-ModuleMember** est facultative, mais il s’agit d’une bonne pratique.
Même si la commande confirme les valeurs par défaut, elle illustre l'intention de l'auteur du module.

## EXEMPLES

### Exemple 1 : exporter des fonctions et des alias dans un module de script

```powershell
Export-ModuleMember -Function * -Alias *
```

Cette commande exporte toutes les fonctions et les alias définis dans le module de script.

### Exemple 2 : exporter des alias et des fonctions spécifiques

```powershell
Export-ModuleMember -Function Get-Test, New-Test, Start-Test -Alias gtt, ntt, stt
```

Cette commande exporte trois alias et trois fonctions définies dans le module de script.

Vous pouvez utiliser ce format de commande pour spécifier les noms des membres de module.

### Exemple 3 : exporter aucun membre

```powershell
Export-ModuleMember
```

Cette commande spécifie qu'aucun membre défini dans le module de script n'est exporté.

Cette commande empêche l'exportation des membres du module, mais elle ne masque pas les membres.
Les utilisateurs peuvent lire et copier les membres de module, ou utiliser l'opérateur d'appel (&) pour appeler les membres de module qui ne sont pas exportés.

### Exemple 4 : exporter une variable spécifique

```powershell
Export-ModuleMember -Variable increment
```

Cette commande exporte uniquement la variable $increment à partir du module de script.
Aucun autre membre n'est exporté.

Si vous souhaitez exporter une variable, outre l’exportation des fonctions dans un module, la commande **Export-ModuleMember** doit inclure les noms de toutes les fonctions et le nom de la variable.

### Exemple 5 : commandes d’exportation multiples

```powershell
# From TestModule.psm1
Function New-Test
{
    Write-Output 'I am New-Test function'
}
Export-ModuleMember -Function New-Test

function Validate-Test
{
    Write-Output 'I am Validate-Test function'
}
function Start-Test
{
    Write-Output 'I am Start-Test function'
}
Set-Alias stt Start-Test
Export-ModuleMember -Function Start-Test -Alias stt
```

Ces commandes montrent comment plusieurs commandes **Export-ModuleMember** sont interprétées dans un fichier de module de script (. psm1).

Ces commandes créent trois fonctions et un alias, puis exportent deux des fonctions et l'alias.

Sans les commandes **Export-ModuleMember** , les trois fonctions et l’alias seront exportés.
Avec les commandes **Export-ModuleMember** , seules les fonctions **New-Test** et **Start-test** et l’alias STT sont exportées.

### Exemple 6 : exporter des membres dans un module dynamique

```powershell
New-Module -Script {function SayHello {"Hello!"}; Set-Alias Hi SayHello; Export-ModuleMember -Alias Hi -Function SayHello}
```

Cette commande montre comment utiliser Export-ModuleMember dans un module dynamique créé à l’aide de l’applet **de commande New-module** .

Dans cet exemple, **Export-ModuleMember** est utilisé pour exporter l’alias Hi et la fonction **sayHello** dans le module dynamique.

### Exemple 7 : déclarer et exporter une fonction dans une seule commande

```powershell
# From TestModule.psm1
function Export
{
  param (
    [Parameter(Mandatory=$true)]
    [ValidateSet("function","variable")]
    $Type,
    [Parameter(Mandatory=$true)]
    $Name,
    [Parameter(Mandatory=$true)]
    $Value
    )

    if ($Type -eq "function")
    {
        Set-item "function:script:$Name" $Value
        Export-ModuleMember $Name
    }
    else
    {
    Set-Variable -scope Script $Name $Value
    Export-ModuleMember -variable $Name
    }
}

Export function New-Test {Write-Output 'I am New-Test function'}
function helper {Write-Output 'I am helper function'}

Export variable Interval 0
$Interval = 2
```

Cet exemple comprend une fonction nommée **Export** qui déclare une fonction ou crée une variable, puis écrit une `Export-ModuleMember` commande pour la fonction ou la variable.
Cela vous permet de déclarer et d'exporter une fonction ou une variable dans une seule commande.

Pour utiliser la fonction d' **exportation** , incluez-la dans votre module de script.
Pour exporter une fonction, tapez `Export` avant le mot clé **Function** .

Pour exporter une variable, utilisez le format suivant pour déclarer la variable et définissez sa valeur :

`Export variable <variable-name> <value>`

Les commandes dans l'exemple montrent le format correct.
Dans cet exemple, seule la fonction **New-test** et la variable $Interval sont exportées.

## PARAMETERS

### -Alias

Spécifie les alias qui sont exportés à partir du fichier de module de script.
Entrez les noms des alias.
Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Applet de commande

Spécifie les applets de commande qui sont exportés à partir du fichier de module de script.
Entrez les noms des applets de commande.
Les caractères génériques sont autorisés.

Vous ne pouvez pas créer des applets de commande dans un fichier de module de script, mais vous pouvez importer les applets de commande à partir d'un module binaire dans un module de script et les exporter de nouveau à partir du module de script.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Fonction

Spécifie les fonctions exportées à partir du fichier de module de script.
Entrez les noms des fonctions.
Les caractères génériques sont autorisés.
Vous pouvez également diriger les chaînes de nom de fonction vers **Export-ModuleMember** .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Variable

Spécifie les variables exportées à partir du fichier de module de script.
Entrez les noms des variables, sans le signe dollar.
Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

Vous pouvez diriger les chaînes de nom de fonction vers cette applet de commande.

## SORTIES

### Aucun

Cette applet de commande ne génère aucune sortie.

## REMARQUES

* Pour exclure un membre de la liste des membres exportés, ajoutez une commande **Export-ModuleMember** qui répertorie tous les autres membres mais qui omet le membre que vous souhaitez exclure.

## LIENS CONNEXES

[Get-Module](Get-Module.md)

[Module d’importation](Import-Module.md)

[Remove-Module](Remove-Module.md)

[about_Modules](About/about_Modules.md)
