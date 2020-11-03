---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSRoleCapabilityFile
ms.openlocfilehash: 3dca5f922f31690bb78ccc610b4ed44b7423ca47
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202714"
---
# New-PSRoleCapabilityFile

## SYNOPSIS
Crée un fichier qui définit un ensemble de fonctionnalités à exposer par le biais d’une configuration de session.

## SYNTAX

```
New-PSRoleCapabilityFile [-Path] <String> [-Guid <Guid>] [-Author <String>] [-Description <String>]
 [-CompanyName <String>] [-Copyright <String>] [-ModulesToImport <Object[]>] [-VisibleAliases <String[]>]
 [-VisibleCmdlets <Object[]>] [-VisibleFunctions <Object[]>] [-VisibleExternalCommands <String[]>]
 [-VisibleProviders <String[]>] [-ScriptsToProcess <String[]>] [-AliasDefinitions <IDictionary[]>]
 [-FunctionDefinitions <IDictionary[]>] [-VariableDefinitions <Object>] [-EnvironmentVariables <IDictionary>]
 [-TypesToProcess <String[]>] [-FormatsToProcess <String[]>] [-AssembliesToLoad <String[]>]
 [<CommonParameters>]
```

## Description

L' `New-PSRoleCapabilityFile` applet de commande crée un fichier qui définit un ensemble de fonctionnalités utilisateur qui peuvent être exposées par le biais de fichiers de configuration de session. Cela comprend la détermination des applets de commande, des fonctions et des scripts disponibles pour les utilisateurs. Le fichier de capacité est un fichier texte lisible qui contient une table de hachage des propriétés et des valeurs de configuration de session. Le fichier a une extension de nom de fichier. PSRC et peut être utilisé par plusieurs configurations de session.

Tous les paramètres de `New-PSRoleCapabilityFile` sont facultatifs, à l’exception du paramètre **path** , qui spécifie le chemin d’accès au fichier pour le fichier. Si vous n’incluez pas de paramètre lorsque vous exécutez l’applet de commande, la clé correspondante dans le fichier de configuration de session est commentée, sauf indication contraire dans la description du paramètre. Par exemple, si vous n’incluez pas le paramètre **AssembliesToLoad** , cette section du fichier de configuration de session est commentée.

Pour utiliser le fichier de capacité de rôle dans une configuration de session, placez d’abord le fichier dans un sous-dossier **RoleCapabilities** d’un dossier de module PowerShell valide. Ensuite, référencez le fichier par nom dans le champ **RoleDefinitions** dans un fichier de configuration de session PowerShell (. PSSC).

Cette applet de commande a été introduite dans Windows PowerShell 5,0.

## EXEMPLES

### Exemple 1 : créer un fichier de capacité de rôle vide

Cet exemple crée un fichier de capacité de rôle qui utilise les valeurs par défaut (vides). Le fichier peut ensuite être modifié dans un éditeur de texte pour modifier ces paramètres de configuration.

```powershell
New-PSRoleCapabilityFile -Path ".\ExampleFile.psrc"
```

### Exemple 2 : créer un fichier de capacité de rôle permettant aux utilisateurs de redémarrer les services et tout ordinateur VDI

Cet exemple crée un exemple de fichier de capacité de rôle qui permet aux utilisateurs de redémarrer des services et des ordinateurs qui correspondent à un modèle de nom spécifique. Le filtrage de nom est défini en définissant le paramètre **ValidatePattern** sur l’expression régulière `VDI\d+` .

```powershell
$roleParameters = @{
    Path = ".\Maintenance.psrc"
    Author = "User01"
    CompanyName = "Fabrikam Corporation"
    Description = "This role enables users to restart any service and restart any VDI computer."
    ModulesToImport = "Microsoft.PowerShell.Core"
    VisibleCmdlets = "Restart-Service", @{
                      Name = "Restart-Computer"
                      Parameters = @{ Name = "ComputerName"; ValidatePattern = "VDI\d+" }
    }
}
New-PSRoleCapabilityFile @roleParameters
```

## PARAMETERS

### -AliasDefinitions

Ajoute les alias spécifiés aux sessions qui utilisent le fichier de capacité de rôle. Entrez une table de hachage avec les clés suivantes :

- Nom. Nom de l'alias. Cette clé est obligatoire.
- Valeur. Commande représentée par l'alias. Cette clé est obligatoire.
- Description. Chaîne de texte qui décrit l'alias. Cette clé est facultative.
- Options. Options de l'alias. Cette clé est facultative. La valeur par défaut est Aucun. Les valeurs acceptables pour ce paramètre sont : None, ReadOnly, constant, Private ou options AllScope.

Par exemple : `@{Name="hlp";Value="Get-Help";Description="Gets help";Options="ReadOnly"}`

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AssembliesToLoad

Spécifie les assemblys à charger dans les sessions qui utilisent le fichier de capacité de rôle.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Auteur

Spécifie l’utilisateur qui a créé le fichier de capacité de rôle.

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

### -CompanyName

Identifie la société qui a créé le fichier de capacité de rôle.
La valeur par défaut est Unknown.

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

### -Copyright

Spécifie un copyright pour le fichier de capacité de rôle. Si vous omettez ce paramètre, `New-PSRoleCapabilityFile` génère une déclaration de droits d’auteur à l’aide de la valeur du paramètre **auteur** .

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

### Description

Spécifie une description pour le fichier de capacité de rôle.

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

### -EnvironmentVariables

Spécifie les variables d’environnement pour les sessions qui exposent ce fichier de capacités de rôle. Entrez une table de hachage dans laquelle les clés sont les noms des variables d'environnement, et les valeurs sont les valeurs des variables d'environnement.

Par exemple : `EnvironmentVariables=@{TestShare="\\\\Server01\TestShare"}`

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FormatsToProcess

Spécifie les fichiers de mise en forme (. ps1xml) qui s’exécutent dans les sessions qui utilisent le fichier de capacité de rôle. La valeur de ce paramètre doit être un chemin d’accès complet ou absolu des fichiers de mise en forme.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FunctionDefinitions

Ajoute les fonctions spécifiées aux sessions qui exposent la capacité de rôle. Entrez une table de hachage avec les clés suivantes :

- Nom. Nom de la fonction. Cette clé est obligatoire.
- ScriptBlock. Corps de la fonction. Entrez un bloc de script. Cette clé est obligatoire.
- Options. Options de la fonction. Cette clé est facultative. La valeur par défaut est Aucun. Les valeurs acceptables pour ce paramètre sont les suivantes : None, ReadOnly, constant, Private ou options AllScope.

Par exemple :

`@{Name="Get-PowerShellProcess";ScriptBlock={Get-Process PowerShell};Options="AllScope"}`

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Guid

Spécifie un identificateur unique pour le fichier de capacité de rôle. Si vous omettez ce paramètre, `New-PSRoleCapabilityFile` génère un GUID pour le fichier. Pour créer un nouveau GUID dans PowerShell, tapez `[guid]::NewGuid()` .

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModulesToImport

Spécifie les modules qui sont importés automatiquement dans des sessions qui utilisent le fichier de capacité de rôle. Par défaut, toutes les commandes dans les modules répertoriés sont visibles. En cas d’utilisation avec **VisibleCmdlets** ou **VisibleFunctions** , les commandes visibles à partir des modules spécifiés peuvent être restreintes.

Chaque module utilisé dans la valeur de ce paramètre peut être représenté par une chaîne ou par une table de hachage. Une chaîne de module se compose uniquement du nom du module. Une table de hachage de module peut inclure des clés **modulename** , **ModuleVersion** et **GUID** . Seule la clé **ModuleName** est obligatoire.

Par exemple, la valeur suivante se compose d'une chaîne et d'une table de hachage. Toutes les combinaisons de chaînes et de tables de hachage, dans n'importe quel ordre, sont valides.

`"TroubleshootingPack", @{ModuleName="PSDiagnostics"; ModuleVersion="1.0.0.0";GUID="c61d6278-02a3-4618-ae37-a524d40a7f44"}`

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Spécifie le chemin d’accès et le nom du fichier de capacité du rôle. Le fichier doit avoir une `.psrc` extension de nom de fichier.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptsToProcess

Spécifie les scripts à ajouter aux sessions qui utilisent le fichier de capacité de rôle. Entrez le chemin d'accès et les noms de fichiers des scripts. La valeur de ce paramètre doit être un chemin d’accès complet ou absolu des noms de fichiers de script.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypesToProcess

Spécifie les fichiers de type (. ps1xml) à ajouter aux sessions qui utilisent le fichier de capacité de rôle. Entrez les noms de fichiers de type. La valeur de ce paramètre doit être un chemin d’accès complet ou absolu des noms de fichiers de type.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VariableDefinitions

Spécifie des variables à ajouter aux sessions qui utilisent le fichier de capacité de rôle. Entrez une table de hachage avec les clés suivantes :

- Nom. Nom de la variable. Cette clé est obligatoire.
- Valeur. Valeur de la variable. Cette clé est obligatoire.
- Options. Options de la variable. Cette clé est facultative. La valeur par défaut est Aucun. Les valeurs acceptables pour ce paramètre sont les suivantes : None, ReadOnly, constant, Private ou options AllScope.

Par exemple : `@{Name="WarningPreference";Value="SilentlyContinue";Options="AllScope"}`

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VisibleAliases

Limite les alias de la session à ceux spécifiés dans la valeur de ce paramètre, ainsi qu’à tous les alias que vous définissez dans le paramètre **AliasDefinition** . Les caractères génériques sont pris en charge.
Par défaut, tous les alias définis par le moteur PowerShell et tous les alias que les modules exportent sont visibles dans la session.

Par exemple, pour limiter les alias disponibles à GM et GCM, utilisez la syntaxe suivante : `VisibleAliases="gcm", "gp"`

Lorsqu’un paramètre **visible** est inclus dans le fichier de capacité de rôle, PowerShell supprime l' `Import-Module` applet de commande et son `ipmo` alias de la session.

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

### -VisibleCmdlets

Limite les applets de commande de la session à celles spécifiées dans la valeur de ce paramètre. Les caractères génériques et les noms de module qualifiés sont pris en charge.

Par défaut, toutes les applets de commande que les modules de la session exportent sont visibles dans la session. Utilisez les paramètres **SessionType** et **ModulesToImport** pour déterminer quels modules et composants logiciels enfichables sont importés dans la session. Si aucun module dans **ModulesToImport** n’expose l’applet de commande, `New-PSRoleCapabilityFile` tente de charger le module approprié.

Quand un paramètre **visible** est inclus dans le fichier de configuration de session, PowerShell supprime l' `Import-Module` applet de commande et son `ipmo` alias de la session.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -VisibleExternalCommands

Limite les fichiers binaires externes, les scripts et les commandes qui peuvent être exécutés dans la session à ceux spécifiés dans la valeur de ce paramètre.

Par défaut, aucune commande externe n’est visible dans cette session.

Quand un paramètre **visible** est inclus dans le fichier de configuration de session, PowerShell supprime l' `Import-Module` applet de commande et son `ipmo` alias de la session.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VisibleFunctions

Limite les fonctions de la session à celles spécifiées dans la valeur de ce paramètre, ainsi qu’à toutes les fonctions que vous définissez dans le paramètre **FunctionDefinitions** . Les caractères génériques sont pris en charge.

Par défaut, toutes les fonctions exportées par les modules de la session sont visibles dans cette session. Utilisez les paramètres **SessionType** et **ModulesToImport** pour déterminer les modules qui sont importés dans la session.

Quand un paramètre **visible** est inclus dans le fichier de configuration de session, PowerShell supprime l' `Import-Module` applet de commande et son `ipmo` alias de la session.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -VisibleProviders

Limite les fournisseurs PowerShell dans la session à ceux spécifiés dans la valeur de ce paramètre.
Les caractères génériques sont pris en charge.

Par défaut, tous les fournisseurs exportés par un module dans la session sont visibles dans la session. Utilisez les paramètres **SessionType** et **ModulesToImport** pour déterminer les modules qui sont importés dans la session.

Quand un paramètre **visible** est inclus dans le fichier de configuration de session, PowerShell supprime l' `Import-Module` applet de commande et son `ipmo` alias de la session.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

## SORTIES

## REMARQUES

## LIENS CONNEXES

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[Get-PSSessionCapability](Get-PSSessionCapability.md)
