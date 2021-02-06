---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-itemproperty?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ItemProperty
ms.openlocfilehash: 18383dc2b1e018e56864e412dfe75eca2b578a08
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596520"
---
# Set-ItemProperty

## SYNOPSIS
Crée ou modifie la valeur d'une propriété d'un élément.

## SYNTAXE

### propertyValuePathSet (par défaut)

```
Set-ItemProperty [-Path] <String[]> [-Name] <String> [-Value] <Object> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-Type <RegistryValueKind>] [<CommonParameters>]
```

### propertyPSObjectPathSet

```
Set-ItemProperty [-Path] <String[]> -InputObject <PSObject> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-Type <RegistryValueKind>] [<CommonParameters>]
```

### propertyValueLiteralPathSet

```
Set-ItemProperty -LiteralPath <String[]> [-Name] <String> [-Value] <Object> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-Type <RegistryValueKind>] [<CommonParameters>]
```

### propertyPSObjectLiteralPathSet

```
Set-ItemProperty -LiteralPath <String[]> -InputObject <PSObject> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-Type <RegistryValueKind>] [<CommonParameters>]
```

## Description

L' `Set-ItemProperty` applet de commande modifie la valeur de la propriété de l’élément spécifié.
Vous pouvez utiliser cette applet de commande pour définir ou modifier les propriétés d'éléments.
Par exemple, vous pouvez utiliser `Set-ItemProperty` pour définir la valeur de la propriété **IsReadOnly** d’un objet fichier sur `$True` .

Vous pouvez également utiliser `Set-ItemProperty` pour créer et modifier les valeurs de Registre et les données.
Par exemple, vous pouvez ajouter une nouvelle entrée de Registre à une clé, puis définir ou modifier sa valeur.

## EXEMPLES

### Exemple 1 : définir une propriété d’un fichier

Cette commande affecte la valeur « true » à la propriété **IsReadOnly** du fichier « final.doc ».
Elle utilise **path** pour spécifier le fichier, **Name** pour spécifier le nom de la propriété et le paramètre **value** pour spécifier la nouvelle valeur.

Le fichier est un objet **System. IO. FileInfo** et **IsReadOnly** est simplement l’une de ses propriétés.
Pour afficher toutes les propriétés, tapez `Get-Item C:\GroupFiles\final.doc | Get-Member -MemberType
Property` .

La `$true` variable automatique représente une valeur « true ».
Pour plus d’informations, consultez [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).

```powershell
Set-ItemProperty -Path C:\GroupFiles\final.doc -Name IsReadOnly -Value $true
```

### Exemple 2 : créer une entrée et une valeur de Registre

Cet exemple montre comment utiliser `Set-ItemProperty` pour créer une nouvelle entrée de Registre et affecter une valeur à l’entrée. Il crée l’entrée « NoOfEmployees » dans la clé « ContosoCompany » dans la `HKLM\Software` clé et définit sa valeur sur 823.

Étant donné que les entrées de Registre sont considérées comme des propriétés des clés de Registre, qui sont des éléments, vous utilisez `Set-ItemProperty` pour créer des entrées de Registre et pour définir et modifier leurs valeurs.

```powershell
Set-ItemProperty -Path "HKLM:\Software\ContosoCompany" -Name "NoOfEmployees" -Value 823
Get-ItemProperty -Path "HKLM:\Software\ContosoCompany"
```

```Output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\contosocompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : contosocompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 823
```

```powershell
Set-ItemProperty -Path "HKLM:\Software\ContosoCompany" -Name "NoOfEmployees" -Value 824
Get-ItemProperty -Path "HKLM:\Software\ContosoCompany"
```

```Output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\contosocompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : contosocompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 824
```

La première commande crée l’entrée de registre.
Elle utilise **path** pour spécifier le chemin d’accès du `HKLM:` lecteur et la clé « Software\MyCompany. ».
La commande utilise **Name** pour spécifier le nom et la **valeur** de l’entrée pour spécifier une valeur.

La deuxième commande utilise l' `Get-ItemProperty` applet de commande pour afficher la nouvelle entrée de registre.
Si vous utilisez les `Get-Item` applets de commande ou `Get-ChildItem` , les entrées ne s’affichent pas, car il s’agit des propriétés d’une clé, et non des éléments ou des éléments enfants.

La troisième commande modifie la valeur de l’entrée **NoOfEmployees** en 824.

Vous pouvez également utiliser l' `New-ItemProperty` applet de commande pour créer l’entrée de Registre et sa valeur, puis utiliser `Set-ItemProperty` pour modifier la valeur.

Pour plus d’informations sur le `HKLM:` lecteur, tapez `Get-Help Get-PSDrive` .
Pour plus d’informations sur l’utilisation de PowerShell pour gérer le registre, tapez `Get-Help Registry` .

### Exemple 3 : modifier un élément à l’aide du pipeline

Ces commandes montrent comment utiliser un opérateur de pipeline ( `|` ) pour envoyer un élément à `Set-ItemProperty` .

La première partie de la commande utilise `Get-ChildItem` pour récupérer un objet qui représente le fichier « Weekly.txt ». La commande utilise un opérateur de pipeline auquel envoyer l’objet fichier `Set-ItemProperty` .
La `Set-ItemProperty` commande utilise les paramètres **Name** et **value** pour spécifier la propriété et sa nouvelle valeur.

Cette commande revient à utiliser le paramètre **InputObject** pour spécifier l’objet qui `Get-ChildItem` obtient.

```powershell
Get-ChildItem weekly.txt | Set-ItemProperty -Name IsReadOnly -Value $True
```

## PARAMETERS

### -Credential

> [!NOTE]
> Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.
> Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Exclude

Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération. La valeur de ce paramètre qualifie le paramètre **Path**. Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` . Les caractères génériques sont autorisés. Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.

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

### -Filter

Spécifie un filtre pour qualifier le paramètre **path** . Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres. Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).
Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Force

Force l’applet de commande à définir une propriété sur des éléments qui, sinon, ne sont pas accessibles par l’utilisateur.
L'implémentation est différente d'un fournisseur à l'autre.
Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

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

### -Include

Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération. La valeur de ce paramètre qualifie le paramètre **Path**. Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` . Les caractères génériques sont autorisés. Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.

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

Spécifie l’objet qui a les propriétés modifiées par cette applet de commande.
Entrez une variable qui contient l'objet ou tapez une commande permettant d'obtenir cet objet.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: propertyPSObjectPathSet, propertyPSObjectLiteralPathSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Spécifie un chemin d’accès à un ou plusieurs emplacements. La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).

```yaml
Type: System.String[]
Parameter Sets: propertyValueLiteralPathSet, propertyPSObjectLiteralPathSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Spécifie le nom de la propriété.

```yaml
Type: System.String
Parameter Sets: propertyValuePathSet, propertyValueLiteralPathSet
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

Retourne un objet qui représente la propriété de l’élément.
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

### -Path

Spécifie le chemin d’accès des éléments avec la propriété à modifier.
Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: propertyValuePathSet, propertyPSObjectPathSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Type

Le **type** est un paramètre dynamique que le fournisseur du Registre ajoute à l’applet de commande `Set-ItemProperty` .
Ce paramètre fonctionne uniquement dans les lecteurs de registre.

Spécifie le type de propriété que cette applet de commande ajoute.
Les valeurs valides pour ce paramètre sont :

- **String**: spécifie une chaîne terminée par le caractère null. Équivalent à **REG_SZ**.
- **ExpandString**: spécifie une chaîne terminée par le caractère null qui contient des références non développées à des variables d’environnement qui sont développées lorsque la valeur est récupérée. Équivalent à **REG_EXPAND_SZ**.
- **Binary**: spécifie des données binaires sous n’importe quelle forme. Équivalent à **REG_BINARY**.
- **DWORD**: spécifie un nombre binaire de 32 bits. Équivalent à **REG_DWORD**.
- **MultiString**: spécifie un tableau de chaînes terminées par le caractère null qui se sont terminées par deux caractères null.
  Équivalent à **REG_MULTI_SZ**.
- **QWord**: spécifie un nombre binaire de 64 bits. Équivalent à **REG_QWORD**.
- **Inconnu**: indique un type de données de Registre non pris en charge, tel que **REG_RESOURCE_LIST**.

```yaml
Type: Microsoft.Win32.RegistryValueKind
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Value

Spécifie la valeur de la propriété.

```yaml
Type: System.Object
Parameter Sets: propertyValuePathSet, propertyValueLiteralPathSet
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
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

Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` . Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System. Management. Automation. PSObject

Vous pouvez diriger les objets vers cette applet de commande.

## SORTIES

### Aucun, System. Management. Automation. PSCustomObject

Cette applet de commande génère un objet **PSCustomObject** qui représente l’élément qui a été modifié et sa nouvelle valeur de propriété, si vous spécifiez le paramètre **PassThru** .
Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

`Set-ItemProperty` est conçu pour fonctionner avec les données exposées par n’importe quel fournisseur. Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` . Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## LIENS CONNEXES

[Clear-ItemProperty](Clear-ItemProperty.md)

[Copy-ItemProperty](Copy-ItemProperty.md)

[Get-ItemProperty](Get-ItemProperty.md)

[Move-ItemProperty](Move-ItemProperty.md)

[New-ItemProperty](New-ItemProperty.md)

[Remove-ItemProperty](Remove-ItemProperty.md)

[Rename-ItemProperty](Rename-ItemProperty.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

