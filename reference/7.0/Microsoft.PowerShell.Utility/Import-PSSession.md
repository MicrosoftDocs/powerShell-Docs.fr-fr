---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-pssession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PSSession
ms.openlocfilehash: fafc4da46eb6b6f7cf252d5ca2aa50f6bd42b49f
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201181"
---
# Import-PSSession

## SYNOPSIS
Importe des commandes à partir d'une autre session dans la session active.

## SYNTAX

```
Import-PSSession [-Prefix <String>] [-DisableNameChecking] [[-CommandName] <String[]>] [-AllowClobber]
 [-ArgumentList <Object[]>] [-CommandType <CommandTypes>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-FormatTypeName] <String[]>]
 [-Certificate <X509Certificate2>] [-Session] <PSSession> [<CommonParameters>]
```

## Description

L’applet de commande **Import-PSSession** importe des commandes, telles que des applets de commande, des fonctions et des alias, à partir d’une session PSSession sur un ordinateur local ou distant dans la session active.
Vous pouvez importer n’importe quelle commande que l’applet de commande Get-Command peut trouver dans la session PSSession.

Utilisez une commande **Import-PSSession** pour importer des commandes à partir d’un shell personnalisé, tel qu’un shell Microsoft Exchange Server, ou à partir d’une session qui comprend des modules et des composants logiciels enfichables PowerShell ou d’autres éléments qui ne sont pas dans la session active.

Pour importer des commandes, utilisez d’abord l’applet de commande New-PSSession pour créer une session PSSession.
Utilisez ensuite l'applet de commande **Import-PSSession** pour importer les commandes.
Par défaut, **Import-PSSession** importe toutes les commandes à l'exception de celles qui ont le même nom que les commandes dans la session active.
Pour importer toutes les commandes, utilisez le paramètre *AllowClobber* .

Vous pouvez utiliser des commandes importées comme vous utiliseriez n'importe quelle commande de la session.
Quand vous utilisez une commande importée, la partie importée de la commande s'exécute implicitement dans la session à partir de laquelle elle a été importée.
Toutefois, les opérations à distance sont gérées entièrement par PowerShell.
Vous ne devez même pas vous en rendre compte, sauf que vous devez conserver la connexion à l'autre session (PSSession) ouverte.
Si vous la fermez, les commandes importées ne sont plus disponibles.

Comme l'exécution des commandes importées peut prendre plus de temps que celle des commandes locales, **Import-PSSession** ajoute un paramètre *AsJob* à chaque commande importée.
Ce paramètre vous permet d’exécuter la commande en tant que tâche en arrière-plan PowerShell.
Pour plus d'informations, consultez about_Jobs.

Quand vous utilisez **Import-PSSession** , PowerShell ajoute les commandes importées à un module temporaire qui existe uniquement dans votre session et retourne un objet qui représente le module.
Pour créer un module permanent que vous pouvez utiliser dans les sessions ultérieures, utilisez l’applet de commande Export-PSSession.

L’applet de commande **Import-PSSession** utilise la fonctionnalité de communication à distance implicite de PowerShell.
Lorsque vous importez des commandes dans la session active, elles s’exécutent implicitement dans la session d’origine ou dans une session similaire sur l’ordinateur d’origine.

À compter de Windows PowerShell 3,0, vous pouvez utiliser l’applet de commande Import-Module pour importer des modules à partir d’une session à distance dans la session active.
Cette fonctionnalité utilise la communication à distance implicite.
Elle revient à utiliser **Import-PSSession** pour importer les modules sélectionnés à partir d'une session à distance dans la session active.

## EXEMPLES

### Exemple 1 : importer toutes les commandes à partir d’une session PSSession

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S
```

Cette commande importe toutes les commandes d'une session PSSession sur l'ordinateur Server01 dans la session active, à l'exception des commandes qui ont le même nom que les commandes dans la session active.

Comme cette commande n'utilise pas le paramètre *CommandName* , elle importe également toutes les données de mise en forme requises pour les commandes importées.

### Exemple 2 : importer des commandes qui se terminent par une chaîne spécifique

```
PS C:\> $S = New-PSSession https://ps.testlabs.com/powershell
PS C:\> Import-PSSession -Session $S -CommandName *-test -FormatTypeName *
PS C:\> New-Test -Name Test1
PS C:\> Get-Test test1 | Run-Test
```

Ces commandes importent les commandes dont les noms se terminent par « -test » à partir d'une session PSSession dans la session locale, puis indiquent comment utiliser une applet de commande importée.

La première commande utilise l’applet de commande New-PSSession pour créer une session PSSession.
Elle enregistre la session PSSession dans la variable $S.

La deuxième commande utilise l’applet de commande **Import-PSSession** pour importer des commandes à partir de la session pssession dans $S dans la session active.
Elle utilise le paramètre *CommandName* pour spécifier des commandes avec le nom Test et le paramètre *FormatTypeName* pour importer les données de mise en forme pour les commandes Test.

Les troisième et quatrième commandes utilisent les commandes importées dans la session active.
Comme les commandes importées sont en réalité ajoutées à la session active, vous utilisez la syntaxe locale pour les exécuter.
Vous n’avez pas besoin d’utiliser l’applet de commande Invoke-Command pour exécuter une commande importée.

### Exemple 3 : importer des applets de commande à partir d’une session PSSession

```
PS C:\> $S1 = New-PSSession -ComputerName s1
PS C:\> $S2 = New-PSSession -ComputerName s2
PS C:\> Import-PSSession -Session s1 -Type cmdlet -Name New-Test, Get-Test -FormatTypeName *
PS C:\> Import-PSSession -Session s2 -Type Cmdlet -Name Set-Test -FormatTypeName *
PS C:\> New-Test Test1 | Set-Test -RunType Full
```

Cet exemple montre que vous pouvez utiliser les applets de commande importées comme vous utiliseriez des applets de commande locales.

Ces commandes importent les applets de commande New-Test et Get-Test à partir d'une session PSSession sur l'ordinateur Server01 et l'applet de commande Set-Test à partir d'une session PSSession sur l'ordinateur Server02.

Même si les applets de commande ont été importées à partir de différentes sessions PSSession, vous pouvez diriger un objet d'une applet de commande vers une autre sans erreur.

### Exemple 4 : exécuter une commande importée en tant que tâche en arrière-plan

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S -CommandName *-test* -FormatTypeName *
PS C:\> $batch = New-Test -Name Batch -AsJob
PS C:\> Receive-Job $batch
```

Cet exemple montre comment exécuter une commande importée en tant que tâche en arrière-plan.

Comme l'exécution des commandes importées peut prendre plus de temps que celle des commandes locales, **Import-PSSession** ajoute un paramètre *AsJob* à chaque commande importée.
Le paramètre *AsJob* vous permet d'exécuter la commande en tant que tâche en arrière-plan.

La première commande crée une session PSSession sur l’ordinateur SERVEUR01 et enregistre l’objet PSSession dans la variable $S.

La deuxième commande utilise **Import-PSSession** pour importer les applets de commande de test de la session pssession dans $S dans la session active.

La troisième commande utilise le paramètre *AsJob* de l'applet de commande New-Test importée pour exécuter une commande New-Test en tant que tâche en arrière-plan.
La commande enregistre l'objet de tâche retourné par New-Test dans la variable $batch.

La quatrième commande utilise l’applet de commande Receive-Job pour obtenir les résultats de la tâche dans la variable $batch.

### Exemple 5 : importer des applets de commande et des fonctions à partir d’un module PowerShell

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Invoke-Command -Session $S {Import-Module TestManagement}
PS C:\> Import-PSSession -Session $S -Module TestManagement
```

Cet exemple montre comment importer les applets de commande et les fonctions à partir d’un module PowerShell sur un ordinateur distant dans la session active.

La première commande crée une session PSSession sur l’ordinateur SERVEUR01 et l’enregistre dans la variable $S.

La deuxième commande utilise l’applet de commande **Invoke-Command** pour exécuter une commande Import-Module dans la session PSSession dans $S.

En règle générale, le module est ajouté à toutes les sessions par une commande **import-module** dans un profil PowerShell, mais les profils ne sont pas exécutés dans sessions PSSession.

La troisième commande utilise le paramètre *module*  d' **Import-PSSession** pour importer les applets de commande et les fonctions du module dans la session active.

### Exemple 6 : créer un module dans un fichier temporaire

```
PS C:\> Import-PSSession $S -CommandName Get-Date, SearchHelp -FormatTypeName * -AllowClobber

Name              : tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1zunz.ttf
Path              : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1zunz.ttf\tmp_79468106-4e1d-4d90-af97-1154f9317239_
tcw1zunz.ttf.psm1
Description       : Implicit remoting for http://server01.corp.fabrikam.com/wsman
Guid              : 79468106-4e1d-4d90-af97-1154f9317239
Version           : 1.0
ModuleBase        : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1zunz.ttf
ModuleType        : Script
PrivateData       : {ImplicitRemoting}
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Get-Date, Get-Date], [SearchHelp, SearchHelp]}
ExportedVariables : {}
NestedModules     : {}
```

Cet exemple montre que **Import-PSSession** crée un module dans un fichier temporaire sur le disque.
Il montre également que toutes les commandes sont converties en fonctions avant leur importation dans la session active.

La commande utilise l’applet de commande **Import-PSSession** pour importer une applet de commande Get-Date et une fonction SearchHelp dans la session active.

L'applet de commande **Import-PSSession** retourne un objet **PSModuleInfo** qui représente le module temporaire.
La valeur de la propriété **Path** montre que **Import-PSSession** a créé un fichier de module de script (.psm1) à un emplacement temporaire.
La propriété **ExportedFunctions** montre que l'applet de commande **Get-Date** et la fonction SearchHelp ont toutes deux été importées en tant que fonctions.

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

La première commande importe une applet de commande Get-Date à partir de la session PSSession dans la variable $S.
Comme la session active inclut une applet de commande **Get-Date** , le paramètre *AllowClobber* est requis dans la commande.

La deuxième commande utilise le paramètre **All** de l’applet de commande Get-Command pour récupérer toutes les commandes d' **extraction** de la session active.
La sortie indique que la session inclut l'applet de commande **Get-Date** d'origine et une fonction **Get-Date** .
La fonction de **récupération** exécute l’applet de commande **« obtient-date »** importée dans la session PSSession dans $S.

La troisième commande exécute une commande **Get-Date** .
Étant donné que les fonctions sont prioritaires sur les applets de commande, PowerShell exécute la fonction d' **extraction de date** , qui retourne une date julienne.

Les quatrième et cinquième commandes montrent comment utiliser un nom qualifié pour exécuter une commande qui est masquée par une commande importée.

La quatrième commande obtient le nom du composant logiciel enfichable PowerShell qui a ajouté l’applet de commande de l’extension de **Date** d’origine à la session active.

La cinquième commande utilise le nom qualifié du composant logiciel enfichable de l'applet de commande **Get-Date** pour exécuter une commande **Get-Date** .

Pour plus d'informations sur la priorité des commandes et les commandes masquées, consultez about_Command_Precedence.

### Exemple 8 : importer des commandes qui ont une chaîne spécifique dans leurs noms

```
PS C:\> Import-PSSession -Session $S -CommandName *Item* -AllowClobber
```

Cette commande importe les commandes dont les noms incluent l’élément de la session PSSession dans $S.
Étant donné que la commande comprend le paramètre *CommandName* mais pas le paramètre *FormatTypeData* , seule la commande est importée.

Utilisez cette commande quand vous utilisez **Import-PSSession** pour exécuter une commande sur un ordinateur distant et que vous avez déjà les données de mise en forme pour la commande dans la session active.

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

Cette commande montre comment utiliser le paramètre *module* de la **commande « obtenir-Command »** pour déterminer les commandes qui ont été importées dans la session par une commande **Import-PSSession** .

La première commande utilise l’applet de commande **Import-PSSession** pour importer des commandes dont les noms incluent « bits » de la session PSSession dans la variable $S.
La commande **Import-PSSession** retourne un module temporaire et la commande enregistre le module dans la variable $m.

La deuxième commande utilise l’applet de commande Get-Command pour récupérer les commandes exportées par le module dans la variable $M.

Le paramètre *Module* prend une valeur de chaîne, qui est conçue pour le nom du module.
Toutefois, lorsque vous envoyez un objet de module, PowerShell utilise la méthode **ToString** sur l’objet de module, qui retourne le nom du module.

La commande d' **extraction de commande** est l’équivalent de `Get-Command $M.Name` «.

## PARAMETERS

### -AllowClobber

Indique que cette applet de commande importe les commandes spécifiées, même si elles ont les mêmes noms que les commandes dans la session active.

Si vous importez une commande portant le même nom qu'une commande dans la session active, la commande importée masque ou remplace les commandes d'origine.
Pour plus d'informations, consultez about_Command_Precedence.

Par défaut, **Import-PSSession** n'importe pas les commandes qui ont le même nom que les commandes dans la session active.

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

Par exemple, pour importer la variante de la commande Get-Item dans le certificat (CERT :) dans la session PSSession dans $S, tapez `Import-PSSession -Session $S -Command Get-Item -ArgumentList cert:` .

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

Spécifie le certificat client qui est utilisé pour signer les fichiers de format (*.Format.ps1xml) ou fichiers de module de script (.psm1) dans le module temporaire créé par **Import-PSSession** .

Entrez une variable qui contient un certificat, ou bien une commande ou une expression qui obtient le certificat.

Pour rechercher un certificat, utilisez l’applet de commande Get-PfxCertificate ou utilisez l’applet de commande Get-ChildItem dans le certificat (CERT :) unités.
Si le certificat n'est pas valide ou n'a pas une autorité suffisante, la commande échoue.

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

Spécifie les commandes avec les noms ou modèles de noms spécifiés.
Les caractères génériques sont autorisés.
Utilisez *CommandName* ou son alias, *Name* .

Par défaut, **Import-PSSession** importe toutes les commandes de la session, à l'exception de celles qui ont le même nom que les commandes dans la session active.
Cela empêche les commandes importées de masquer ou de remplacer des commandes dans la session.
Pour importer toutes les commandes, y compris celles qui masquent ou remplacent d'autres commandes, utilisez le paramètre *AllowClobber* .

Si vous utilisez le paramètre *CommandName* , les fichiers de mise en forme pour les commandes ne sont pas importés, sauf si vous utilisez le paramètre *FormatTypeName* .
De même, si vous utilisez le paramètre *FormatTypeName* , aucune commande n'est importée, sauf si vous utilisez le paramètre *CommandName* .

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

Spécifie le type d’objets de commande.
La valeur par défaut est Cmdlet.
Utilisez *CommandType* ou son alias, *Type* .
Les valeurs valides pour ce paramètre sont :

- Affecté.
Alias PowerShell dans la session à distance.
- Tout le monde.
Applets de commande et fonctions dans la session à distance.
- console.
Tous les fichiers autres que les fichiers PowerShell dans les chemins d’accès qui sont répertoriés dans la variable d’environnement PATH ($env :p Hemin) dans la session à distance, y compris les fichiers. txt,. exe et. dll.
- PolicySchedule.
Applets de commande dans la session à distance.
« Cmdlet » est la valeur par défaut.
- ExternalScript.
Fichiers .ps1 dans les chemins d'accès répertoriés dans la variable d'environnement Path ($env:path) dans la session à distance.
- Filtre et fonction.
Fonctions PowerShell dans la session à distance.
- Script.
Blocs de scripts dans la session à distance.

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

Par défaut, lorsqu’un module que vous importez exporte des applets de commande ou des fonctions qui ont des verbes non approuvés dans leurs noms, PowerShell affiche le message d’avertissement suivant :

"AVERTISSEMENT : certains noms de commandes importés incluent des verbes non approuvés qui peuvent les rendre moins détectables.
Utilisez le paramètre Verbose pour plus d'informations ou tapez Get-Verb pour obtenir la liste des verbes approuvés. »

Ce message n'est qu'un avertissement.
Le module entier est toujours importé, y compris les commandes non conformes.
Bien que le message soit affiché aux utilisateurs du module, le problème d'affectation de noms doit être corrigé par l'auteur du module.

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

La valeur de ce paramètre doit être le nom d'un type qui est retourné par une commande Get-FormatData dans la session à partir de laquelle les commandes sont importées.
Pour obtenir toutes les données de mise en forme dans la session à distance, tapez *.

Si la commande n’inclut pas le paramètre *CommandName* ou *FormatTypeName* , **Import-PSSession** importe les instructions de mise en forme pour tous les types de .NET Framework retournés par une commande **FormatData** dans la session à distance.

Si vous utilisez le paramètre *FormatTypeName* , aucune commande n'est importée, sauf si vous utilisez le paramètre *CommandName* .

De même, si vous utilisez le paramètre *CommandName* , les fichiers de mise en forme pour les commandes ne sont pas importés, sauf si vous utilisez le paramètre *FormatTypeName* .

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

Spécifie les modules dont les noms sont spécifiés sous la forme d’objets **ModuleSpecification** (décrits dans la section Notes du [constructeur ModuleSpecification (HASHTABLE)](https://msdn.microsoft.com/library/jj136290) dans MSDN Library).
Par exemple, le paramètre *FullyQualifiedModule* accepte un nom de module qui est spécifié au format @ {ModuleName = "ModuleName"; ModuleVersion = "version_number"} ou @ {ModuleName = "ModuleName"; ModuleVersion = "version_number"; Guid = "GUID"}.
**ModuleName** et **ModuleVersion** sont obligatoires, mais **Guid** est facultatif.

Vous ne pouvez pas spécifier le paramètre *FullyQualifiedModule* dans la même commande qu’un paramètre *module* ; les deux paramètres s’excluent mutuellement.

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

Spécifie et tableau de commandes dans les modules et composants logiciels enfichables PowerShell.
Entrez les noms de composant logiciel enfichable et de module.
Les caractères génériques ne sont pas autorisés.

**Import-PSSession** ne peut pas importer des fournisseurs à partir d’un composant logiciel enfichable.

Pour plus d'informations, consultez about_PSSnapins et [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).

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

Par exemple, si vous spécifiez le préfixe Remote, puis importez une applet de commande Get-Date, l’applet de commande est connue dans la session en tant que RemoteDate et n’est pas confondue avec l’applet de commande d’origine de l’opération d' **extraction** .

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

Spécifie la **session PSSession** à partir de laquelle les applets de commande sont importées.
Entrez une variable qui contient un objet de session ou une commande qui obtient un objet de session, tel qu’une commande New-PSSession ou Get-PSSession.
Vous ne pouvez spécifier qu'une seule session.
Ce paramètre est obligatoire.

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

**Import-PSSession** retourne le même objet de module que New-Module et les applets de commande Get-Module retournent.
Toutefois, le module importé est temporaire et existe uniquement dans la session active.
Pour créer un module permanent sur le disque, utilisez l’applet de commande Export-PSSession.

## REMARQUES

* **Import-PSSession** s’appuie sur l’infrastructure de communication à distance PowerShell. Pour utiliser cette applet de commande, l'ordinateur doit être configuré pour la communication à distance WS-Management. Pour plus d’informations, consultez about_Remote et about_Remote_Requirements.
* **Import-PSSession** n’importe pas les variables ou les fournisseurs PowerShell.
* Quand vous importez des commandes qui ont le même nom que les commandes dans la session active, les commandes importées peuvent masquer des alias, des fonctions et des applets de commande dans la session, et peuvent remplacer des fonctions et variables dans la session. Pour éviter les conflits de noms, utilisez le paramètre *Prefix* . Pour plus d'informations, consultez about_Command_Precedence.
* **Import-PSSession** convertit toutes les commandes en fonctions avant de les importer. Par conséquent, les commandes importées se comportent un peu différemment que si elles avaient conservé leur type de commande d'origine. Par exemple, si vous importez une applet de commande à partir d'une session PSSession, puis une applet de commande avec le même nom à partir d'un module ou d'un composant logiciel enfichable, l'applet de commande qui est importée à partir de la session PSSession s'exécute toujours par défaut, car les fonctions sont prioritaires sur les applets de commande. À l'inverse, si vous importez un alias dans une session qui a un alias avec le même nom, l'alias d'origine est toujours utilisé, car les alias sont prioritaires sur les fonctions. Pour plus d'informations, consultez about_Command_Precedence.
* **Import-PSSession** utilise l’applet de commande Write-Progress pour afficher la progression de la commande. Vous pouvez voir la barre de progression pendant l'exécution de la commande.
* Pour rechercher les commandes à importer, **Import-PSSession** utilise l’applet de commande Invoke-Command pour exécuter une commande Get-Command dans la session PSSession. Pour obtenir des données de mise en forme pour les commandes, elle utilise l’applet de commande Get-FormatData. Vous pouvez voir des messages d’erreur de ces applets de commande lorsque vous exécutez une commande **Import-PSSession** . En outre, **Import-PSSession** ne peut pas importer de commandes à partir d’une session PSSession qui n’inclut pas les applets de commande obtenir-Command, obtenir-FormatData, Select-Object et Get-Help.
* Les commandes importées présentent les mêmes restrictions que d'autres commandes à distance, notamment l'impossibilité de démarrer un programme avec une interface utilisateur, tel que le Bloc-notes.
* Étant donné que les profils PowerShell ne sont pas exécutés dans sessions PSSession, les commandes qu’un profil ajoute à une session ne sont pas disponibles pour **Import-PSSession** . Pour importer des commandes à partir d'un profil, utilisez une commande Invoke-Command pour exécuter le profil dans la session PSSession manuellement avant d'importer des commandes.
* Le module temporaire créé par **Import-PSSession** peut inclure un fichier de mise en forme, même si la commande n'importe pas les données de mise en forme. Si la commande n'importe pas de données de mise en forme, les fichiers de mise en forme éventuellement créés ne contiennent pas de données de mise en forme.
* Pour utiliser **Import-PSSession** , la stratégie d'exécution dans la session active ne peut pas être Restricted ni AllSigned, car le module temporaire créé par **Import-PSSession** contient des fichiers de script non signés qui sont interdits par ces stratégies. Pour utiliser **Import-PSSession** sans modifier la stratégie d’exécution de l’ordinateur local, utilisez le paramètre *scope* de Set-ExecutionPolicy pour définir une stratégie d’exécution moins restrictive pour un seul processus.
* Dans Windows PowerShell 2.0, les rubriques d'aide pour les commandes qui sont importées à partir d'une autre session n'incluent pas le préfixe que vous attribuez à l'aide du paramètre *Prefix* . Pour obtenir de l'aide pour une commande importée dans Windows PowerShell 2.0, utilisez le nom de commande (sans préfixe) d'origine.

## LIENS CONNEXES

[Export-PSSession](Export-PSSession.md)
