---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-pssession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PSSession
ms.openlocfilehash: c64a59300cdaffe71de04c7843bf644df49530d5
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94390114"
---
# Import-PSSession

## SYNOPSIS
Importe des commandes à partir d'une autre session dans la session active.

## SYNTAXE

```
Import-PSSession [-Prefix <String>] [-DisableNameChecking] [[-CommandName] <String[]>] [-AllowClobber]
 [-ArgumentList <Object[]>] [-CommandType <CommandTypes>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-FormatTypeName] <String[]>]
 [-Certificate <X509Certificate2>] [-Session] <PSSession> [<CommonParameters>]
```

## DESCRIPTION

L' `Import-PSSession` applet de commande importe des commandes, telles que des applets de commande, des fonctions et des alias, à partir d’une session PSSession sur un ordinateur local ou distant dans la session active. Vous pouvez importer n’importe quelle commande que l' `Get-Command` applet de commande peut trouver dans la session PSSession.

Utilisez une `Import-PSSession` commande pour importer des commandes à partir d’un shell personnalisé, tel qu’un shell Microsoft Exchange Server, ou à partir d’une session qui comprend des modules et des composants logiciels enfichables Windows PowerShell ou d’autres éléments qui ne sont pas dans la session active.

Pour importer des commandes, utilisez d’abord l' `New-PSSession` applet de commande pour créer une session PSSession. Utilisez ensuite l' `Import-PSSession` applet de commande pour importer les commandes. Par défaut, `Import-PSSession` importe toutes les commandes, à l’exception des commandes qui ont les mêmes noms que les commandes dans la session active. Pour importer toutes les commandes, utilisez le paramètre **AllowClobber**.

Vous pouvez utiliser des commandes importées comme vous utiliseriez n'importe quelle commande de la session. Quand vous utilisez une commande importée, la partie importée de la commande s'exécute implicitement dans la session à partir de laquelle elle a été importée. Toutefois, les opérations à distance sont gérées entièrement par Windows PowerShell. Vous ne devez même pas vous en rendre compte, sauf que vous devez conserver la connexion à l'autre session (PSSession) ouverte. Si vous la fermez, les commandes importées ne sont plus disponibles.

Étant donné que les commandes importées peuvent durer plus longtemps que les commandes locales, `Import-PSSession` ajoute un paramètre **AsJob** à chaque commande importée. Ce paramètre vous permet d'exécuter la commande en tant que tâche en arrière-plan Windows PowerShell. Pour plus d’informations, consultez [à propos des_tâches](../Microsoft.PowerShell.Core/about/about_Jobs.md).

Lorsque vous utilisez `Import-PSSession` , Windows PowerShell ajoute les commandes importées à un module temporaire qui existe uniquement dans votre session et retourne un objet qui représente le module. Pour créer un module permanent que vous pouvez utiliser dans les sessions ultérieures, utilisez l’applet de commande `Export-PSSession` .

L' `Import-PSSession` applet de commande utilise la fonctionnalité de communication à distance implicite de Windows PowerShell. Lorsque vous importez des commandes dans la session active, elles s’exécutent implicitement dans la session d’origine ou dans une session similaire sur l’ordinateur d’origine.

À compter de Windows PowerShell 3,0, vous pouvez utiliser la `Import-Module` cmdlet pour importer des modules à partir d’une session à distance dans la session active. Cette fonctionnalité utilise la communication à distance implicite. Cela équivaut à utiliser `Import-PSSession` pour importer des modules sélectionnés à partir d’une session à distance dans la session active.

## EXEMPLES

### Exemple 1 : importer toutes les commandes à partir d’une session PSSession

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S
```

Cette commande importe toutes les commandes d'une session PSSession sur l'ordinateur Server01 dans la session active, à l'exception des commandes qui ont le même nom que les commandes dans la session active.

Comme cette commande n'utilise pas le paramètre **CommandName** , elle importe également toutes les données de mise en forme requises pour les commandes importées.

### Exemple 2 : importer des commandes qui se terminent par une chaîne spécifique

```
PS C:\> $S = New-PSSession https://ps.testlabs.com/powershell
PS C:\> Import-PSSession -Session $S -CommandName *-test -FormatTypeName *
PS C:\> New-Test -Name Test1
PS C:\> Get-Test test1 | Run-Test
```

Ces commandes importent les commandes dont les noms se terminent par « -test » à partir d'une session PSSession dans la session locale, puis indiquent comment utiliser une applet de commande importée.

La première commande utilise l' `New-PSSession` applet de commande pour créer une session PSSession. Elle enregistre la session PSSession dans la `$S` variable.

La deuxième commande utilise l' `Import-PSSession` applet de commande pour importer des commandes de la session PSSession dans dans `$S` la session active. Elle utilise le paramètre **CommandName** pour spécifier des commandes avec le nom Test et le paramètre **FormatTypeName** pour importer les données de mise en forme pour les commandes Test.

Les troisième et quatrième commandes utilisent les commandes importées dans la session active. Comme les commandes importées sont en réalité ajoutées à la session active, vous utilisez la syntaxe locale pour les exécuter. Vous n’avez pas besoin d’utiliser l' `Invoke-Command` applet de commande pour exécuter une commande importée.

### Exemple 3 : importer des applets de commande à partir d’une session PSSession

```
PS C:\> $S1 = New-PSSession -ComputerName s1
PS C:\> $S2 = New-PSSession -ComputerName s2
PS C:\> Import-PSSession -Session s1 -Type cmdlet -Name New-Test, Get-Test -FormatTypeName *
PS C:\> Import-PSSession -Session s2 -Type Cmdlet -Name Set-Test -FormatTypeName *
PS C:\> New-Test Test1 | Set-Test -RunType Full
```

Cet exemple montre que vous pouvez utiliser les applets de commande importées comme vous utiliseriez des applets de commande locales.

Ces commandes importent les `New-Test` applets de commande et `Get-Test` à partir d’une session PSSession sur l’ordinateur SERVEUR01 et l' `Set-Test` applet de commande à partir d’une session PSSession sur l’ordinateur Server02.

Même si les applets de commande ont été importées à partir de différentes sessions PSSession, vous pouvez diriger un objet d'une applet de commande vers une autre sans erreur.

### Exemple 4 : exécuter une commande importée en tant que tâche en arrière-plan

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S -CommandName *-test* -FormatTypeName *
PS C:\> $batch = New-Test -Name Batch -AsJob
PS C:\> Receive-Job $batch
```

Cet exemple montre comment exécuter une commande importée en tant que tâche en arrière-plan.

Étant donné que les commandes importées peuvent durer plus longtemps que les commandes locales, `Import-PSSession` ajoute un paramètre **AsJob** à chaque commande importée. Le paramètre **AsJob** vous permet d'exécuter la commande en tant que tâche en arrière-plan.

La première commande crée une session PSSession sur l’ordinateur SERVEUR01 et enregistre l’objet PSSession dans la `$S` variable.

La deuxième commande utilise `Import-PSSession` pour importer les applets de commande de test de la session PSSession dans `$S` dans la session active.

La troisième commande utilise le paramètre **AsJob** de l’applet de commande importée `New-Test` pour exécuter une `New-Test` commande en tant que tâche en arrière-plan. La commande enregistre l’objet de traitement qui `New-Test` retourne dans la `$batch` variable.

La quatrième commande utilise l' `Receive-Job` applet de commande pour obtenir les résultats de la tâche dans la `$batch` variable.

### Exemple 5 : importer des applets de commande et des fonctions à partir d’un module Windows PowerShell

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Invoke-Command -Session $S {Import-Module TestManagement}
PS C:\> Import-PSSession -Session $S -Module TestManagement
```

Cet exemple montre comment importer les applets de commande et fonctions à partir d'un module Windows PowerShell sur un ordinateur distant dans la session active.

La première commande crée une session PSSession sur l’ordinateur SERVEUR01 et l’enregistre dans la `$S` variable.

La deuxième commande utilise l' `Invoke-Command` applet de commande pour exécuter une `Import-Module` commande dans la session PSSession dans `$S` .

En règle générale, le module est ajouté à toutes les sessions par une `Import-Module` commande dans un profil Windows PowerShell, mais les profils ne sont pas exécutés dans sessions PSSession.

La troisième commande utilise le paramètre **module** de `Import-PSSession` pour importer les applets de commande et les fonctions du module dans la session active.

### Exemple 6 : créer un module dans un fichier temporaire

```
PS C:\> Import-PSSession $S -CommandName Get-Date, SearchHelp -FormatTypeName * -AllowClobber

Name              : tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1zunz.ttf
Path              : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1
zunz.ttf\tmp_79468106-4e1d-4d90-af97-1154f9317239_
tcw1zunz.ttf.psm1
Description       : Implicit remoting for http://server01.corp.fabrikam.com/wsman
Guid              : 79468106-4e1d-4d90-af97-1154f9317239
Version           : 1.0
ModuleBase        : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1
zunz.ttf
ModuleType        : Script
PrivateData       : {ImplicitRemoting}
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Get-Date, Get-Date], [SearchHelp, SearchHelp]}
ExportedVariables : {}
NestedModules     : {}
```

Cet exemple montre que `Import-PSSession` crée un module dans un fichier temporaire sur le disque. Il montre également que toutes les commandes sont converties en fonctions avant leur importation dans la session active.

La commande utilise l' `Import-PSSession` applet de commande pour importer une applet de commande `Get-Date` et une fonction SearchHelp dans la session active.

L' `Import-PSSession` applet de commande retourne un objet **PSModuleInfo** qui représente le module temporaire. La valeur de la propriété **path** indique que `Import-PSSession` a créé un fichier de module de script (. psm1) dans un emplacement temporaire. La propriété **ExportedFunctions** montre que l' `Get-Date` applet de commande et la fonction SearchHelp ont été importées en tant que fonctions.

### Exemple 7 : exécuter une commande qui est masquée par une commande importée

```
PS C:\> Import-PSSession $S -CommandName Get-Date -FormatTypeName * -AllowClobber

PS C:\> Get-Command Get-Date -All

CommandType   Name       Definition
-----------   ----       ----------
Function      Get-Date   ...
Cmdlet        Get-Date   Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>]

PS C:\> Get-Date
09074

PS C:\> (Get-Command -Type Cmdlet -Name Get-Date).PSSnapin.Name
Microsoft.PowerShell.Utility

PS C:\> Microsoft.PowerShell.Utility\Get-Date
Sunday, March 15, 2009 2:08:26 PM
```

Cet exemple montre comment exécuter une commande qui est masquée par une commande importée.

La première commande importe une `Get-Date` applet de commande à partir de la session PSSession dans la `$S` variable. Étant donné que la session active comprend une `Get-Date` applet de commande, le paramètre **AllowClobber** est requis dans la commande.

La deuxième commande utilise le paramètre **All** de l' `Get-Command` applet de commande pour récupérer toutes les `Get-Date` commandes dans la session active. La sortie indique que la session comprend l’applet de commande d’origine `Get-Date` et une `Get-Date` fonction. La `Get-Date` fonction exécute l’applet de commande importée `Get-Date` dans la session PSSession dans `$S` .

La troisième commande exécute une `Get-Date` commande. Étant donné que les fonctions sont prioritaires sur les applets de commande, Windows PowerShell exécute la fonction importée `Get-Date` , qui retourne une date julienne.

Les quatrième et cinquième commandes montrent comment utiliser un nom qualifié pour exécuter une commande qui est masquée par une commande importée.

La quatrième commande récupère le nom du composant logiciel enfichable Windows PowerShell qui a ajouté l’applet de commande d’origine `Get-Date` à la session active.

La cinquième commande utilise le nom qualifié du composant logiciel enfichable de l' `Get-Date` applet de commande pour exécuter une `Get-Date` commande.

Pour plus d'informations sur la priorité des commandes et les commandes masquées, consultez [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).

### Exemple 8 : importer des commandes qui ont une chaîne spécifique dans leurs noms

```
PS C:\> Import-PSSession -Session $S -CommandName **Item** -AllowClobber
```

Cette commande importe les commandes dont les noms incluent l’élément de la session PSSession dans `$S` . Étant donné que la commande comprend le paramètre **CommandName** mais pas le paramètre **FormatTypeData** , seule la commande est importée.

Utilisez cette commande lorsque vous utilisez `Import-PSSession` pour exécuter une commande sur un ordinateur distant et que vous avez déjà les données de mise en forme pour la commande dans la session active.

### Exemple 9 : utiliser le paramètre module pour détecter les commandes qui ont été importées dans la session

```
PS C:\> $M = Import-PSSession -Session $S -CommandName *bits* -FormatTypeName *bits*
PS C:\> Get-Command -Module $M
CommandType     Name
-----------     ----
Function        Add-BitsFile
Function        Complete-BitsTransfer
Function        Get-BitsTransfer
Function        Remove-BitsTransfer
Function        Resume-BitsTransfer
Function        Set-BitsTransfer
Function        Start-BitsTransfer
Function        Suspend-BitsTransfer
```

Cette commande montre comment utiliser le paramètre **module** de `Get-Command` pour déterminer les commandes qui ont été importées dans la session par une `Import-PSSession` commande.

La première commande utilise l' `Import-PSSession` applet de commande pour importer des commandes dont les noms incluent « bits » de la session PSSession dans la `$S` variable. La `Import-PSSession` commande retourne un module temporaire et la commande enregistre le module dans la `$m` variable.

La deuxième commande utilise l' `Get-Command` applet de commande pour récupérer les commandes exportées par le module dans la `$M` variable.

Le paramètre **Module** prend une valeur de chaîne, qui est conçue pour le nom du module. Toutefois, quand vous envoyez un objet de module, Windows PowerShell utilise la méthode **ToString** sur l'objet de module, qui retourne le nom du module.

La `Get-Command` commande est l’équivalent de `Get-Command $M.Name` «.

## PARAMÈTRES

### -AllowClobber

Indique que cette applet de commande importe les commandes spécifiées, même si elles ont les mêmes noms que les commandes dans la session active.

Si vous importez une commande portant le même nom qu'une commande dans la session active, la commande importée masque ou remplace les commandes d'origine. Pour plus d’informations, consultez [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).

Par défaut, `Import-PSSession` n’importe pas les commandes qui portent le même nom que les commandes de la session active.

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

### -ArgumentList

Spécifie un tableau de commandes qui résulte de l’utilisation des arguments spécifiés (valeurs de paramètre).

Par exemple, pour importer la variante de la `Get-Item` commande dans le certificat (CERT :) dans la session PSSession dans `$S` , tapez `Import-PSSession -Session $S -Command Get-Item -ArgumentList cert:` .

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Certificat

Spécifie le certificat client utilisé pour signer les fichiers de format (* .Format.ps1XML) ou les fichiers de module de script (. psm1) dans le module temporaire `Import-PSSession` créé par.

Entrez une variable qui contient un certificat, ou bien une commande ou une expression qui obtient le certificat.

Pour rechercher un certificat, utilisez l' `Get-PfxCertificate` applet de commande ou utilisez l' `Get-ChildItem` applet de commande dans le certificat (CERT :) unités. Si le certificat n'est pas valide ou n'a pas une autorité suffisante, la commande échoue.

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CommandName

Spécifie les commandes avec les noms ou modèles de noms spécifiés. Les caractères génériques sont autorisés. Utilisez **CommandName** ou son alias, **Name**.

Par défaut, `Import-PSSession` importe toutes les commandes de la session, à l’exception des commandes qui ont les mêmes noms que les commandes dans la session active. Cela empêche les commandes importées de masquer ou de remplacer des commandes dans la session. Pour importer toutes les commandes, y compris celles qui masquent ou remplacent d'autres commandes, utilisez le paramètre **AllowClobber**.

Si vous utilisez le paramètre **CommandName** , les fichiers de mise en forme pour les commandes ne sont pas importés, sauf si vous utilisez le paramètre **FormatTypeName**. De même, si vous utilisez le paramètre **FormatTypeName** , aucune commande n'est importée, sauf si vous utilisez le paramètre **CommandName**.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CommandType

Spécifie le type d’objets de commande. La valeur par défaut est Cmdlet. Utilisez **CommandType** ou son alias, **Type**. Les valeurs valides pour ce paramètre sont :

- Affecté. Alias Windows PowerShell dans la session à distance.
- Tout le monde. Applets de commande et fonctions dans la session à distance.
- console. Tous les fichiers autres que Windows-PowerShell fichiers dans les chemins d’accès qui sont répertoriés dans la variable d’environnement PATH ( `$env:path` ) dans la session à distance, y compris les fichiers. txt,. exe et. dll.
- PolicySchedule. Applets de commande dans la session à distance. « Cmdlet » est la valeur par défaut.
- ExternalScript. Fichiers. ps1 dans les chemins d’accès figurant dans la variable d’environnement PATH ( `$env:path` ) dans la session à distance.
- Filtre et fonction. Fonctions Windows PowerShell dans la session à distance.
- Script. Blocs de scripts dans la session à distance.

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: Alias, Function, Filter, Cmdlet, ExternalScript, Application, Script, Workflow, Configuration, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisableNameChecking

Indique que cette applet de commande supprime le message qui vous avertit lorsque vous importez une applet de commande ou une fonction dont le nom comprend un verbe non approuvé ou un caractère interdit.

Par défaut, lorsqu’un module que vous importez exporte des applets de commande ou des fonctions qui ont des verbes non approuvés dans leurs noms, Windows PowerShell affiche le message d’avertissement suivant :

"AVERTISSEMENT : certains noms de commandes importés incluent des verbes non approuvés qui peuvent les rendre moins détectables. Utilisez le paramètre Verbose pour plus d’informations ou tapez `Get-Verb` pour afficher la liste des verbes approuvés.»

Ce message n'est qu'un avertissement. Le module entier est toujours importé, y compris les commandes non conformes. Bien que le message soit affiché aux utilisateurs du module, le problème d'affectation de noms doit être corrigé par l'auteur du module.

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

### -FormatTypeName

Spécifie les instructions de mise en forme pour les types d’Microsoft .NET Framework spécifiés.
Entrez les noms des types.
Les caractères génériques sont autorisés.

La valeur de ce paramètre doit être le nom d’un type retourné par une `Get-FormatData` commande dans la session à partir de laquelle les commandes sont importées. Pour récupérer toutes les données de mise en forme dans la session à distance, tapez `*` .

Si la commande n’inclut pas le paramètre **CommandName** ou **FormatTypeName** , `Import-PSSession` importe les instructions de mise en forme pour tous les types de .NET Framework retournés par une `Get-FormatData` commande dans la session à distance.

Si vous utilisez le paramètre **FormatTypeName** , aucune commande n'est importée, sauf si vous utilisez le paramètre **CommandName**.

De même, si vous utilisez le paramètre **CommandName** , les fichiers de mise en forme pour les commandes ne sont pas importés, sauf si vous utilisez le paramètre **FormatTypeName**.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FullyQualifiedModule

Spécifie les modules dont les noms sont spécifiés sous la forme d’objets **ModuleSpecification** (décrits dans la section Notes du [constructeur ModuleSpecification (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_) dans le kit de développement logiciel (SDK) PowerShell. Par exemple, le paramètre **FullyQualifiedModule** accepte un nom de module qui est spécifié au format :

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}` ou
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`.

**ModuleName** et **ModuleVersion** sont obligatoires, mais **Guid** est facultatif.

Vous ne pouvez pas spécifier le paramètre **FullyQualifiedModule** dans la même commande qu’un paramètre **module** . Les deux paramètres s’excluent mutuellement.

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Module

Spécifie et tableau de commandes dans les modules et composants logiciels enfichables Windows PowerShell. Entrez les noms de composant logiciel enfichable et de module. Les caractères génériques ne sont pas autorisés.

`Import-PSSession` Impossible d’importer des fournisseurs à partir d’un composant logiciel enfichable.

Pour plus d'informations, consultez [about_PSSnapins](/powershell/module/Microsoft.PowerShell.Core/About/about_PSSnapins) et [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Prefix

Spécifie un préfixe pour les noms des commandes importées.

Utilisez ce paramètre pour éviter les conflits de noms qui peuvent se produire quand des commandes différentes dans la session ont le même nom.

Par exemple, si vous spécifiez le préfixe Remote, puis importez une applet de commande `Get-Date` , l’applet de commande est connue dans la session en tant que `Get-RemoteDate` , et elle n’est pas confondue avec l’applet de commande d’origine `Get-Date` .

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

### -Session

Spécifie la **session PSSession** à partir de laquelle les applets de commande sont importées. Entrez une variable qui contient un objet de session ou une commande qui obtient un objet de session, tel qu’une `New-PSSession` `Get-PSSession` commande ou. Vous ne pouvez spécifier qu'une seule session. Ce paramètre est obligatoire.

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas rediriger des objets vers cette applet de commande.

## SORTIES

### System. Management. Automation. PSModuleInfo

`Import-PSSession` retourne le même objet de module que les `New-Module` applets de commande et `Get-Module` retournent.
Toutefois, le module importé est temporaire et existe uniquement dans la session active. Pour créer un module permanent sur le disque, utilisez l’applet de commande `Export-PSSession` .

## REMARQUES

- `Import-PSSession` s’appuie sur l’infrastructure de communication à distance PowerShell. Pour utiliser cette applet de commande, l'ordinateur doit être configuré pour la communication à distance WS-Management. Pour plus d’informations, consultez [about_Remote](../Microsoft.PowerShell.Core/about/about_Remote.md) et [about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md).
- `Import-PSSession` n’importe pas les variables ou les fournisseurs PowerShell.
- Quand vous importez des commandes qui ont le même nom que les commandes dans la session active, les commandes importées peuvent masquer des alias, des fonctions et des applets de commande dans la session, et peuvent remplacer des fonctions et variables dans la session. Pour éviter les conflits de noms, utilisez le paramètre **Prefix**. Pour plus d’informations, consultez [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).
- `Import-PSSession` convertit toutes les commandes en fonctions avant de les importer. Par conséquent, les commandes importées se comportent un peu différemment que si elles avaient conservé leur type de commande d'origine. Par exemple, si vous importez une applet de commande à partir d'une session PSSession, puis une applet de commande avec le même nom à partir d'un module ou d'un composant logiciel enfichable, l'applet de commande qui est importée à partir de la session PSSession s'exécute toujours par défaut, car les fonctions sont prioritaires sur les applets de commande. À l'inverse, si vous importez un alias dans une session qui a un alias avec le même nom, l'alias d'origine est toujours utilisé, car les alias sont prioritaires sur les fonctions. Pour plus d’informations, consultez [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).
- `Import-PSSession` utilise l' `Write-Progress` applet de commande pour afficher la progression de la commande. Vous pouvez voir la barre de progression pendant l'exécution de la commande.
- Pour rechercher les commandes à importer, `Import-PSSession` utilise l' `Invoke-Command` applet de commande pour exécuter une `Get-Command` commande dans la session PSSession. Pour obtenir des données de mise en forme pour les commandes, elle utilise l’applet de commande `Get-FormatData` . Vous pouvez voir des messages d’erreur de ces applets de commande lorsque vous exécutez une `Import-PSSession` commande. En outre, `Import-PSSession` ne peut pas importer de commandes à partir d’une session PSSession qui n’inclut pas les `Get-Command` applets de commande, `Get-FormatData` , `Select-Object` et `Get-Help` .
- Les commandes importées présentent les mêmes restrictions que d'autres commandes à distance, notamment l'impossibilité de démarrer un programme avec une interface utilisateur, tel que le Bloc-notes.
- Étant donné que les profils Windows PowerShell ne sont pas exécutés dans sessions PSSession, les commandes qu’un profil ajoute à une session ne sont pas disponibles pour `Import-PSSession` . Pour importer des commandes à partir d’un profil, utilisez une `Invoke-Command` commande pour exécuter le profil dans la session PSSession manuellement avant d’importer des commandes.
- Le module temporaire que `Import-PSSession` crée peut inclure un fichier de mise en forme, même si la commande n’importe pas de données de mise en forme. Si la commande n'importe pas de données de mise en forme, les fichiers de mise en forme éventuellement créés ne contiennent pas de données de mise en forme.
- Pour utiliser `Import-PSSession` , la stratégie d’exécution dans la session active ne peut pas être restreinte ou AllSigned, car le module temporaire qui `Import-PSSession` crée contient des fichiers de script non signés interdits par ces stratégies. Pour utiliser `Import-PSSession` sans modifier la stratégie d’exécution de l’ordinateur local, utilisez le paramètre **scope** de `Set-ExecutionPolicy` pour définir une stratégie d’exécution moins restrictive pour un seul processus.
- Dans Windows PowerShell 2.0, les rubriques d'aide pour les commandes qui sont importées à partir d'une autre session n'incluent pas le préfixe que vous attribuez à l'aide du paramètre **Prefix**. Pour obtenir de l'aide pour une commande importée dans Windows PowerShell 2.0, utilisez le nom de commande (sans préfixe) d'origine.

## LIENS CONNEXES

[Export-PSSession](Export-PSSession.md)
