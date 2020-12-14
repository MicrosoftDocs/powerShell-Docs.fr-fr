---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/08/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-modulemanifest?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-ModuleManifest
ms.openlocfilehash: f5dc6d086f609b5a3f82a035c3ac5c7433e8d236
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891698"
---
# Update-ModuleManifest

## SYNOPSIS
Met à jour un fichier manifeste de module.

## SYNTAXE

### Tous

```
Update-ModuleManifest [-Path] <String> [-NestedModules <Object[]>] [-Guid <Guid>] [-Author <String>]
 [-CompanyName <String>] [-Copyright <String>] [-RootModule <String>] [-ModuleVersion <Version>]
 [-Description <String>] [-ProcessorArchitecture <ProcessorArchitecture>]
 [-CompatiblePSEditions <String[]>] [-PowerShellVersion <Version>] [-ClrVersion <Version>]
 [-DotNetFrameworkVersion <Version>] [-PowerShellHostName <String>]
 [-PowerShellHostVersion <Version>] [-RequiredModules <Object[]>] [-TypesToProcess <String[]>]
 [-FormatsToProcess <String[]>] [-ScriptsToProcess <String[]>] [-RequiredAssemblies <String[]>]
 [-FileList <String[]>] [-ModuleList <Object[]>] [-FunctionsToExport <String[]>]
 [-AliasesToExport <String[]>] [-VariablesToExport <String[]>] [-CmdletsToExport <String[]>]
 [-DscResourcesToExport <String[]>] [-PrivateData <Hashtable>] [-Tags <String[]>]
 [-ProjectUri <Uri>] [-LicenseUri <Uri>] [-IconUri <Uri>] [-ReleaseNotes <String[]>]
 [-Prerelease <String>] [-HelpInfoUri <Uri>] [-PassThru] [-DefaultCommandPrefix <String>]
 [-ExternalModuleDependencies <String[]>] [-PackageManagementProviders <String[]>]
 [-RequireLicenseAcceptance] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Update-ModuleManifest` applet de commande met à jour un fichier manifeste de module ( `.psd1` ).

## EXEMPLES

### Exemple 1 : mettre à jour un manifeste de module

Cet exemple met à jour un fichier manifeste de module existant. La projection est utilisée pour passer des valeurs de paramètre à `Update-ModuleManifest` . Pour plus d’informations, consultez [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).

```powershell
$Parms = @{
  Path = "C:\Test\TestManifest.psd1"
  Author = "TestUser1"
  CompanyName = "Contoso Corporation"
  Copyright = "(c) 2019 Contoso Corporation. All rights reserved."
}

Update-ModuleManifest @Parms
```

`$Parms` est un se terminant par qui stocke les valeurs de paramètre pour **path**, **Author**, **CompanyName** et **Copyright**. `Update-ModuleManifest` Obtient les valeurs de paramètre à partir de `@Parms` et met à jour le manifeste de module, **TestManifest.psd1**.

## PARAMETERS

### -AliasesToExport

Spécifie les alias exportés par le module. Les caractères génériques sont autorisés.

Utilisez ce paramètre pour limiter les alias exportés par le module. **AliasesToExport** peut supprimer des alias de la liste des alias exportés, mais il ne peut pas ajouter d’alias à la liste.

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

### -Auteur

Spécifie l'auteur du module.

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

### -ClrVersion

Spécifie la version minimale du Common Language Runtime (CLR) de Microsoft .NET Framework dont le module a besoin.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CmdletsToExport

Spécifie les applets de commande exportées par le module. Les caractères génériques sont autorisés.

Utilisez ce paramètre pour limiter les applets de commande exportées par le module. **CmdletsToExport** peut supprimer des applets de commande de la liste des applets de commande exportées, mais il ne peut pas ajouter d’applets de commande à la liste.

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

### -CompanyName

Spécifie la société ou le fournisseur qui a créé le module.

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

### -CompatiblePSEditions

Spécifie le **des éditions PS** compatible du module. Pour plus d’informations sur **PSEdition**, consultez [modules avec des éditions PowerShell compatibles](/powershell/scripting/gallery/concepts/module-psedition-support).

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Desktop, Core

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Vous invite à confirmer l’exécution `Update-ModuleManifest` .

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

### -Copyright

Spécifie une déclaration de copyright pour le module.

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

### -DefaultCommandPrefix

Spécifie le préfixe de commande par défaut.

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

Spécifie une description du module.

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

### -DotNetFrameworkVersion

Spécifie la version minimale de Microsoft .NET Framework dont le module a besoin.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DscResourcesToExport

Spécifie les ressources de configuration d’état souhaité (DSC) exportées par le module. Les caractères génériques sont autorisés.

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

### -ExternalModuleDependencies

Spécifie un tableau de dépendances de modules externes.

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

### -FileList

Spécifie tous les éléments qui sont inclus dans le module.

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

### -FormatsToProcess

Spécifie les fichiers de mise en forme ( `.ps1xml` ) qui s’exécutent lors de l’importation du module.

Lorsque vous importez un module, PowerShell exécute l' `Update-FormatData` applet de commande avec les fichiers spécifiés.
Étant donné que les fichiers de mise en forme ne sont pas étendus, ils affectent tous les États de session de la session.

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

### -FunctionsToExport

Spécifie les fonctions exportées par le module. Les caractères génériques sont autorisés.

Utilisez ce paramètre pour limiter les fonctions exportées par le module. **FunctionsToExport** peut supprimer des fonctions de la liste des alias exportés, mais il ne peut pas ajouter de fonctions à la liste.

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

### -Guid

Spécifie un identificateur unique pour le module. Le GUID peut servir à distinguer les modules portant le même nom.

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

### -HelpInfoUri

Spécifie l’adresse Internet du fichier **XML HelpInfo** du module. Entrez un Uniform Resource Identifier (URI) qui commence par **http** ou **https**.

Le fichier **XML HelpInfo** prend en charge la fonctionnalité d’aide actualisable qui a été introduite dans PowerShell version 3,0. Elle contient des informations sur l’emplacement des fichiers d’aide téléchargeables du module et les numéros de version des fichiers d’aide les plus récents pour chaque paramètre régional pris en charge.

Pour plus d’informations sur l’aide actualisable, voir [about_Updatable_Help](../Microsoft.PowerShell.Core/About/about_Updatable_Help.md).
Pour plus d’informations sur le fichier **XML HelpInfo** , consultez [prise en charge de l’aide actualisable](/powershell/scripting/developer/module/supporting-updatable-help).

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IconUri

Spécifie l’URL d’une icône pour le module. L’icône spécifiée est affichée sur la page Web de la Galerie pour le module.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LicenseUri

Spécifie l’URL des termes du contrat de licence pour le module.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModuleList

Spécifie un tableau de modules inclus dans le module.

Entrez le nom de chaque module sous la forme d'une chaîne ou d'une table de hachage avec les clés **ModuleName** et **ModuleVersion**. La table de hachage peut également avoir une clé **GUID** facultative. Vous pouvez combiner des chaînes et des tables de hachage dans la valeur du paramètre.

Cette clé est conçue pour agir en tant qu'inventaire de module. Les modules répertoriés dans la valeur de cette clé ne sont pas traités automatiquement.

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

### -ModuleVersion

Spécifie la version du module.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NestedModules

Spécifie les modules de script ( `.psm1` ) et les modules binaires ( `.dll` ) qui sont importés dans l’état de session du module. Les fichiers de la clé **NestedModules** s’exécutent dans l’ordre dans lequel ils sont listés dans la valeur.

Entrez le nom de chaque module sous la forme d'une chaîne ou d'une table de hachage avec les clés **ModuleName** et **ModuleVersion**. La table de hachage peut également avoir une clé **GUID** facultative. Vous pouvez combiner des chaînes et des tables de hachage dans la valeur du paramètre.

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

### -PackageManagementProviders

Spécifie un tableau de fournisseurs de gestion des packages.

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

### -PassThru

Retourne un objet représentant l’élément que vous utilisez. Par défaut, `Update-ModuleManifest` ne génère pas de sortie.

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

Spécifie le chemin d’accès et le nom de fichier du manifeste de module. Entrez un chemin d’accès et un nom de fichier avec une `.psd1` extension de nom de fichier, par exemple `$PSHOME\Modules\MyModule\MyModule.psd1` .

Si vous spécifiez le chemin d’accès à un fichier existant, `Update-ModuleManifest` remplace le fichier sans avertissement, sauf si le fichier a l’attribut de lecture seule.

Le manifeste doit se trouver dans le répertoire du module, et le nom du fichier manifeste doit être le même que le nom du répertoire du module, mais avec une `.psd1` extension.

Vous ne pouvez pas utiliser de variables, telles que `$PSHOME` ou `$HOME` , en réponse à une invite pour une valeur de paramètre **path** . Pour utiliser une variable, incluez le paramètre **Path** dans la commande.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PowerShellHostName

Spécifie le nom du programme hôte PowerShell requis par le module. Entrez le nom du programme hôte, tel que hôte ISE PowerShell ou ConsoleHost. Les caractères génériques ne sont pas autorisés.

Pour rechercher le nom d’un programme hôte, dans le programme, tapez `$Host.Name` .

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

### -PowerShellHostVersion

Spécifie la version minimale du programme hôte PowerShell qui fonctionne avec le module. Entrez un numéro de version, par exemple 1.1.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PowerShellVersion

Spécifie la version minimale de PowerShell qui fonctionnera avec ce module. Par exemple, vous pouvez spécifier 3,0, 4,0 ou 5,0 comme valeur de ce paramètre.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Version préliminaire

Indique que le module est en version préliminaire.

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

### -PrivateData

Spécifie les données qui sont passées au module lors de son importation.

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

### -ProcessorArchitecture

Spécifie l'architecture de processeur dont le module a besoin.

Les valeurs valides pour ce paramètre sont :

- Amd64
- Arm
- IA64
- MSIL
- Aucun (inconnu ou non spécifié)
- X86

```yaml
Type: System.Reflection.ProcessorArchitecture
Parameter Sets: (All)
Aliases:
Accepted values: None, MSIL, X86, IA64, Amd64, Arm

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProjectUri

Spécifie l’URL d’une page Web sur ce projet.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ReleaseNotes

Spécifie un tableau de chaînes qui contient des notes de publication ou des commentaires que vous souhaitez voir disponibles pour cette version du script.

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

### -RequireLicenseAcceptance

Spécifie qu’une acceptation de licence est requise pour le module.

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

### -RequiredAssemblies

Spécifie les fichiers d’assembly ( `.dll` ) dont le module a besoin. Entrez les noms de fichiers d'assembly.
PowerShell charge les assemblys spécifiés avant de mettre à jour des types ou des formats, d’importer des modules imbriqués ou d’importer le fichier de module spécifié dans la valeur de la clé **RootModule** .

Utilisez ce paramètre pour spécifier tous les assemblys requis par le module, y compris les assemblys qui doivent être chargés pour mettre à jour les fichiers de mise en forme ou de type répertoriés dans les clés **FormatsToProcess** ou **TypesToProcess** , même si ces assemblys sont également répertoriés en tant que modules binaires dans la clé **NestedModules** .

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

### -RequiredModules

Spécifie les modules qui doivent être dans l'état de session global. Si les modules requis ne sont pas dans l’état de session global, PowerShell les importe. Si les modules requis ne sont pas disponibles, la `Import-Module` commande échoue.

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

### -RootModule

Spécifie le fichier principal ou racine du module. Entrez le nom de fichier d’un script ( `.ps1` ), d’un module de script ( `.psm1` ), d’un manifeste de module ( `.psd1` ), d’un assembly ( `.dll` ), d’un fichier XML de définition d’applet de commande ( `.cdxml` ) ou d’un flux de travail ( `.xaml` ). Quand le module est importé, les membres exportés à partir du fichier de module racine sont importés dans l'état de session de l'appelant.

Si un module a un fichier manifeste et qu’aucun fichier racine n’a été spécifié dans la clé **RootModule** , le manifeste devient le fichier primaire pour le module. Et, le module devient un module de manifeste (ModuleType = manifest).

Pour exporter des membres à partir de `.psm1` `.dll` fichiers ou dans un module qui a un manifeste, les noms de ces fichiers doivent être spécifiés dans les valeurs des clés **RootModule** ou **NestedModules** dans le manifeste. Dans le cas contraire, leurs membres ne sont pas exportés.

Dans PowerShell 2,0, cette clé était appelée **ModuleToProcess**.

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

### -ScriptsToProcess

Spécifie les fichiers de script ( `.ps1` ) qui s’exécutent dans l’état de session de l’appelant lors de l’importation du module.
Vous pouvez utiliser ces scripts pour préparer un environnement, tout comme vous pouvez utiliser un script de connexion.

Pour spécifier les scripts qui s'exécutent dans l'état de session du module, utilisez la clé **NestedModules**.

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

### -Tags

Spécifie un tableau de balises.

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

Spécifie les fichiers de type ( `.ps1xml` ) qui s’exécutent lors de l’importation du module.

Lorsque vous importez le module, PowerShell exécute l' `Update-TypeData` applet de commande avec les fichiers spécifiés.
Étant donné que les fichiers de type ne sont pas étendus, ils affectent tous les États de session de la session.

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

### -VariablesToExport

Spécifie les variables exportées par le module. Les caractères génériques sont autorisés.

Utilisez ce paramètre pour limiter les variables exportées par le module. **VariablesToExport** peut supprimer des variables de la liste des variables exportées, mais il ne peut pas ajouter de variables à la liste.

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

### -WhatIf

Montre ce qui se passe si `Update-ModuleManifest` s’exécute. L’applet de commande n’est pas exécutée.

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

### System.String

## SORTIES

### System.Object

## REMARQUES

> [!IMPORTANT]
> Depuis le 2020 avril, le PowerShell Gallery ne prend plus en charge les versions 1,0 et 1,1 du protocole TLS (Transport Layer Security). Si vous n’utilisez pas TLS 1,2 ou une version ultérieure, vous recevrez une erreur lors de la tentative d’accès au PowerShell Gallery. Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1,2 :
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> Pour plus d’informations, consultez l' [annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) dans le blog PowerShell.

## LIENS CONNEXES
