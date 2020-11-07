---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Service
ms.openlocfilehash: f9aacc2d27ef0f0ec6f3c3854f1da07f32a13383
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94342652"
---
# Start-Service

## SYNOPSIS
Démarre un ou plusieurs services arrêtés.

## SYNTAXE

### InputObject (valeur par défaut)

```
Start-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Default

```
Start-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DisplayName

```
Start-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

L' `Start-Service` applet de commande envoie un message de démarrage au contrôleur de services Windows pour chacun des services spécifiés. Si un service est déjà en cours d'exécution, le message est ignoré sans erreur. Vous pouvez spécifier les services par leur nom de service ou leur nom d’affichage, ou vous pouvez utiliser le paramètre **InputObject** pour fournir un objet de service qui représente les services que vous souhaitez démarrer.

## EXEMPLES

### Exemple 1 : démarrer un service à l’aide de son nom

Cet exemple démarre le service EventLog sur l’ordinateur local. Le paramètre **Name** identifie le service par son nom de service.

```powershell
Start-Service -Name "eventlog"
```

### Exemple 2 : afficher des informations sans démarrer un service

Cet exemple montre ce qui se produit si vous avez démarré les services dont le nom d’affichage comprend « Remote ».

```powershell
Start-Service -DisplayName *remote* -WhatIf
```

Le paramètre **DisplayName** identifie les services par leur nom d’affichage au lieu de leur nom de service. Le paramètre **WhatIf** permet à l’applet de commande d’afficher ce qui se passerait lorsque vous exécuterez la commande sans apporter de modifications.

### Exemple 3 : démarrer un service et enregistrer l’action dans un fichier texte

Cet exemple démarre le service Windows Management Instrumentation (WMI) sur l’ordinateur et ajoute un enregistrement de l’action au fichier services.txt.

```powershell
$s = Get-Service wmi
Start-Service -InputObject $s -PassThru | Format-List >> services.txt
```

Tout d’abord, nous utilisons `Get-Service` pour récupérer un objet qui représente le service WMI et le stocker dans la `$s` variable. Ensuite, nous démarrons le service. Sans le paramètre **PassThru** , `Start-Service` ne crée aucune sortie. L’opérateur de pipeline (|) passe la sortie de l’objet à `Start-Service` l’applet de commande `Format-List` pour mettre en forme l’objet sous la forme d’une liste de ses propriétés. L’opérateur de redirection d’ajout ( \> \> ) redirige la sortie vers le fichier services.txt. La sortie est ajoutée à la fin du fichier existant.

### Exemple 4 : démarrer un service désactivé

Cet exemple montre comment démarrer un service lorsque le type de démarrage du service est **désactivé**.

```
PS> Start-Service tlntsvr
Start-Service : Service 'Telnet (TlntSvr)' cannot be started due to the following error: Cannot start service TlntSvr on computer '.'.
At line:1 char:14
+ Start-Service  <<<< tlntsvr

PS> Get-CimInstance win32_service | Where-Object Name -eq "tlntsvr"
ExitCode  : 0
Name      : TlntSvr
ProcessId : 0
StartMode : Disabled
State     : Stopped
Status    : OK

PS> Set-Service tlntsvr -StartupType manual
PS> Start-Service tlntsvr
```

La première tentative de démarrage du service Telnet (tlntsvr) échoue. La `Get-CimInstance` commande indique que la propriété **startMode** du service tlntsvr est **désactivée**. L' `Set-Service` applet de commande change le type de démarrage en **Manuel**. Nous pouvons à présent soumettre à nouveau la `Start-Service` commande. Cette fois, elle réussit. Pour vérifier que la commande a réussi, exécutez `Get-Service` .

## PARAMÈTRES

### -DisplayName

Spécifie les noms d’affichage des services à démarrer. Les caractères génériques sont autorisés.

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

Spécifie les services que cette applet de commande omet. La valeur de ce paramètre qualifie le paramètre **Name** . Entrez un élément ou un modèle de nom, tel que `s*` . Les caractères génériques sont autorisés.

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

Spécifie les services que cette applet de commande démarre. La valeur de ce paramètre qualifie le paramètre **Name** . Entrez un élément ou un modèle de nom, tel que `s*` . Les caractères génériques sont autorisés.

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

Spécifie les objets **ServiceController** représentant les services à démarrer. Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.

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

Spécifie le nom de service du service à démarrer.

Le nom de paramètre est facultatif. Vous pouvez utiliser **Name** ou son alias, **ServiceName** ou omettre le nom du paramètre.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -PassThru

Retourne un objet qui représente le nouveau service. Par défaut, cette applet de commande ne génère aucun résultat.

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

Vous pouvez diriger les objets qui représentent les services ou les chaînes qui contiennent les noms de service vers cette applet de commande.

## SORTIES

### Aucun, System. ServiceProcess. ServiceController

Cette applet de commande génère un objet **System. ServiceProcess. ServiceController** qui représente le service, si vous spécifiez **PassThru**. Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

- Vous pouvez également faire référence à `Start-Service` par son alias intégré, `sasv` . Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).
- `Start-Service` peut contrôler les services uniquement si l’utilisateur actuel est autorisé à le faire. Si une commande ne fonctionne pas correctement, cela signifie peut-être que vous ne disposez pas des autorisations requises.
- Pour rechercher les noms de service et les noms d’affichage des services sur votre système, tapez `Get-Service` .
  Les noms de service s’affichent dans la colonne **nom** , et les noms d’affichage apparaissent dans la colonne **DisplayName** .
- Vous pouvez uniquement démarrer les services dont le type de démarrage est manuel, automatique ou automatique (début différé). Vous ne pouvez pas démarrer les services dont le type de démarrage est désactivé. Si une `Start-Service` commande échoue avec le message `Cannot start service \<service-name\> on computer` , utilisez `Get-CimInstance` pour rechercher le type de démarrage du service et, si nécessaire, utilisez la `Set-Service` cmdlet pour modifier le type de démarrage du service.
- Certains services, tels le service Journaux et alertes de performance (Sysmonlog), s'arrêtent automatiquement lorsqu'ils n'ont aucune tâche à exécuter. Lorsque PowerShell démarre un service qui s’arrête presque immédiatement, il affiche le message suivant : `Service \<display-name\> start failed.`

## LIENS CONNEXES

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)
