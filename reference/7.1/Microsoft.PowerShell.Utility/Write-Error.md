---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-error?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Error
ms.openlocfilehash: ad9e3daa7d67fc2bec6fa19a873573ce33dc609d
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208473"
---
# Write-Error

## SYNOPSIS
Écrit un objet dans le flux d'erreurs.

## SYNTAX

### Noexception (valeur par défaut)

```
Write-Error [-Message] <String> [-Category <ErrorCategory>] [-ErrorId <String>] [-TargetObject <Object>]
 [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### WithException

```
Write-Error -Exception <Exception> [[-Message] <String>] [-Category <ErrorCategory>] [-ErrorId <String>]
 [-TargetObject <Object>] [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### ErrorRecord

```
Write-Error -ErrorRecord <ErrorRecord> [-RecommendedAction <String>] [-CategoryActivity <String>]
 [-CategoryReason <String>] [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

## Description

L' `Write-Error` applet de commande déclare une erreur sans fin d’achèvement. Par défaut, les erreurs sont envoyées dans le flux d'erreurs vers le programme hôte pour être affichées, avec la sortie.

Pour écrire une erreur sans fin d'exécution, entrez une chaîne de message d'erreur, un objet **ErrorRecord** ou un objet **Exception** . Utilisez les autres paramètres de `Write-Error` pour remplir l’enregistrement d’erreur.

Les erreurs sans fin d'exécution écrivent une erreur dans le flux d'erreurs, mais elles n'arrêtent pas le traitement des commandes.
Si une erreur sans fin d'exécution est déclarée sur un élément dans une collection d'éléments d'entrée, la commande continue de traiter les autres éléments dans la collection.

Pour déclarer une erreur d’arrêt, utilisez le `Throw` mot clé.
Pour plus d’informations, consultez [about_Throw](../Microsoft.PowerShell.Core/About/about_Throw.md).

## EXEMPLES

### Exemple 1 : écrire une erreur pour l’objet RegistryKey

```powershell
Get-ChildItem | ForEach-Object {
    if ($_.GetType().ToString() -eq "Microsoft.Win32.RegistryKey")
    {
        Write-Error "Invalid object" -ErrorId B1 -TargetObject $_
    }
    else
    {
        $_
    }
}
```

Cette commande déclare une erreur sans fin d’achèvement lorsque l' `Get-ChildItem` applet de commande retourne un `Microsoft.Win32.RegistryKey` objet, tel que les objets dans `HKLM:` les `HKCU:` lecteurs ou du fournisseur de Registre PowerShell.

### Exemple 2 : écrire un message d’erreur dans la console

```powershell
Write-Error "Access denied."
```

Cette commande déclare une erreur sans fin d'exécution et écrit une erreur « Accès refusé ». La commande utilise le paramètre **Message** pour spécifier le message, mais omet le nom du paramètre **Message** facultatif.

### Exemple 3 : écrire une erreur dans la console et spécifier la catégorie

```powershell
Write-Error -Message "Error: Too many input values." -Category InvalidArgument
```

Cette commande déclare une erreur sans fin d'exécution et spécifie une catégorie d'erreur.

### Exemple 4 : écrire une erreur à l’aide d’un objet exception

```powershell
$E = [System.Exception]@{Source="Get-ParameterNames.ps1";HelpLink="https://go.microsoft.com/fwlink/?LinkID=113425"}
Write-Error -Exception $E -Message "Files not found. The $Files location does not contain any XML files."
```

Cette commande utilise un objet **Exception** pour déclarer une erreur sans fin d'exécution.

La première commande utilise une table de hachage pour créer l'objet **System.Exception** . Elle enregistre l’objet exception dans la `$E` variable. Vous pouvez utiliser une table de hachage pour créer n'importe quel objet d'un type qui a un constructeur de valeur null.

La deuxième commande utilise l' `Write-Error` applet de commande pour déclarer une erreur sans fin d’achèvement. La valeur du paramètre **exception** est l’objet **exception** dans la `$E` variable.

## PARAMETERS

### -Catégorie

Spécifie la catégorie de l'erreur. La valeur par défaut est **NotSpecified** . Les valeurs valides pour ce paramètre sont :

- NotSpecified
- OpenError
- CloseError
- DeviceError
- DeadlockDetected
- InvalidArgument
- InvalidData
- InvalidOperation
- InvalidResult
- InvalidType
- MetadataError
- NotImplemented
- NotInstalled
- ObjectNotFound
- OperationStopped
- OperationTimeout
- SyntaxError
- ParserError
- PermissionDenied
- ResourceBusy
- ResourceExists
- ResourceUnavailable
- ReadError
- WriteError
- FromStdErr
- SecurityError
- ProtocolError
- ConnectionError
- AuthenticationError
- LimitsExceeded
- QuotaExceeded
- NotEnabled

Pour plus d’informations sur les catégories d’erreur, consultez [énumération ErrorCategory](https://go.microsoft.com/fwlink/?LinkId=143600).

```yaml
Type: System.Management.Automation.ErrorCategory
Parameter Sets: NoException, WithException
Aliases:
Accepted values: NotSpecified, OpenError, CloseError, DeviceError, DeadlockDetected, InvalidArgument, InvalidData, InvalidOperation, InvalidResult, InvalidType, MetadataError, NotImplemented, NotInstalled, ObjectNotFound, OperationStopped, OperationTimeout, SyntaxError, ParserError, PermissionDenied, ResourceBusy, ResourceExists, ResourceUnavailable, ReadError, WriteError, FromStdErr, SecurityError, ProtocolError, ConnectionError, AuthenticationError, LimitsExceeded, QuotaExceeded, NotEnabled

Required: False
Position: Named
Default value: NotSpecified
Accept pipeline input: False
Accept wildcard characters: False
```

### -CategoryActivity

Spécifie l’action à l’origine de l’erreur.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Activity

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CategoryReason

Spécifie comment ou pourquoi l’activité a provoqué l’erreur.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Reason

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CategoryTargetName

Spécifie le nom de l'objet en cours de traitement quand l'erreur s'est produite.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: TargetName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CategoryTargetType

Spécifie le type de l'objet en cours de traitement quand l'erreur s'est produite.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: TargetType

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ErrorId

Spécifie une chaîne d'identification pour identifier l'erreur. La chaîne doit être propre à l'erreur.

```yaml
Type: System.String
Parameter Sets: NoException, WithException
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ErrorRecord

Spécifie un objet d'enregistrement d'erreur qui représente l'erreur. Utilisez les propriétés de l'objet pour décrire l'erreur.

Pour créer un objet enregistrement d’erreur, utilisez l’applet de commande `New-Object` ou récupérez un objet enregistrement d’erreur à partir du tableau dans la `$Error` variable automatique.

```yaml
Type: System.Management.Automation.ErrorRecord
Parameter Sets: ErrorRecord
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Exception

Spécifie un objet d'exception qui représente l'erreur. Utilisez les propriétés de l'objet pour décrire l'erreur.

Pour créer un objet exception, utilisez une table de hachage ou utilisez l’applet de commande `New-Object` .

```yaml
Type: System.Exception
Parameter Sets: WithException
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Message

Spécifie le texte du message de l'erreur. Si le texte comprend des espaces ou des caractères spéciaux, placez-le entre guillemets. Vous pouvez également diriger une chaîne de message vers `Write-Error` .

```yaml
Type: System.String
Parameter Sets: NoException, WithException
Aliases: Msg

Required: True (NoException), False (WithException)
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -RecommendedAction

Spécifie l’action que l’utilisateur doit entreprendre pour résoudre ou éviter l’erreur.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TargetObject

Spécifie l'objet en cours de traitement quand l'erreur s'est produite. Entrez l’objet, une variable qui contient l’objet ou une commande qui obtient l’objet.

```yaml
Type: System.Object
Parameter Sets: NoException, WithException
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

### System.String

Vous pouvez diriger une chaîne qui contient un message d’erreur vers `Write-Error` .

## SORTIES

### Objet d’erreur

`Write-Error` écrit uniquement dans le flux d’erreurs. Aucun objet n'est retourné.

## REMARQUES

`Write-Error` ne modifie pas la valeur de la `$?` variable automatique. par conséquent, elle ne signale pas une condition d’erreur de fin. Pour signaler une erreur de fin, utilisez la méthode [$PSCmdlet. WriteError ()](/dotnet/api/system.management.automation.cmdlet.writeerror) .

## LIENS CONNEXES

[about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md)

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Write-Debug](Write-Debug.md)

[Write-Host](Write-Host.md)

[Write-Output](Write-Output.md)

[Write-Progress](Write-Progress.md)

[Write-Verbose](Write-Verbose.md)

[Write-Warning](Write-Warning.md)
