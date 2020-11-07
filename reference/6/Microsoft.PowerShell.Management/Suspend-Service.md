---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/suspend-service?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Service
ms.openlocfilehash: 5e4037c4ba8947f8efb438103f2bfd47eb05d1f5
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94343733"
---
# Suspend-Service

## SYNOPSIS
Interrompt (suspend) un ou plusieurs services en cours d'exécution.

## SYNTAXE

### InputObject (valeur par défaut)

```
Suspend-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Default

```
Suspend-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DisplayName

```
Suspend-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

L' `Suspend-Service` applet de commande envoie un message d’interruption au contrôleur de services Windows pour chacun des services spécifiés. Pendant l’interruption, le service est toujours en cours d’exécution, mais son action est arrêtée jusqu’à sa reprise, par exemple par l’applet de commande objet `Resume-Service` . Vous pouvez spécifier les services par leur nom de service ou leur nom d’affichage, ou vous pouvez utiliser le paramètre **InputObject** pour passer un objet de service qui représente les services que vous souhaitez suspendre.

## EXEMPLES

### Exemple 1 : suspendre un service

```
PS C:\> Suspend-Service -DisplayName "Telnet"
```

Cette commande interrompt le service Telnet (Tlntsvr) sur l’ordinateur local.

### Exemple 2 : afficher ce qui se passerait si vous suspendez des services

```
PS C:\> Suspend-Service -Name lanman* -WhatIf
```

Cette commande indique ce qui se passerait si vous suspendiez les services dont le nom de service commence par LANMAN. Pour interrompre les services, réexécutez la commande sans le paramètre **WhatIf** .

### Exemple 3 : obtenir et suspendre un service

```
PS C:\> Get-Service schedule | Suspend-Service
```

Cette commande utilise l' `Get-Service` applet de commande pour récupérer un objet qui représente le service Planificateur de tâches (planification) sur l’ordinateur. L’opérateur de pipeline ( `|` ) passe le résultat à `Suspend-Service` , qui suspend le service.

### Exemple 4 : suspendre tous les services qui peuvent être suspendus

```
PS C:\> Get-Service | Where-Object {$_.CanPauseAndContinue -eq "True"} | Suspend-Service -Confirm
```

Cette commande interrompt tous les services pouvant être interrompus sur l’ordinateur. Elle utilise `Get-Service` pour récupérer des objets qui représentent les services sur l’ordinateur. L’opérateur de pipeline passe les résultats à l’applet de commande `Where-Object` , qui sélectionne uniquement les services dont `$True` la valeur est pour la propriété **CanPauseAndContinue** . Un autre opérateur de pipeline passe les résultats à `Suspend-Service` . Le paramètre **Confirm** vous invite à confirmer l’interruption de chaque service.

## PARAMÈTRES

### -DisplayName

Spécifie les noms d’affichage des services à interrompre. Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: DisplayName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Exclude

Spécifie les services à omettre des services spécifiés. La valeur de ce paramètre qualifie le paramètre **Name** . Entrez un élément ou un modèle de nom, tel que « s* ». Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Include

Spécifie les services à interrompre. La valeur de ce paramètre qualifie le paramètre **Name** . Entrez un élément ou un modèle de nom, tel que « s* ». Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -InputObject

Spécifie les objets **ServiceController** qui représentent les services à interrompre. Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Spécifie les noms des services à interrompre. Les caractères génériques sont autorisés.

Le nom de paramètre est facultatif. Vous pouvez utiliser **Name** ou son alias, **ServiceName** ou omettre le nom du paramètre.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -PassThru

Retourne un objet représentant l’élément que vous utilisez. Par défaut, cette applet de commande ne génère aucun résultat.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Vous demande une confirmation avant d’exécuter l’applet de commande.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Montre ce qui se passe en cas d’exécution de l’applet de commande.
L’applet de commande n’est pas exécutée.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. ServiceProcess. ServiceController, System. String

Vous pouvez diriger un objet de service ou une chaîne qui contient un nom de service vers cette applet de commande.

## SORTIES

### Aucun, System. ServiceProcess. ServiceController

Cette applet de commande génère un objet **System. ServiceProcess. ServiceController** qui représente le service, si vous spécifiez le paramètre **PassThru** . Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

Cette applet de commande est disponible uniquement sur les plateformes Windows.

- `Suspend-Service` peut contrôler les services uniquement lorsque l’utilisateur actuel est autorisé à le faire. Si une commande ne fonctionne pas correctement, cela signifie peut-être que vous ne disposez pas des autorisations requises.
- `Suspend-Service` peut suspendre uniquement les services qui prennent en charge l’interruption et la reprise. Pour déterminer si un service particulier peut être interrompu, utilisez l' `Get-Service` applet de commande avec la propriété **CanPauseAndContinue** . Par exemple, `Get-Service wmi | Format-List Name, CanPauseAndContinue`. Pour rechercher tous les services sur l’ordinateur qui peuvent être suspendus, tapez `Get-Service | Where-Object {$_.CanPauseAndContinue -eq $true}` .
- Pour rechercher les noms de service et les noms d’affichage des services sur votre système, tapez `Get-Service` .
  Les noms de service s’affichent dans la colonne **nom** , et les noms d’affichage apparaissent dans la colonne **DisplayName** .

## LIENS CONNEXES

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Remove-Service](Remove-Service.md)
