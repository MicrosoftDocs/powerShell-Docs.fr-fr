---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restart-service?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restart-Service
ms.openlocfilehash: 5ad6fb4d39b604834bb77935b14686e088bb61f2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202221"
---
# Restart-Service

## SYNOPSIS
Arrête, puis démarre un ou plusieurs services.

## SYNTAX

### InputObject (valeur par défaut)

```
Restart-Service [-Force] [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Default

```
Restart-Service [-Force] [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### DisplayName

```
Restart-Service [-Force] [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L’applet de commande **Restart-Service** envoie un message d’arrêt, puis un message de démarrage au contrôleur de services Windows pour un service spécifié.
Si un service est déjà arrêté, il est démarré sans notification d'erreur.
Vous pouvez spécifier les services par leur nom de service ou leur nom d’affichage, ou vous pouvez utiliser le paramètre *InputObject* pour passer un objet qui représente chaque service que vous souhaitez redémarrer.

## EXEMPLES

### Exemple 1 : redémarrer un service sur l’ordinateur local

```powershell
PS C:\> Restart-Service -Name winmgmt
```

Cette commande redémarre le service WMI (Windows Management Instrumentation) WinMgmt sur l'ordinateur local.

### Exemple 2 : exclure un service

```powershell
PS C:\> Restart-Service -DisplayName "net*" -Exclude "net logon"
```

Cette commande redémarre les services dont le nom d’affichage commence par net, à l’exception du service d’ouverture de session réseau.

### Exemple 3 : démarrer tous les services réseau arrêtés

```powershell
PS C:\> Get-Service -Name "net*" | Where-Object {$_.Status -eq "Stopped"} | Restart-Service
```

Cette commande démarre tous les services réseau arrêtés sur l'ordinateur.

Cette commande utilise l’applet de commande Get-Service pour récupérer des objets qui représentent les services dont le nom de service commence par net.
L’opérateur de pipeline (|) envoie l’objet de services à l’applet de commande Where-Object, qui sélectionne uniquement les services dont l’État est arrêté.
Un autre opérateur de pipeline envoie les services sélectionnés à **Restart-Service** .

Dans la pratique, vous utiliseriez le paramètre *WhatIf* pour déterminer l’effet de la commande avant de l’exécuter.

## PARAMETERS

### -DisplayName

Spécifie les noms d’affichage des services à redémarrer.
Les caractères génériques sont autorisés.

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

Spécifie les services que cette applet de commande omet.
La valeur de ce paramètre qualifie le paramètre *Name* .
Entrez un élément ou un modèle de nom, tel que s *.
Les caractères génériques sont autorisés.

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

### -Force

Force l’exécution de la commande sans demander la confirmation de l’utilisateur.

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

### -Include

Spécifie les services redémarrés par cette applet de commande.
La valeur de ce paramètre qualifie le paramètre *Name* .
Entrez un élément ou un modèle de nom, tel que s *.
Les caractères génériques sont autorisés.

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

Spécifie les objets **ServiceController** qui représentent les services à redémarrer.
Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.

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

Spécifie les noms des services à redémarrer.

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

Retourne un objet qui représente le nouveau service.
Par défaut, cette applet de commande ne génère aucun résultat.

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

Cette applet de commande génère un objet **System. ServiceProcess. ServiceController** qui représente le service redémarré, si vous spécifiez le paramètre *PassThru* .
Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

* **Restart-Service** peut contrôler les services uniquement lorsque l’utilisateur actuel est autorisé à le faire. Si une commande ne fonctionne pas correctement, cela signifie peut-être que vous ne disposez pas des autorisations requises.
* Pour rechercher les noms de service et les noms d’affichage des services sur votre système, tapez « **obtenir-service** ». Les noms de service s’affichent dans la colonne **nom** , et les noms d’affichage apparaissent dans la colonne **DisplayName** .

## LIENS CONNEXES

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)

[Remove-Service](Remove-Service.md)

